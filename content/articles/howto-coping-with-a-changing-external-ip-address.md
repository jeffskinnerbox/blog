Title: HowTo: Coping With a Changing External IP Address
Date: 2021-10-02 15:18
Category: Software
Tags: How To, DDNS
Slug: howto-coping-with-a-changing-external-ip-address
Author: Jeff Irland
Image: how-to.jpg
Summary: Since I'm not using a static IP for my home router, my ISP can change (and they do) my IP address as they sees fit. But in order for me to SSH into my home server from outside my local network, I need my home’s router current IP address. Here I show two methods to cope with your ISP's IP adress changes.

<a href="http://whatismyipaddress.com/">
    <img class="img-rounded" style="margin: 0px 8px; float: left" title="Since I'm not using a static IP for my home router, my ISP can change my IP address as they sees fit. But in order for me to SSH into my home server from outside my local network, I need my home’s router current IP address." alt="internet connection picture" src="{filename}/images/internet-connection.png" width="128" height="128" />
</a>

# Dynamic DNS (DDNS)
Some ISPs frequently change the IP address they provide you,
while others provide it on a long lease but may still change it.
Most ISPs allocate their range of IP addresses dynamically (using DHCP),
and the “lease” is often until you reboot the router or set to 24 hours,
which is why your address might change frequently.
For most users, changing IP doesn’t matter,
but in my case, I need a known address so I can login remotely.
To do this easily, you could have your ISP give you a fixed address
(aka a static IP address),
but if they offer this service at all, they will charge you for it.

Given my infrequent need,
I particularly don't want to pay for the static IP address, so I need an alternative.
One alternative is to make use of a [Dynamic DNS (DDNS)][01] address service.
These services associate your actual address (in its numerical form)
with a fixed mnemonic address in real time,
so as long as you have  mnemonic form, it will point you to your server.
This service can also cost you money.
(e.g. [Dyn][02] has stopped their free plans
and [No-IP][03] provides a quasi-free service).
In some implementations,
your home router will also need to support the DDNS client.
Not all routers support DDNS,
but [OpenWrt does][04] and is [fairly easy to install][05].
I'm choosing to do all that is required from my desktop Linux box.
There are ways to support a DDNS via your router or firewall,
assuming your devices are capable.

# Why Dynamic DNS
[What’s Dynamic DNS And Why Would I Want It?][15].
Dynamic DNS (DDNS) is very useful if you need to access home network services from across the Internet.
It will allow you to reach you home network despite the fact your ISP might be
changing your router's IP address.
DDNS will be provide you a domain name that is fix even while the IP address has changed.

## Method #1: Push to Cell Phone
Here a create a simple utility that pushes to my cell phone
the new address when my router's IP address changes.
This cheapskate alternative is to create a service on your server
that email or other wish notifies you, when the IP address changes.
This is practical if the IP address isn't changing too frequently,
which happens to be my case.
My choose is to use a  simple service for periodically looking up my IP address,
specifically using the website [ifconfig.co][06].
The design is to execute the command `curl ifconfig.co` periodically,
check if the IP address has changes, and if so, email or text the change to myself.

### Step 1: Create Cron Entry
To do this, I placed the shell program listed below, which I call `ip_check`,
in `cron` to run every hour.

```bash
#!/bin/bash

# This utility is used to periodically check to see if the external IP address
# has changed, and if so, send a notification giving the new IP address.
#
# Reasons why crontab does not work - http://askubuntu.com/questions/23009/reasons-why-crontab-does-not-work

FLAG=0                          # set to 1 for verbose output
MYPATH="/home/jeff/bin"         # path to apprise, need for running in cron

# Parse command line options
USAGE="Usage: `basename $0` [-h] [-x]"
while getopts hx OPT; do
    case "$OPT" in
        h)
            echo $USAGE
            exit 0
            ;;
        x)
            FLAG=1
            ;;
        \?)
            # getopts issues an error message
            echo $USAGE >&2
            exit 1
            ;;
    esac
done

# get current and old IP address
IP_ADDRESS_STORE=$HOME/.external_ip_address
CURRENT_IP=$(cat $IP_ADDRESS_STORE)
NEW_IP=$(curl --silent ifconfig.co)

# send message about any changes
if [ $CURRENT_IP == $NEW_IP ];
    then
        if [ $FLAG -eq 1 ];
            then
                $MYPATH/apprise -t "External IP Address" -m "No change in home router external IP address ($CURRENT_IP)."
        fi
        exit 2
    else
        echo $NEW_IP > $IP_ADDRESS_STORE
        $MYPATH/apprise -t "External IP Address" -m "Your home router external IP address has changed from $CURRENT_IP to $NEW_IP."
        exit 3
fi
```

To run the script in [`cron`][09] every hour,
I [edited the cron table][08] via the command `crontab -e`
and place the following in the table: `@hourly  /home/jeff/bin/ip_check -x`.
Also note that `cron` can be temperamental,
so check out the post "[Reasons why crontab does not work][10]"
if you have problems getting it working.

