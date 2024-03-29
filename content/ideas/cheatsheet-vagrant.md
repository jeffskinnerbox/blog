<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----


# Vagrant Cheat Sheet
Typing just `vagrant` or `vagrant help` on the command line will display a list of all available commands.

Be sure that you are in the same directory as the Vagrantfile when running these commands!

## Creating a VM
- `vagrant init`           -- Initialize Vagrant with a Vagrantfile and ./.vagrant directory, using no specified base image. Before you can do vagrant up, you'll need to specify a base image in the Vagrantfile.
- `vagrant init <boxpath>` -- Initialize Vagrant with a specific box. To find a box, go to the [public Vagrant box catalog](https://app.vagrantup.com/boxes/search). When you find one you like, just replace it's name with boxpath. For example, `vagrant init ubuntu/trusty64`.

## Starting a VM
- `vagrant up`                  -- starts vagrant environment (also provisions only on the FIRST vagrant up)
- `vagrant resume`              -- resume a suspended machine (vagrant up works just fine for this as well)
- `vagrant provision`           -- forces re-provisioning of the vagrant machine
- `vagrant reload`              -- restarts vagrant machine, loads new Vagrantfile configuration (equal to a 'halt' followed by an 'up')
- `vagrant reload --provision`  -- restart the virtual machine and force provisioning

## Getting into a VM
- `vagrant ssh`           -- connects to machine via SSH
- `vagrant ssh <boxname>` -- If you give your box a name in your Vagrantfile, you can ssh into it with boxname. Works from any directory.

## Stopping a VM
- `vagrant halt`        -- stops the vagrant machine
- `vagrant suspend`     -- suspends a virtual machine (remembers state)

## Cleaning Up a VM
- `vagrant destroy`        -- stops and deletes all traces of the vagrant machine
- `vagrant destroy <ID>`   -- delete vagrant machine of the referenced ID (e.g. `vagrant destroy e4981e5ec1db498b9fac379c7aea095b`)
- `vagrant destroy -f`     -- same as above, without confirmation

## Boxes
- `vagrant box list`              -- see a list of all installed boxes on your computer
- `vagrant box add <name> <url>`  -- download a box image to your computer
- `vagrant box outdated`          -- check for updates vagrant box update
- `vagrant box remove <name>`     -- deletes a box from the machine (e.g. `vagrant box remove ubuntu/bionic64` or `vagrant box remove ubuntu/disco64 --box-version=20191204.0.0`)
- `vagrant package`               -- packages a running virtualbox env in a reusable box
- `vagrant box update`            -- updates the box for the current Vagrant environment if there are updates available

## Saving Progress
- `vagrant snapshot save [options] [vm-name] <name>` -- vm-name is often `default`. Allows us to save so that we can rollback at a later time

## Tips
- `vagrant -v`                    -- get the vagrant version
- `vagrant status`                -- outputs status of the vagrant machine
- `vagrant global-status`         -- outputs status of all vagrant machines
- `vagrant global-status --prune` -- same as above, but prunes invalid entries
- `vagrant provision --debug`     -- use the debug flag to increase the verbosity of the output
- `vagrant push`                  -- yes, vagrant can be configured to [deploy code](http://docs.vagrantup.com/v2/push/index.html)!
- `vagrant up --provision | tee provision.log`  -- Runs `vagrant up`, forces provisioning and logs all output to a file

## Plugins
- `vagrant plugin list`           -- list the plugins currently installed in Vagrant
- [vagrant-hostsupdater](https://github.com/cogitatio/vagrant-hostsupdater) -- Use `vagrant plugin install vagrant-hostsupdater` to update your `/etc/hosts` file automatically each time you start/stop your vagrant box.

## Notes
- If you are using [VVV](https://github.com/varying-vagrant-vagrants/vvv/), you can enable xdebug by running `vagrant ssh` and then `xdebug_on` from the virtual machine's CLI.
