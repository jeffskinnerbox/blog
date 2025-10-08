<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg"
    title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------

[HTTP Server Examples: Using wifi with adafruit_httpserver](https://learn.adafruit.com/networking-in-circuitpython/http-server-examples)
[Adafruit ESP32-S3 Feather: CircuitPython Libraries](https://learn.adafruit.com/adafruit-esp32-s3-feather/circuitpython-libraries#copying-libraries-to-your-board-2978253)
[Adafruit CircuitPython Library Bundle](https://docs.circuitpython.org/projects/bundle/en/stable/)

[Train and Deploy Your Own AI Model](https://wiki.seeedstudio.com/train_and_deploy_model/)
[Using XIAO ESP32S3 Sense as an AI Sensor with SenseCraft AI](https://wiki.seeedstudio.com/sensecraft-ai/tutorials/sensecraft-ai-output-libraries-xiao/)

# Seeed Studio XIAO ESP32 S3 Sense Video Streaming Service

## Video streaming:-

what is it ?

Video streaming is a continuous transmission of video files from a server to a client. Video streaming enables users to view videos online without having to download them. Streamed video content can include movies, TV shows, YouTube videos and livestreamed content.

What is streaming ?

The term streaming refers to the continual transmission of audio and video files from a server to a client. In video streams, content is sent in a compressed form over the internet and is displayed by the viewer in real time. The media is sent in a continuous stream of data and is played as it arrives. The user needs a player, which is a special program that uncompresses and sends video data to the display and audio data to speakers. Examples of media players include Windows Media Player 12 for Windows 10 or QuickTime Player for MacOS.

How does streaming works ?

Video streams normally begin with a prerecorded media file hosted on a remote server. Once the server receives a client request, the data in the video file is compressed and sent to the requesting device in pieces. Audio and video files are broken into data packets, where each packet contains a small piece of data. A transmission protocol, much of the time either Transmission Control Protocol (TCP) or User Datagram Protocol (UDP), is used to exchange data over a network. Once the requesting client receives the data packets, a video player on the user end will decompress the data and interpret video and audio. The video files are automatically deleted once played.



## Initial Design Goal
* Camera - Seeed Studio XIAO ESP32 S3 Sense
* PC / Mobile Phone - Web Browser for viewing live stream video from the camera

## 1st Goal
Prompt for Gemini or Claude:
I wish to create a live video stream from a camera that I can view in a web browser on a PC or mobile phone.
The camera will be the Seeed Studio XIAO ESP32S3 Sense and all development on the camera will be done in Adafruit's CircuitPython.
The camera will host a WiFi website where the streaming video can be observed.
The camera website will be hosted on my home network SSID "MYWIFI" with access password "MYPASSWORD" at static IP address 192.168.1.130
The camera should immediately provide the streaming service when its powered on, no setup required.

This prompt produced the following:

```python
import os
import ssl
import time
import board
import busio
import digitalio
import wifi
import socketpool
import adafruit_httpserver as server
from adafruit_httpserver.response import HTTPResponse

# --- Camera and Wi-Fi Setup ---
try:
    # Get Wi-Fi credentials from settings.toml
    # The file should look like:
    # WIFI_SSID="MYWIFI"
    # WIFI_PASSWORD="MYPASSWORD"
    ssid = os.getenv("WIFI_SSID")
    password = os.getenv("WIFI_PASSWORD")
except Exception as e:
    print(f"Error getting credentials from settings.toml: {e}")
    print("Please create a settings.toml file with your WiFi credentials.")
    # Fallback for demonstration if settings.toml is missing
    ssid = "MYWIFI"
    password = "MYPASSWORD"

# Initialize the camera using the built-in I2C bus
# The XIAO ESP32S3 Sense uses an internal connection for the camera
cam_bus = busio.I2C(board.SCL, board.SDA)

# Attempt to import and initialize the camera
# This will raise an ImportError if the camera isn't found
try:
    import adafruit_ov5640
    cam = adafruit_ov5640.OV5640(
        cam_bus,
        data_pins=board.CAMERA_DATA,
        clock=board.CAMERA_PCLK,
        vsync=board.CAMERA_VSYNC,
        href=board.CAMERA_HREF,
        mclk=board.CAMERA_XCLK,
        shutdown=None,
        reset=None,
    )
    cam.size = adafruit_ov5640.OV5640_SIZE_QVGA # 320x240 resolution
    cam.colorspace = adafruit_ov5640.OV5640_COLOR_JPEG
    cam.flip_y = True
    print("Camera initialized successfully.")
except ImportError:
    print("Error: Camera library not found. Make sure adafruit_ov5640 is in the lib folder.")
    while True: pass
except RuntimeError as e:
    print(f"Error initializing camera: {e}")
    print("Camera not detected. Check connections.")
    while True: pass


# --- Network Connection ---
# Set the static IP address
STATIC_IP = "192.168.1.130"
NETMASK = "255.255.255.0"
GATEWAY = "192.168.1.1" # Change if your gateway is different
DNS = "8.8.8.8"      # Google's DNS, change if needed

try:
    # Set the static IP configuration
    wifi.radio.set_ipv4_address(
        ipv4=socketpool.SocketPool.getaddrinfo(STATIC_IP, 80)[0][4][0],
        netmask=socketpool.SocketPool.getaddrinfo(NETMASK, 80)[0][4][0],
        gateway=socketpool.SocketPool.getaddrinfo(GATEWAY, 80)[0][4][0],
        ipv4_dns=socketpool.SocketPool.getaddrinfo(DNS, 80)[0][4][0]
    )
    print(f"Connecting to Wi-Fi SSID: {ssid}")
    wifi.radio.connect(ssid, password)
    print(f"Connected! My IP is: {wifi.radio.ipv4_address}")

except Exception as e:
    print(f"Failed to connect to Wi-Fi: {e}")
    while True: pass

# Create a socket pool and web server
pool = socketpool.SocketPool(wifi.radio)
http_server = server.Server(pool, "/static", debug=True)

# --- Web Server Routes ---

# Route for the main HTML page
@http_server.route("/")
def base(request):
    """Serves the main HTML page with the streaming image tag."""
    html = """
    <!DOCTYPE html>
    <html>
    <head>
        <title>XIAO ESP32S3 Sense Stream</title>
        <style>
            body { font-family: Arial, sans-serif; background-color: #333; margin: 0; padding: 0; display: flex; justify-content: center; align-items: center; height: 100vh; }
            img { border: 2px solid #555; max-width: 90%; max-height: 90vh; }
        </style>
    </head>
    <body>
        <img src="/stream" width="640" height="480" />
    </body>
    </html>
    """
    return HTTPResponse(body=html, content_type="text/html")

# Route for the MJPEG video stream
@http_server.route("/stream")
def stream(request):
    """Provides the MJPEG video stream from the camera."""

    # Create a streaming response
    response = HTTPResponse(request, content_type="multipart/x-mixed-replace; boundary=frame")

    # Send the response headers
    response.send_headers()

    # Loop to continuously send frames
    while True:
        try:
            # Capture a frame from the camera
            frame = cam.capture()
            if frame is None:
                print("Failed to capture frame")
                time.sleep(0.1)
                continue

            # MJPEG frame format
            frame_data = (
                b'--frame\r\n'
                b'Content-Type: image/jpeg\r\n'
                b'Content-Length: ' + str(len(frame)).encode() + b'\r\n\r\n'
                + frame + b'\r\n'
            )

            # Send the frame
            response.send(frame_data)

        except ConnectionError as e:
            # This happens when the client (browser) disconnects
            print(f"Client disconnected: {e}")
            break
        except Exception as e:
            print(f"An error occurred during streaming: {e}")
            break

# --- Start the Server ---
print(f"Starting server at http://{wifi.radio.ipv4_address}")
try:
    http_server.serve_forever()
except KeyboardInterrupt:
    print("Server stopped by user.")
except Exception as e:
    print(f"Server crashed: {e}")
```

#### Step 1: Install the CircuitPython Interpreter onto ESP32 Board
The first process step you'll need to do is installing firmware on the ESP32 board.
This firmware, that is, the CircuitPython interpreter, allowing it to run the CircuitPython code your writing.
You only need to do this step once.

The CircuitPython firmware is found at [Adafruit's CircuitPython website][01],
specifically the [Seeed Studio XIAO ESP32S3 Sense page][02].
For many (if not most) boards, the firmware is a file with a `.uf2` file extension.
**THIS IS NOT THE CASE FOR ESP BOARDS.**
We need to use the file with a `.BIN` file extension.

Do the following:

1. Hit the **DOWNLOAD .BIN NOW** button on the [Seeed Studio XIAO ESP32S3 Sense page][02]
1. Next click the **OPEN INSTALLER** button
1. On the pop-up screen, select the **Install CircuitPython 10.0.0 Bin Only** item (NOTE: your version number may differ)
1. On the next screen, hit the **Next** button
1. Follow the instructions on the next screen.
   Make sure to to hold down the **BOOT** button, them pluging the cable, then release the BOOT button.
1. When complete (about 15 seconds after loading),
   you should see the `CIRCUITPY` filesystem within your filesystem explorer,
   and in there will be the file `code.py` that CircuitPython will be executing.

#### Step 2: Install the `copy.py` Application

#### Step X: Manually Copy Required Libraries
For the Seeed Studio XIAO ESP32S3, and for many other boards,
the firmware included with your board only contains the most essential modules to save storage space.
The `adafruit_httpserver` package is not part of the standard CircuitPython firmware
for the Seeed Studio XIAO ESP32S3 Sense and must be installed separately.

To add this functionality to your board,
you will need to manually copy the library onto its file system.
Follow these steps:

1. Navigate to the [CircuitPython Libraries webpage][03]:
* Find the appropriate library bundle for your version of CircuitPython
  (`adafruit-circuitpython-seeed_xiao_esp32_s3_sense-en_US-10.0.0.bin`, version 10.0.0 in my case).
* Download the ZIP file that corresponds to the bundle (`adafruit-circuitpython-bundle-10.x-mpy-20250930.zip` in my case).
1. Copy the library to your board and Unzip (via `unzip <zipped-file.zip`) the downloaded bundle file.
* Connect your Seeed Studio XIAO ESP32S3 Sense to your computer.
* It should appear as a new disk drive named CIRCUITPY.
* Copy the `adafruit_httpserver` folder from the unzipped bundle's lib directory to the `lib` folder on your `CIRCUITPY` drive.
3. Start coding
* Once the library files are copied, you can use import `adafruit_httpserver` in your `code.py` file to start using the web server functionality.




## Camera Sensor


* [Demystifying digital camera sensors once and for all](https://www.techhive.com/article/2052159/demystifying-digital-camera-sensors-once-and-for-all.html)

## Color

<https://en.wikipedia.org/wiki/Color_space>
gamma, brightness, contrast, hue, sturation

* [Understanding Color Models Used in Digital Image Processing](https://www.allaboutcircuits.com/technical-articles/understanding-color-models-used-in-digital-image-processing/)
* [Color Spaces: The Model at the End of the Rainbow](https://hackaday.com/2018/03/30/color-spaces-the-model-at-the-end-of-the-rainbow/)
* [RGB LEDs: How to Master Gamma and Hue for Perfect Brightness](https://hackaday.com/2016/08/23/rgb-leds-how-to-master-gamma-and-hue-for-perfect-brightness/)
* [List of color spaces and their uses](https://en.wikipedia.org/wiki/List_of_color_spaces_and_their_uses)
color space - <https://en.wikipedia.org/wiki/Color_space>
* [A Beginner’s Guide to Understanding White Balance](https://www.makeuseof.com/tag/white-balance-guide/)

* [23 open source audio-visual production tools](https://opensource.com/article/18/2/open-source-audio-visual-production-tools)
* [color theory](https://en.wikipedia.org/wiki/Color_theory)
* [The fundamentals of understanding color theory](https://99designs.com/blog/tips/the-7-step-guide-to-understanding-color-theory/)

* [YUV Color Encoding](https://en.wikipedia.org/wiki/YUV)


[01]:https://circuitpython.org/
[02]:https://circuitpython.org/board/seeed_xiao_esp32s3_sense/
[03]:https://circuitpython.org/libraries