### Step 2: Push Ne IP Address to Mobile Phone
The above shell program makes use of the utility `apprise`,
a push notification tool for the [Pushover][07] service.
This will notify me on my cell phone of any changes to the external IP address.

```bash
#!/bin/bash

# This utility does a push notification to the service Pushover - https://pushover.net/

APPTOKEN="aegfmQiK9Krrigwmir4fgnoodw8w"
USERKEY="ufwidfifFYQHyggjdpdgeGfehdfpg"

# Parse command line options
USAGE="Usage: `basename $0` [-h] -t title -m message"
while getopts ht:m: OPT; do
    case "$OPT" in
        h)
            echo $USAGE
            exit 0
            ;;
        t)
            TITLE=$OPTARG
            ;;
        m)
            MESSAGE=$OPTARG
            ;;
        \?)
            # getopts issues an error message
            echo $USAGE >&2
            exit 1
            ;;
    esac
done

# Send message to Pushover to create notification
curl --silent \
    -F "token=$APPTOKEN" \
    -F "user=$USERKEY" \
    -F "message=$MESSAGE" \
    -F "device=desktop" \
    -F "title=$TITLE" \
    -F "sound=spacealarm" \
    https://api.pushover.net/1/messages.json | grep '"status":1' > /dev/null

# Check the exit code to identify an error
if [ $? -eq 0 ];
    then
        exit 0
    else
        echo "apprise failed"
        exit 1
fi
```

## Method #2: Subscribe to DDNS Service
There is a better way to do all this.
Setting up [Duck DNS][11] allows you to access your home computer from outside of your home.
Its a free services and widely used.
I'll be using the "linux cron" methodology but you will find many more.

### Step 1: Duck DNS Registration
Go to [Duck DNS][11] and sign-in, choose a sub-domain to use, get a token,
and you are done with registration.

I signed in with my GitHub account as my authenticator,
hit the "reCAPTCHA" button,
and up popped the screen where I entered a domain and Duck DNS provided me a token.
You'll need the domain & token later.

### Step 2: Duck DNS Installation
I'm using the ["linux cron" installation methodology][12].
The Duck DNS website provide detail instructions which go basically like this:

```bash
# create a directory where duck dns tools will be located
mkdir ~/src/duckdns
cd ~/src/duckdns

# using an editor, create the file duck.sh with this content
# NOTE: make sure to use your token and domain from step 1 above
echo url="https://www.duckdns.org/update?domains=exampledomain&token=a7c4d0ad-114e-40ef-ba1d-d217904a50f2&ip=" | curl --silent -k -o ~/src/duckdns/duck.log -K -

# save the file and make it executable
chmod 700 duck.sh

# make the script run every 5 minutes via editing the cron table
crontab -e

# enter this into the cron table
*/5 * * * * ~/src/duckdns/duck.sh >/dev/null 2>&1

# test the script you created
# this should simply return to a prompt
./duck.sh

# check if the last attempt was successful (good = OK or bad = KO)
cat ~/src/duckdns/duck.log
```

### Step 3: Test the Service
To see your [DNS TXT record][13] for your sub-domain,
you can [use the following command][14]:

```bash
# dns txt record
dig jeffskinnerbox.duckdns.org TXT
```

To test if you are in fact able to reach your home desktop Linux box via `jeffskinnerbox.duckdns.org`,
go into your router, and forward the routers port 22 to the IP address of your desktop.
Now execute the following command and see if you get a terminal prompt:

```
# with the home router properly port forwarded, you should be able to login with this
ssh <your-domain>.duckdns.org
```

This is proof positive your up and working fine.

----

>**NOTE:** I originally posted this on February 2nd, 2016 discussing only method #1.
>Since that time, Duck DDS and others have been providing free Dynamic DNS services.



[01]:https://stevessmarthomeguide.com/dynamic-dns/
[02]:http://dyn.com/dns/
[03]:http://www.noip.com/
[04]:https://wiki.openwrt.org/doc/howto/ddns.client
[05]:http://www.pebra.net/blog/2014/02/07/installing-openwrt-on-wd-mynet-n600/
[06]:http://ifconfig.co/
[07]:https://pushover.net/
[08]:http://man7.org/linux/man-pages/man5/crontab.5.html
[09]:https://en.wikipedia.org/wiki/Cron
[10]:http://askubuntu.com/questions/23009/reasons-why-crontab-does-not-work
[11]:https://www.duckdns.org/
[12]:https://www.duckdns.org/install.jsp
[13]:https://www.cloudflare.com/learning/dns/dns-records/dns-txt-record/
[14]:https://www.duckdns.org/spec.jsp
[15]:https://www.howtogeek.com/66438/how-to-easily-access-your-home-network-from-anywhere-with-ddns/
