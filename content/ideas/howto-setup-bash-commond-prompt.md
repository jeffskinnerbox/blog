<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.1
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg"
        title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------


# XXX

Sources:
* [What is the $PS1 Variable in Linux — Unix][01]
* [Bash users: What do you have for your $PS1?](https://web.archive.org/web/20180825215337/https://www.reddit.com/r/programming/comments/697cu/bash_users_what_do_you_have_for_your_ps1/)
* [What is your favorite Bash prompt?](https://web.archive.org/web/20161214154424/https://stackoverflow.com/questions/103857/what-is-your-favorite-bash-prompt)
* [What is the difference between PS1 and PROMPT_COMMAND?](https://stackoverflow.com/questions/3058325/what-is-the-difference-between-ps1-and-prompt-command)
* [My New Favorite Bash Prompt](https://brettterpstra.com/2009/11/17/my-new-favorite-bash-prompt/)
* [$PROMPT_COMMAND  –  Commands to Execute Before Printing The Prompt][06]
* [Bash/Prompt customization](https://wiki.archlinux.org/title/Bash/Prompt_customization)
* [README-bash-prompt](https://gist.github.com/rickumali/92e4c5d8e28cb8078ca4d52b26b0a016)

## Primary Prompt String (PS1)
The [`PS1`][01] is a Linux environment variable, called the primary prompt string,
that defines the format of the command prompt displayed in the terminal.
It stands for “Prompt String 1” and is used to customize the appearance of the prompt.

The contents of `PS1` are interpreted by the shell and displayed as the command prompt before each new command line.
It can contain various [escape sequences and special characters][04] that are expanded
or replaced with specific values when the prompt is displayed.
The default value of `PS1` is `‘\s-\v\$ ’`, which includes the current username, hostname, and current working directory,
followed by the `$` symbol for a regular user or the `#` symbol for the root user.
See ["Controlling the Prompt"][02] for the complete list of escape sequences that are expanded before `PS1` is displayed.

There are several other prompt strings.
The `PS0` parameter is expanded like `PS1` and displayed by interactive shells
after reading a command and before the command is executed.
`PS2` is the secondary prompt string and has a default value is `‘> ’`.
`PS2` is expanded in the same way as `PS1` before being displayed.
`PS3` variable is used as the prompt for the select command.
If this variable is not set, the select command prompts with `‘#? ’`.
The `PS4` parameter is expanded like `PS1`
and the expanded value is the prompt printed before the command line is echoed
when the `-x` option is set (see ["The Set Builtin"][03]).
The first character of the expanded value is replicated multiple times, as necessary,
to indicate multiple levels of indirection.
The default is `‘+ ’`.

Bash expands and displays `PS1` before reading the first line of a command,
and expands and displays `PS2` before reading the second and subsequent lines of a multi-line command.
Bash expands and displays `PS0` after it reads a command but before executing it.

Customizing Bash Prompt - <https://www.baeldung.com/linux/customize-bash-prompt>
* Note that our changes are not permanent when we set a value directly to the PS1 shell variable through the command-line interface.
* Except for escape characters, we may incorporate shell commands in the expression we set to the PS1 shell variable.
* We set terminal colors with non-printable escape character sequences. A color character sequence starts with a \[\033[ or \[e[, and ends with a \].
* The Bash shell evaluates the PROMPT_COMMAND variable contents just before it prints the primary command prompt.

## PROMPT_COMMAND
If the shell variable [`PROMPT_COMMAND`][06] is set, and is an array,
the value of each set element is interpreted as a command to execute before printing the primary prompt `PS1`.
If this is set, but not an array variable, its value is used as a command to execute instead.
Bash executes the values of the set elements of the `PROMPT_COMMAND` array variable
as commands before printing the primary prompt `PS1` (see [Bash Variables][05]).

[Bash Prompt Escape Sequences][07]

## Design For PS1 / PROMPT_COMMAND

### Very Basic Design

```bash
# -----  traditional coding of PS1, using only the bash prompt escape sequences -----
PS1="\[\033[01;32m\]\u@\h: \[\033[01;34m\]\w\[\033[00m\] [$?] \$ "

# -----  same as above except replacing some escape sequences with inline shell commands -----
PS1="\[\033[01;32m\]$(whoami)@$(hostname): \[\033[01;34m\]\w\[\033[00m\] [$?] \$ "

# -----  same as above except replacing some escape sequences with shell variables -----
GREEN="\[\033[0;32m\]"
BLUE="\[\033[0;34m\]"
NCOLOR="\[\033[0;39m\]"            # return color to Terminal setting for text color
PS1="${GREEN}$(whoami)@$(hostname): ${BLUE}\w${NCOLOR} [$?]\$ "
```

### Using PROMPT_COMMAND
Now lets make use of the `PROMPT_COMMAND` in this continuing example.
We are making use of this command to capture dynamic status of the system.
We'll show how to capture command errors status and status of where we are in the file system.

```bash
# -----  same as above except adding color coding for error code -----
# import the colors used for terminal characters
source ~/.bash/bash_colors.sh

prompt_command() {
  # this MUST be the very first operation within the PROMPT_COMMAND so `$?` value isn't over written
  if [ $? -eq 0 ]; then
      ERRPROMPT="\$ "
  else
      ERRPROMPT="${RED}[$?]\$${NCOLOR} "
  fi

  PS1="${GREEN}\u@\h: ${BLUE}\w${NCOLOR} $ERRPROMPT"
}
PROMPT_COMMAND=prompt_command
```

### Dynamic PS1 Design Pattern
Now lets make the `PS1` prompt more dynamic by potentially changing it after every command-line entry.

* Create project directories called `test-1` and `test-2` and make them separate python virtual environment:

```bash
# create your test-1 project directory
mkdir -p ~/tmp/test-1
cd ~/tmp/test-1
python3 -m venv .venv

# create your test-2 project directory
mkdir -p ~/tmp/test-2
cd ~/tmp/test-2
python3 -m venv .venv
```

* Create another project directory called `test-2`:

```bash
# activate the test-1 python virtual environment
cd ~/tmp/test-1
source .venv/bin/activate

deactivate
```



```bash
# -----  same as above except adding color coding for error code -----
# import the colors used for terminal characters
source ~/.bash/bash_colors.sh

# ----------------------- Prompt for Python Virtual Environment -----------------------
function prompt_command() {
  # this MUST be the very first operation within the PROMPT_COMMAND so `$?` value isn't over written
  if [ $? -eq 0 ]; then
      ERRPROMPT=" \$ "
  else
      ERRPROMPT=" ${RED}[$?]\$${NCOLOR} "
  fi

  # function returns true/false if the directory your in has an active virtual environment
  function in_active_venv_dir() {
    [[ "$PWD/.venv" == "$VIRTUAL_ENV" ]]
  }

  # function returns true/false if there is an active virtual environment somewhere
  function venv_is_active() {
    [[ -n "$VIRTUAL_ENV" ]]
  }

  # function returns true/false if the directory your in has a virtual environment but nothing is active
  function in_venv_dir() {
    [[ -d "$PWD/.venv" ]]
  }

  # function to create the python virtual environment message in PS1 prompt
  function set_venv_prompt() {
    if in_active_venv_dir; then                                          # Case 1: your in a directory with an active python virtual environment
      local VENV_PROJ_NAME="$(echo "$VIRTUAL_ENV" | awk -F "/" '{print $(NF-1)}')"
      VENVPROMPT="${GREEN} VENV-ACTIVE:${VENV_PROJ_NAME}${NCOLOR}"
    elif venv_is_active; then                                            # Case 2: there is an active python virtual environment but you are NOT in it
      local VENV_PROJ_NAME="$(echo "$VIRTUAL_ENV" | awk -F "/" '{print $(NF-1)}')"
      VENVPROMPT="${YELLOW} VENV-ACTIVE:${VENV_PROJ_NAME}${NCOLOR}"
    elif in_venv_dir; then                                               # Case 3: the directory you are in is a python virtual environment but it is not active
      local VENV_PROJ_NAME="$(basename $PWD)"
      VENVPROMPT="${CYAN} VENV-INACTIVE:${VENV_PROJ_NAME}${NCOLOR}"
    else                                                                 # Case 4: there is no active python virtual environment at all
      VENVPROMPT=""
    fi
  }

  # using the above functions, create your new (dynamic) PS1 prompt
  set_venv_prompt
  export PS1="${GREEN}\u@\h: ${BLUE}\w${NCOLOR}${VENVPROMPT}${ERRPROMPT}"
}

# the contents of PROMPT_COMMAND is executed immediately before PS1 is executed via the command-line
PROMPT_COMMAND=prompt_command
```

### More Complex Design Pattern
Now let do git ....

```bash
# -----  same design patten as above, but now doing it for git operations -----

# ----------------------- Prompt for Git Directory -----------------------
function prompt_command() {
  # this MUST be the very first operation within the PROMPT_COMMAND so `$?` value isn't over written
  if [ $? -eq 0 ]; then
    ERRPROMPT=" \$ "
  else
    ERRPROMPT=" ${RED}[$?]\$${NCOLOR} "
  fi

  # function to detect whether the current directory is a git repository.
  function is_git_repository() {
    git branch >/dev/null 2>&1
  }

  # determine the branch/state information for this git repository.
  function create_gitprompt() {
    # capture the output of the "git status" command for processing below
    local git_status="$(git status 2>/dev/null)"

    # Set color based on clean/staged/dirty
    if [[ ${git_status} =~ "working tree clean" ]] || [[ ${git_status} =~ "working directory clean" ]]; then
      state="${GREEN}"
    elif [[ ${git_status} =~ "Changes to be committed" ]]; then
      state="${YELLOW}"
    else
      state="${RED}"
    fi

    # set arrow icon based on status against remote
    local remote_pattern="# Your branch is (.*) of"
    if [[ ${git_status} =~ ${remote_pattern_pattern} ]]; then
      if [[ ${BASH_REMATCH[1]} == "ahead" ]]; then
        remote="↑"
      else
        remote="↓"
      fi
    else
      remote=""
    fi

    local diverge_pattern="# Your branch and (.*) have diverged"
    if [[ ${git_status} =~ ${diverge_pattern} ]]; then
      remote="↕"
    fi

    # Get the name of the branch.
    local branch_pattern="^On branch ([^${IFS}]*)"
    if [[ ${git_status} =~ ${branch_pattern} ]]; then
      branch=${BASH_REMATCH[1]}
    fi

    # set the final branch string.
    GITPROMPT=" ${state}(${branch})${remote}${NCOLOR}"
  }

  # create the GITPROMPT variable
  function set_git_prompt() {
    if is_git_repository; then
      create_gitprompt
    else
      GITPROMPT=""
    fi
  }

  # using the above functions, create your new (dynamic) PS1 prompt
  set_git_prompt
  export PS1="${GREEN}\u@\h: ${BLUE}\w${NCOLOR}${GITPROMPT}${ERRPROMPT}"
}

# the contents of PROMPT_COMMAND is executed immediately before PS1 is executed via the command-line
PROMPT_COMMAND=prompt_command
```


```bash
# ---- THIS NEEDS WORK ---- THIS NEEDS WORK ---- THIS NEEDS WORK ---- THIS NEEDS WORK ----

# ----------------------- Prompt for Conda Virtual Environment -----------------------
function set_conda_prompt() {
    if [[ "$CONDA_DEFAULT_ENV" = "" ]]; then
        CONDAPROMPT=""
    else
        CONDAPROMPT="${BBLUE}"["$CONDA_DEFAULT_ENV"]"${NCOLOR} "
    fi
}
```

### Putting It All Together




[01]:https://medium.com/@linuxadminhacks/what-is-the-ps1-variable-in-linux-unix-9932e981c276
[02]:https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html#Controlling-the-Prompt
[03]:https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html#The-Set-Builtin
[04]:https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html#Controlling-the-Prompt
[05]:https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html#Bash-Variables
[06]:https://www.bashsupport.com/bash/variables/prompt_command/
[07]:https://tldp.org/HOWTO/Bash-Prompt-HOWTO/bash-prompt-escape-sequences.html

