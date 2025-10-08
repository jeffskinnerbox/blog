<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg"
        title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------


# CircuitPython Development Workflow with NeoVim/LazyVim
Using LazyVim for CircuitPython development gives you a modern, feature-rich editing experience,
but we must make NeoVim's language server aware of the specific CircuitPython libraries since they are not in the standard Python environment.
We must also assure that NeoVim/LazyVim honors CircuitPython's REPL strategy,
all the while keeping control of what coding is going to our development environment vs what is within the microcontroller.
A nice feature of the REPL is that CircuitPython detects when the files are changed/written on the board
and will automatically re-start your code.
This makes coding very fast because you save, and it re-runs.

>**NOTE:** The [Python REPL][07] (Read-Eval-Print Loop) is an interactive environment in the Python interpreter
>that allows you to type Python commands, see their immediate results, and experiment with code snippets.
>To access it, open your terminal or command prompt and type `python` or `python3`,
>then you will see a `>>>` prompt where you can enter and execute code.
>
>The REPL operates in a continuous cycle:
> * **Read:** It reads the Python command you input.
> * **>Eval (Evaluate):** It evaluates the command to determine its meaning and execute it.
> * **>Print:** It prints the result of the command to the screen.
> * **>Loop:** It then loops back to the beginning, waiting for your next command.

I'll cover here the following topics:

* Installing CircuitPython on your target microprocessor/microcontroller

