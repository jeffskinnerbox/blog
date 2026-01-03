<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg"
        title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------

Large language models (LLMs) are increasingly being recognized for their potential to act as curators of
knowledge and information, leveraging their ability to process, synthesize, and generate human-like text.
They can be used to sift through vast amounts of data, extract relevant information, and present it in a clear and concise manner,
effectively acting as a bridge between complex information and human understanding.

[ChatGPT][04], OpenAI’s text-generating AI chatbot,
was launch in November 2022 and has been steadily evolving ever since
(see evolutionary [timeline][05]).

For more information, see these sources:
* [When ChatGPT Broke an Entire Field: An Oral History](https://www.quantamagazine.org/when-chatgpt-broke-an-entire-field-an-oral-history-20250430/)
* [New Theory Suggests Chatbots Can Understand Text](https://www.quantamagazine.org/new-theory-suggests-chatbots-can-understand-text-20240122/)
* [What Are Intrusive Thoughts?](https://health.clevelandclinic.org/intrusive-thoughts)
* [Introspection and How It Is Used In Psychology](https://www.verywellmind.com/what-is-introspection-2795252)
* [Claude can identify its ‘intrusive thoughts’](https://www.transformernews.ai/p/claude-can-identify-its-intrusive-ai-introspection)

---------------

# Claude Code Installation and Usage Guide on Ubuntu
Step-by-step guide for installing Claude Code CLI on Ubuntu.
Assumes basic Linux/Bash familiarity.

## Table of Contents

* [Claude Code Installation](#claude-code-installation)
  * [Prerequisites](#prerequisites)
  * [Step 1: Open a Terminal](#step-1-open-a-terminal)
  * [Step 2: Install Claude Code](#step-2-install-claude-code)
  * [Step 3: Restart Your Terminal](#step-3-restart-your-terminal)
  * [Step 4: Verify Installation](#step-4-verify-installation)
  * [Step 5: Start Claude Code](#step-5-start-claude-code)
  * [Step 6: Authenticate](#step-6-authenticate)
  * [Step 7: Check your installation type](#step-7-check-your-installation-type)
  * [Troubleshooting](#troubleshooting)
  * [Uninstalling](#uninstalling)
* [Using Claude Code](#using-claude-code)
  * [Using `claude --help`](#using-claude---help)
  * [Built-in Commands](#built-in-commands)
  * [Slash Commands Inside Claude](#slash-commands-inside-claude)
* [Learning Claude Code](#learning-claude-code)
  * [Example Project](#example-project)
* [Key Concepts](#key-concepts)
  * [Prompt Engineering](#prompt-engineering)
  * [Context Engineering](#context-engineering)
  * [Anthropic's "Prompt Improver"](#anthropics-prompt-improver)
  * [MCP vs. SKILL.md](#mcp-vs-skillmd)

## Claude Code Installation

### Prerequisites
Before starting, ensure you have:

* **Ubuntu version**: 20.04 or newer
* **RAM**: at least 4 GB
* **Internet connection**: required for installation and usage

### Step 1: Open a Terminal
Press `Ctrl + Alt + T` to open a terminal window.

### Step 2: Install Claude Code
Copy and paste this command into your terminal, then press Enter:

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

**What this does:**
* `curl` downloads the installation script from Claude's website
* `bash` runs the script to install Claude Code

Wait for the installation to complete. You'll see progress messages.

>**Alternative Installation Methods**
>
>If you already have Node.js (requires Node.js 18+) installed: `npm install -g @anthropic-ai/claude-code`
>**DO NOT** use `sudo` with this command.
>
>If you have Homebrew installed: `brew install --cask claude-code`

### Step 3: Restart Your Terminal
Close your terminal window and open a new one (press `Ctrl + Alt + T` again).

This ensures your system recognizes the new `claude` command.

### Step 4: Verify Installation
Run this command to check that Claude Code installed correctly:

```bash
claude doctor
```

You should see version information and a success message.

### Step 5: Start Claude Code
Navigate to a project folder and start Claude Code:

```bash
cd ~/my-project    # replace with your project folder
claude
```

### Step 6: Authenticate
When Claude Code starts for the first time, it will ask you to log in.
Choose one of these options:

* Option A: Claude Console (Recommended for developers)
1. You'll see a link in your terminal
1. Open the link in your web browser
1. Log in or create an account at console.anthropic.com
1. Requires active billing set up in the Anthropic Console

* Option B: Claude Pro/Max subscription
1. If you already pay for Claude Pro or Max at claude.ai
1. Select this option when prompted
1. Log in with your existing Claude.ai account

### Step 7: Check your installation type
Validate that Claude doesn't sense that it has any problems with the installation you performed.

```bash
claude doctor
```

### Troubleshooting
Here are some typical troubles you might have with the installation:

**"command not found" error** - If you see `claude: command not found` after installation:
1. Close and reopen your terminal
2. Or run: `source ~/.bashrc`

**Permission errors** - If you get permission errors during installation:
1. Do NOT use `sudo` with the install command
2. Check Anthropic's troubleshooting guide: <https://docs.anthropic.com/en/docs/claude-code/troubleshooting>

### Uninstalling
To remove Claude Code:

```bash
claude uninstall
```

---------------

## Using Claude Code
Curated [Claude Code Cheatsheet][03] with commands, shortcuts, configuration, plugins, skills, MCP integrations, and automation workflows.
A small snapshot of this is found below:

### Using `claude --help`
Run `claude --help` to see all available options and commands:

```bash
claude --help
```

This displays a full list of flags you can use. Here are the most useful ones for beginners:

| Option | What it does |
|--------|--------------|
| `-h, --help` | Show all available options |
| `-v, --version` | Show the version number |
| `-c, --continue` | Continue your most recent conversation |
| `-r, --resume` | Resume a specific past conversation |
| `-p, --print` | Get a single response and exit (good for scripts), ex. `claude -p "What does this error mean: ENOENT?"` |
| `--model <model>` | Choose a different Claude model (e.g., `sonnet`, `opus`) |


### Built-in Commands

Claude --help also shows these subcommands:

| Command | What it does |
|---------|--------------|
| `claude doctor` | Check installation health |
| `claude update` | Check for and install updates |
| `claude mcp` | Configure MCP servers (advanced) |
| `claude install` | Install/reinstall Claude Code |


### Slash Commands Inside Claude
Once you're inside a Claude Code session, you can use **slash commands** by typing `/` followed by a command name. These are different from terminal flags.
To see all available slash commands, type on Claude's command line: `/help`

These are the commands you'll use most often:

**Linux Command Line**

| Command | Description |
|---------|-------------|
| `claude` | Start Claude Code in current directory |
| `claude doctor` | Check installation status |
| `claude --help` | Show all available options |
| `claude --version` | Show version number |

**Essential Slash Commands**

| Command | What it does |
|---------|--------------|
| `/help` | Show all available slash commands |
| `/clear` | Clear conversation history and start fresh |
| `/exit` | Exit Claude Code |
| `/model` | Change the AI model (sonnet, opus, etc.) |
| `/cost` | Show how many tokens you've used |
| `/compact` | Reduce conversation size to save tokens |


**Session Management**

| Command | What it does |
|---------|--------------|
| `/resume` | Resume a previous conversation |
| `/rename <name>` | Give your current session a name ex. `/rename refactoring-auth-module` |
| `/export` | Save conversation to a file ex. `/export my-session.md` |


**Project & Configuration**

| Command | What it does |
|---------|--------------|
| `/init` | Create a CLAUDE.md file for your project |
| `/memory` | Edit your project's CLAUDE.md file |
| `/config` | Open settings |
| `/permissions` | View or change tool permissions |


**Account & Status**

| Command | What it does |
|---------|--------------|
| `/status` | Check version, model, and account info |
| `/login` | Switch to a different account |
| `/logout` | Sign out |
| `/usage` | Show plan limits and usage (subscription only) |
| `/doctor` | Check installation health |


**Code Review & Development**

| Command | What it does |
|---------|--------------|
| `/review` | Ask Claude to review your code |
| `/todos` | Show your current task list |
| `/pr-comments` | View GitHub pull request comments |


**Advanced Commands**

| Command | What it does |
|---------|--------------|
| `/mcp` | Manage MCP server connections |
| `/hooks` | Configure automation hooks |
| `/ide` | Manage VS Code/JetBrains integration |
| `/vim` | Enable vim editing mode |
| `/terminal-setup` | Set up Shift+Enter for newlines |


---------------

## Learning Claude Code
I recommend that you read the following documents and viewed these videos:
* [Claude Code Explained for Beginners](https://www.youtube.com/watch?v=sxp-VXbXZU4)
* [Claude Code best practices | Code w/ Claude](https://www.youtube.com/watch?v=gv0WHhKelSE&t=6s)
* [How I use Claude Code for real engineering](https://www.youtube.com/watch?v=kZ-zzHVUrO4&t=149s)
* [Mastering Claude Code in 30 minutes](https://www.youtube.com/watch?v=6eBSHbLKuN0)
* [Get ANY Claude Skill You Want in Minutes (Live demo)](https://www.youtube.com/watch?v=MJ3F1-bfaVY)
* I took a free introductory course at [DeepLearning.AI](https://www.deeplearning.ai/), [Claude Code: A Highly Agentic Coding Assistant](https://www.deeplearning.ai/short-courses/claude-code-a-highly-agentic-coding-assistant/).

Some of the other tutorials, videos, and articles I reviewed and found somewhat helpful:
* [What is Claude Computer Use and How Do I Use It (Beginner's Tutorial)](https://www.youtube.com/watch?v=8xRNlhkHBU0&t=10s)
* [Start with Anthropic's Claude Large Language Model - One of the Strongest OpenAI ChatGPT Competitor](https://www.youtube.com/watch?v=eYBwofyE0Pk&list=PLO89phzZmnHjp4UrbZFbnV2DUZ7owBIre&index=2)
* [You're Using AI WRONG (Terminal vs ChatGPT)](https://www.youtube.com/watch?v=MsQACpcuTkU)
* [How Claude Code is built](https://newsletter.pragmaticengineer.com/p/how-claude-code-is-built)
* [Claude Code: Best practices for agentic coding](https://www.anthropic.com/engineering/claude-code-best-practices)
* [Claude Code - 47 PRO TIPS in 9 minutes](https://www.youtube.com/watch?v=TiNpzxoBPz0)
* [Claude Code Skills: Automate Everything You Do](https://www.youtube.com/watch?v=vOW1xAVbuNI)
* [How I use Claude Code for real engineering](https://www.youtube.com/watch?v=kZ-zzHVUrO4)
* [Claude Code Tutorial](https://www.youtube.com/playlist?list=PL4cUxeGkcC9g4YJeBqChhFJwKQ9TRiivY)
* [Claude Docs: Claude Code Overview](https://code.claude.com/docs/en/overview)
* [Claude Code Setup Guide: Clearing Up Common Myths (FULL DEMO)](https://www.youtube.com/watch?v=0F_jW4XC1NM)
* [6 Months of Claude Code Lessons in 27 Minutes](https://www.youtube.com/watch?v=rfDvkSkelhg)
* [Claude Docs: Claude Code Quickstart](https://code.claude.com/docs/en/quickstart)

I followed the video and applied what I learned to an existing project.

### Example Project
My goal is to have Claude instruct me on how to replace the Adafruit KB2040 microcontroller
with a Raspberry Pi Pico W. I need the extra GPIO pin to implement additional functionality.

```bash
# prepare your project
mkdir ~/tmp/claude-code
cp -r ~/src/projects/omnidirectional-robot/omni_robot_1/iteration_2 .
cd omni_robot_1
rm -r -f iteration_1/ iteration_3/ pictures/

# have Claude do an analysis of the project and write a report
claude "Explain what this project does and how it is structured" > project-analysis.txt

# time to use a CLAUDE.md file, make updates & edits where you can
claude "For this project, write me a CLAUDE.md file that I'll use for Python and CircuitPython coding."
```

Now I'm going to create a prompt for a major change that I plan to introduce into the code.
Specifically, the replacement of the Adafruit KB2040 microcontroller with a Raspberry Pi Pico W.
I want to make sure give Claude instruction on what I want created to make this move easy for me.

Here is my prompt:

```text
My Goal: To modify the openloop-wheel-control-v1-i2.py code to read the encoders on the N20 motors
to measure directly the speed and direction of each wheel.  I will then used a PID (proportional-integral-derivative)
feedback control mechanism to calculate continuously error value
and applies a corrections so the wheel speed matches it target value.

The Challenge: The Adafruit KB2040 microcontroller lacks sufficient pinouts to read the encoders on the three N20 motors.

My Solution: I want to replace the Adafruit KB2040 microcontroller with a Raspberry Pi Pico W which has more pinouts.

Your Task #1: I want you to instruct me on how to replace the Adafruit KB2040 microcontroller with a Raspberry Pi Pico W.
You instructions should provide a table which maps the KB2040 pin currently used,
to the Raspberry Pi Pico W pins you have selected, so I can rewire the microprocessor, motors, and motor drivers.
Also, modify the openloop-wheel-control-v1-i2.py code to reflect your change and the use of the Raspberry Pi Pico W.

Your Task #2: Give me a plan for implementing Task #1. Explain to me how to calibrate and tune this solution,
using the existing RadioMaster Boxer controller / ER4 ExpressLRS (ELRS) PWM receiver architecture.
Provide test cases to validate the solution.
```

Future Tasks: In a subsequent steps, which you should considered in your planning, but not execute at this time:
* Create the PID controller, calibrate and tune this solution, using the existing RadioMaster Boxer controller
  / ER4 ExpressLRS (ELRS) PWM receiver architecture. Provide test cases to validate the solution.
* Convert this solution so it operates the Robot Operating System 2 (ROS2) framework and no longer uses the
  RadioMaster Boxer controller / ER4 ExpressLRS (ELRS) PWM receiver architecture.
* Create testing process where I can read in test case, written in CircuitPython, to automate testing of the solution
  using the ROS2 RViz and Gazebo tools.

## Key Concepts

### Prompt Engineering
Anthropic defines prompt engineering as the process of crafting and structuring prompts to
guide large language models (LLMs) like Claude toward producing desired outputs.
It involves carefully designing input text to steer the model's tone, style, and behavior for specific use cases,
and is seen as a subset of the broader concept of context engineering.
This technique can be used to improve accuracy, align with brand voice,
and enhance the model's ability to perform specific tasks without retraining the model itself.
* [Prompting Best Practices](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-4-best-practices)
* [Anthropic Prompt Engineering Overview](https://jimmysong.io/en/ai/anthropic-prompt-engineering/)

### Context Engineering
Anthropic defines context engineering as the set of strategies for curating
and maintaining the optimal set of information (tokens) during LLM inference,
extending beyond traditional prompt engineering to manage the entire information ecosystem surrounding the AI agent.
* [Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
* [How to Perform Effective Agentic Context Engineering](https://towardsdatascience.com/how-to-perform-effective-agentic-context-engineering/)

### Anthropic’s “Prompt Improver”
Anthropic launched the “[Prompt Improver][01]” makes AI-assisted prompt writing a reality.
This tool can transform your simple prompt into an optimized, more efficient version in just one minute.
To use it, just visit the [Anthropic Console][02] and get started

Sources:
* [Anthropic Launches Claude Smart Improver: “One-Click Optimization” for Your AI Prompts!][01]
* [Anthropic's Prompt Optimizer Tool](https://www.youtube.com/shorts/BGJMGy0NRak)
* [Generate better prompts in the developer console](https://claude.com/blog/prompt-generator)

### MCP vs. SKILL.md
Why would I use a GitHub MCP instead of creating a GiutHub `SKILL.md` document?
This gets at an important distinction between MCPs and Skills.
Here are the key differences:

* GitHub MCP (Model Context Protocol)
  * Live data access: Can read your actual current repositories, issues, PRs in real-time
  * Two-way interactions: Can create issues, make commits, open PRs, not just read
  * Dynamic: Always has the latest state of your repos
  * Authentication: Works with your specific GitHub account and permissions
  * Requires setup: Needs installation and configuration outside of Claude
* GitHub SKILL.md Document
  * Static instructions: Contains best practices, workflows, and procedures for working with GitHub
  * Knowledge transfer: Teaches Claude how to use GitHub APIs, what conventions to follow, code review practices, etc.
  * No live access: Can't actually see your repos or make changes (unless combined with other tools)
  * Portable: Works immediately in any conversation without setup
  * Educational: Great for standardizing workflows, coding standards, PR templates, etc.
* Best Use Cases
  * Use MCP when you want to:
    * "Show me all open issues in my repo"
    * "Create a PR from this branch"
    * "Search my codebase for function X"
  * Use a SKILL.md when you want to:
    * Define your team's PR review checklist
    * Document your branching strategy
    * Establish coding standards and commit message conventions
    * Teach Claude your organization's GitHub workflows
  * Use BOTH together when:
    * You want Claude to access your GitHub repos (MCP) while following your team's specific practices and standards (SKILL)



[01]:https://medium.com/ai-disruption/anthropic-launches-claude-smart-improver-one-click-optimization-for-your-ai-prompts-66b6e935f95b
[02]:https://console.anthropic.com/dashboard
[03]:https://awesomeclaude.ai/code-cheatsheet
[04]:https://chatgpt.com/
[05]:https://techcrunch.com/2025/03/14/chatgpt-everything-to-know-about-the-ai-chatbot/