Sources:
* [Using the Python REPL][07]
* [CircuitPython on ESP32 Quick Start](https://learn.adafruit.com/circuitpython-with-esp32-quick-start)

## Installing CircuitPython on Target Microprocessor (non-ESP32)
The very first step is to install CircuitPython on the target microprocessor, in my case the [Adafruit KB2040][03].
I followed the tutorial in the video
"[How to Install CircuitPython on a KB2040 board (OR ANY OTHER!)][04]".
Below is a summary of the installation steps:

1. Connect the KB4020 board to you computer via a USB-C cable.
   You'll see a new drive on your computer, typically called `CIRCUITPY` if CircuitPython has already installed.
   If CircuitPython is cleanly installed, move to step 5.
   If not, you should remove all the files & directories on `CIRCUITPY` by going to the next step.
2. Download the [flash erasing "nuke" `UF2` file][05] and then load this 'nuke' UF2 to the microprocessor like a typical `UF2` file.
   Press and hold the `BOOT` button and then press & release the `RESET` button, and finally release the `BOOT` button.
   If all goes well, you should have a `RPI-RP2` directory on the microprocessor.
3. Download the `.UF2` file from the [`circuitpython.org` site][06].
   Copy the `.UF2` file to the `RPI-RP2` directory.
   The microprocessor should automatically consume the `.UF2` file and reboot.
4. The `RPI-RP2` drive will disappear and a new disk drive called `CIRCUITPY` will appear
   with three files and two subdirectories.
   CircuitPython is loaded!
5. The file called `code.py` is where you will load your software but it currently contains
   a simple "Hello World" test program so you can validate all is well.
   You can do do that validation by executing in a terminal the command  `tio /dev/ttyACM0` or `tio /dev/ttyUSB0` on Linux or you can find it via `tio -L`,
   enter `Ctrl-D` to reload and observer "Hello World!" as the output.
6. Enter `Ctrl-t q` to exit serial terminal `tio`.

>**NOTE:** For ESP boards, and some others, the process is different because it requires a `.BIN` file and possibly other steps.
>Consult [`circuitpython.org` site][08], find your board, and follow the details found there.

Sources:
* [tio - a serial device I/O tool](https://github.com/tio/tio)

## Installing CircuitPython on ESP32 Microprocessor
The Espressif ESP is a very popular and worth while microprocessor used in may places,
but some of them lack a native USB,
and CircuitPython, and its development workflow work best with a native USB.

"Native USB" refers to a processor with an integrated USB peripheral,
allowing it to act directly as a USB device without needing a separate USB-to-serial converter chip,
which results in faster and more flexible data transfer speeds for applications like keyboards, mice, and custom peripherals.
In contrast to boards using external chips, this integrated approach removes the limitations of traditional UART baud rates
and can support various USB device classes and higher speeds.

So what does one do?
Consult [`circuitpython.org` site][08], find your board, and follow the details found there.

Sources
* [Dude, Where's My COM Port?](https://learn.adafruit.com/dude-where-s-my-com-port/overview)

## Creating TOML File (aka `settings.toml`)
You will find a file named `settings.toml` is added to the root folder of the CircuitPython file system (aka `CIRCUITPI`).
This file contains local wifi info and other settings.

## Using NeoVim with CircuitPython
To get a handle on how I should used NeoVim/LazyVim to develop code with CircuitPython,
I queried [Google's Gemini 2.5][01] with the following prompt:

_Gemini Prompt: How can I use LazyVim with CircuitPython?_

It gave me a very comfortable development environment with NeoVim for CircuitPython development.
The key is to combine NeoVim's editing power with command-line tools that interact with your CircuitPython board.
The core of a CircuitPython workflow involves three main tasks:

1. **Editing Code**: Writing your Python code in a text editor (NeoVim).
2. **File Management**: Transferring your `code.py` and library files to the board's `CIRCUITPY` drive.
3. **Serial Communication**: Interacting with the REPL for debugging and seeing output.

Outlined below is how to set up NeoVim for an efficient CircuitPython workflow,
for a [Basic Setup](/basic-setup:-neovim-+-a-serial-nonitor) and a [Advanced Setup](/advanced-setup:-lsp,-file-management,-and-automation) with more automation.

---------------

### Basic Setup: NeoVim + A Serial Monitor
It is very simple, you just need NeoVim and a command-line tool to view the serial output.

#### Step 1: Install a Serial Monitor Tool - DONE
Your CircuitPython board provides a serial console (the REPL) over USB.
You need a tool to connect to it.
A great, modern choice is [`tio`][02], instead of the older `screen`.
`tio` is specifically intended as a simpler serial device tool for working with
serial TTY devices with less focus on classic terminal/modem features
and more focus on the needs of embedded developers and hackers.

```bash
# install serial monitor tool
sudo apt install tio
```

You'll also need to know your board's serial port name.
This will likely be `/dev/ttyACM0` or `/dev/ttyUSB0` on Linux or you can find it via `tio -L`.
Make sure you share a group with the above devices:

```bash
# what groups are you part software
$ groups jeff
jeff : jeff adm cdrom sudo dip plugdev users lpadmin libvirt

# make yourself part of the dialout group so you can access the device
sudo usermod -aG dialout jeff

# NOTE: you'll need to log out and log back in for the group changes to take effect
# group membership is evaluated at login time
```

Sources:
* [How to Use Tio — Connecting to Serial Devices with Linux](https://www.tomshardware.com/software/linux/how-to-use-tio-connecting-to-serial-devices-with-linux)

#### Step 2: The Workflow

1. Mount the Board: Plug in your CircuitPython board. It will mount as a USB drive named `CIRCUITPY`.
2. Edit Your Code: Open or create your `code.py` file in NeoVim (`nvim <path-to-your-project>/code.py`).
3. Use NeoVim's Built-in Terminal: You don't need a separate terminal window. Open a terminal split inside NeoVim.
    * In Normal mode, type `:split` followed by `:terminal` to open a horizontal terminal.
    * Or, use the combined command `:term` to open it in a new tab.
    * Or, open a terminal outside of `nvim` using  `tio /dev/ttyACM0` or `tio /dev/ttyUSB0` on Linux or you can find it via `tio -L`.
4. Connect to the REPL: In the new NeoVim terminal pane, start `tio` with: `tio <path-to-device>`
   (typically `tio /dev/ttyACM0` or `tio /dev/ttyUSB0` on Linux or you can find it via `tio -L`)
   You will now see the serial output from your board right inside NeoVim! Use `Ctrl-t q` to quit `tio`.
5. Copy Files: After saving your `code.py` (via the command `:w`), you need to copy it to the `CIRCUITPY` drive.
   You can do this from another terminal or by using a NeoVim command: `:!cp % <path-to>/CIRCUITPY/code.py`
   (The `%` symbol in a NeoVim command refers to the current file path).

This Basic Setup does the job required and all commands are contained within NeoVim's tabs or splits.

```bash
# load nvim with your program on your pc and make your edits
nvim <file-to-edit>.py

# within nvim, save your edits to your pc at the same file location
:w

# within nvim, copy you program to the microprocessor's copy.py file
:!cp % /media/jeff/CIRCUITPY/code.py

# find the path to your device
tio -L

# open a terminal outside of nvim and control python REPL and monitor code.py output
tio /dev/ttyACM0
```

---------------

### Advanced Setup: LSP, File Management, and Automation
You can improve this workflow with plugins and language server support.
This example uses LazyVim for plugin management and Lua for configuration.

#### Step 1: Create a Project and Install CircuitPython Stubs
For each of your CircuitPython projects, it's best practice to have a dedicated virtual environment.
This environment will hold the stubs that match the version of CircuitPython and the specific board you are using.

1. Create a Project Directory:

    ```bash
    mkdir my-circuitpython-project
    cd my-circuitpython-project
    ```

2. Create and Activate a Python Virtual Environment:

    ```bash
    # create and activate a virtual environment
    python3 -m venv .venv
    source .venv/bin/activate
    ```

3. Install Stubs: The easiest way to get the correct stubs is using `adafruit-circuitpython-stubs` (or `circup`).

    ```bash
    # install the stubs (this installs stubs for ALL boards)
    # this is the cleanest way to manage stubs on a per-project basis
    pip install adafruit-circuitpython-stubs
    # OR
    # This will install stubs for all boards running 8.x
    circup install --path ./.venv/lib/python*/site-packages/ adafruit-circuitpython-stubs
    ```

#### Step 2: Configure LazyVim for CircuitPython
LazyVim is designed to be extended easily.
We will create a new plugin specification file to configure the Python language server (`pyright`) to recognize our stubs.

1. Create a Custom Plugin Configuration File:
   Create a new file in your NeoVim configuration directory.
   A good name would be `circuitpython.lua`.
   The path for your new config file: `~/.config/nvim/lua/plugins/circuitpython.lua`.
2. Add the Configuration:
   Paste the following Lua code into your new `circuitpython.lua` file.
   This code does two main things:
* Tells `pyright` (the Python LSP) to look for types and modules in the stubs directory we created.
* Adds a convenient command (`:CpREPL`) to open the CircuitPython REPL directly inside NeoVim.

```bash
-- ~/.config/nvim/lua/plugins/circuitpython.lua
return {
  -- Configure the Python language server (pyright)
  {
    "neovim/nvim-lspconfig",
    opts = {
      servers = {
        -- pyright is the default for python-lsp
        pyright = {
          settings = {
            python = {
              analysis = {
                -- This is the key part: add the stubs path.
                -- This tells pyright where to find all the CircuitPython modules.
                -- You might need to adjust the python version directory (e.g., python3.11)
                extraPaths = {
                  "./.venv/lib/python*/site-packages",
                },
                -- Optional: Disable diagnostics for imports that exist on the board
                -- but might not be in the stubs bundle (e.g., libraries you added manually).
                reportMissingImports = "warning",
              },
            },
          },
        },
      },
    },
  },

  -- Add a command and keymap to easily open the serial REPL
  {
    "nvim-lua/plenary.nvim",
    -- This is just to ensure this config runs after a core plugin
    dependencies = { "lazyvim/lazyvim" },
    config = function()
      -- Find the serial port.
      -- Linux is typically /dev/ttyACM0, macOS is /dev/tty.usbmodem*
      -- You might need to change this!
      -- Run `tio -L` in your terminal to list available serial devices.
      local serial_port = vim.fn.glob("/dev/ttyACM*")
      if vim.fn.empty(serial_port) then
        serial_port = vim.fn.glob("/dev/tty.usbmodem*")
      end

      -- Create a user command to open the REPL
      vim.api.nvim_create_user_command("CpREPL", function()
        if vim.fn.empty(serial_port) then
          vim.notify("CircuitPython device not found.", vim.log.levels.ERROR)
          return
        end
        -- Use NeoVim's built-in terminal
        vim.cmd("vsplit | terminal tio " .. serial_port)
        vim.notify("Opened TIO for " .. serial_port)
      end, {
        desc = "Open CircuitPython REPL in a vertical split",
      })

      -- Optional: Create a keymap for even faster access
      -- <leader>cr for "CircuitPython REPL"
      vim.keymap.set("n", "<leader>cr", "<cmd>CpREPL<cr>", {
        desc = "Open CircuitPython REPL",
      })
    end,
  },
}
```

#### Step 3: The Workflow
You have an integrated workflow.

1. Connect Your Device: Plug your CircuitPython board into your computer. It should mount as a drive named `CIRCUITPY`.
2. Start NeoVim: Navigate to your project directory and start Neovim.

    ```bash
    cd my-circuitpython-project
    source .venv/bin/activate      # Important for command-line tools
    nvim
    ```

3. Edit Your Code:
      * Open your `code.py` file from the `CIRCUITPY` drive.
  You can use Telescope (`<leader>ff`) to find it or open it directly: `nvim /Volumes/CIRCUITPY/code.py`.
      * As you type, you will now get autocompletion for `board`, `digitalio`, `time`, and any other CircuitPython core modules!
      * You will also get type checking and linting, helping you catch errors before you even save the file.

4. Upload Your Code:
   This is now very simple.
   Just save the file (`:w`). The board will automatically detect the change to `code.py` and restart, running your new code.

5. Open the REPL:
   To see program output (`print()` statements) or interact with your code live,
   open the REPL using the command or keymap we created:
      * Type `:CpREPL` and press Enter.
      * Or, press `<Space>cr` (assuming your leader key is Space).
This will open your serial monitor in a new vertical split right inside NeoVim.
You can press `Ctrl+C` and `Ctrl+D` in the terminal window to restart your board and see the boot-up messages and code output.

#### Summary of Benefits
By following these steps, you have configured LazyVim to be a first-class CircuitPython IDE with:

* Intelligent Autocompletion: For all CircuitPython-specific modules.
* Static Analysis & Error Checking: `pyright` will warn you about incorrect types or function calls.
* Integrated REPL: No need to leave your editor to see serial output or interact with your device.
* Seamless "Upload": Your code runs as soon as you save the file.
* All LazyVim Features: You still have access to Telescope, Git integration, and all the other powerful features LazyVim provides.


---------------


[01]:https://gemini.google.com/app
[02]:https://github.com/tio/tio
[03]:https://www.adafruit.com/product/5302
[04]:https://www.youtube.com/watch?v=BYDmXIYNKs0
[05]:https://learn.adafruit.com/adafruit-kb2040/circuitpython
[06]:https://circuitpython.org/board/adafruit_kb2040/
[07]:https://www.pythonmorsels.com/using-the-python-repl/
[08]:https://circuitpython.org/downloads

