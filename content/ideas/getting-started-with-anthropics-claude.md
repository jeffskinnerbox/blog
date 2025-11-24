<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg"
        title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------

**Intrusive thoughts** are unwanted, persistent, and distressing thoughts that repeatedly enter a person's mind.
They can be vivid, vivid, or even terrifying, and they can cause significant anxiety and distress.

**Introspective awareness** is the ability to observe and understand your own mental and emotional states, such as your thoughts, feelings, and behaviors.
It involves self-reflection, where you pause to examine and gain clarity on your inner workings, which can lead to greater self-awareness,
emotional regulation, and a better alignment of your actions with your values

* [What Are Intrusive Thoughts?](https://health.clevelandclinic.org/intrusive-thoughts)
* [Introspection and How It Is Used In Psychology](https://www.verywellmind.com/what-is-introspection-2795252)
* [Claude can identify its ‘intrusive thoughts’](https://www.transformernews.ai/p/claude-can-identify-its-intrusive-ai-introspection)





## Step 1
I read the following documents and viewed these videos:
* [Claude Code Explained for Beginners](https://www.youtube.com/watch?v=sxp-VXbXZU4)
* [Claude Code best practices | Code w/ Claude](https://www.youtube.com/watch?v=gv0WHhKelSE&t=6s)
* [How I use Claude Code for real engineering](https://www.youtube.com/watch?v=kZ-zzHVUrO4&t=149s)
* [Mastering Claude Code in 30 minutes](https://www.youtube.com/watch?v=6eBSHbLKuN0)
* [Get ANY Claude Skill You Want in Minutes (Live demo)](https://www.youtube.com/watch?v=MJ3F1-bfaVY)

I followed the video and applied what I learned to an existing project.
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







* [What is Claude Computer Use and How Do I Use It (Beginner's Tutorial)](https://www.youtube.com/watch?v=8xRNlhkHBU0&t=10s)

* [Start with Anthropic's Claude Large Language Model - One of the Strongest OpenAI ChatGPT Competitor](https://www.youtube.com/watch?v=eYBwofyE0Pk&list=PLO89phzZmnHjp4UrbZFbnV2DUZ7owBIre&index=2)
* [You're Using AI WRONG (Terminal vs ChatGPT)](https://www.youtube.com/watch?v=MsQACpcuTkU)
* [How Claude Code is built](https://newsletter.pragmaticengineer.com/p/how-claude-code-is-built)
* [Claude Code: Best practices for agentic coding](https://www.anthropic.com/engineering/claude-code-best-practices)
* [Claude Code - 47 PRO TIPS in 9 minutes](https://www.youtube.com/watch?v=TiNpzxoBPz0)
* [Claude Code Skills: Automate Everything You Do](https://www.youtube.com/watch?v=vOW1xAVbuNI)
* [How I use Claude Code for real engineering](https://www.youtube.com/watch?v=kZ-zzHVUrO4)
* [Claude Code Tutorial](https://www.youtube.com/playlist?list=PL4cUxeGkcC9g4YJeBqChhFJwKQ9TRiivY)
* [Claude Docs: Claude Code Overview](https://docs.claude.com/en/docs/claude-code/overview)
* [Claude Code Setup Guide: Clearing Up Common Myths (FULL DEMO)](https://www.youtube.com/watch?v=0F_jW4XC1NM)
* [6 Months of Claude Code Lessons in 27 Minutes](https://www.youtube.com/watch?v=rfDvkSkelhg)
* [Claude Docs: Claude Code Quickstart](https://docs.claude.com/en/docs/claude-code/quickstart)



## Prompt Engineering
Anthropic defines prompt engineering as the process of crafting and structuring prompts to
guide large language models (LLMs) like Claude toward producing desired outputs.
It involves carefully designing input text to steer the model's tone, style, and behavior for specific use cases,
and is seen as a subset of the broader concept of context engineering.
This technique can be used to improve accuracy, align with brand voice,
and enhance the model's ability to perform specific tasks without retraining the model itself.
* [Prompting Best Practices](https://docs.claude.com/en/docs/build-with-claude/prompt-engineering/claude-4-best-practices)
* [Anthropic Prompt Engineering Overview](https://jimmysong.io/en/ai/anthropic-prompt-engineering/)

## Context Engineering
Anthropic defines context engineering as the set of strategies for curating
and maintaining the optimal set of information (tokens) during LLM inference,
extending beyond traditional prompt engineering to manage the entire information ecosystem surrounding the AI agent.
* [Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
* [How to Perform Effective Agentic Context Engineering](https://towardsdatascience.com/how-to-perform-effective-agentic-context-engineering/)

## Anthropic’s “Prompt Improver”
Anthropic launched the “[Prompt Improver][01]” makes AI-assisted prompt writing a reality.
This tool can transform your simple prompt into an optimized, more efficient version in just one minute.
To use it, just visit the [Anthropic Console][02] and get started

Sources:
* [Anthropic Launches Claude Smart Improver: “One-Click Optimization” for Your AI Prompts!][01]
* [Anthropic's Prompt Optimizer Tool](https://www.youtube.com/shorts/BGJMGy0NRak)
* [Generate better prompts in the developer console](https://claude.com/blog/prompt-generator)

## MCP vs. SKILL.md
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

























# Getting Started With Claude
The command-line interface (CLI) development environment is getting an major upgrade via an AI agent.
So what is this "AI agent" ..., well check out [this article][10] but a quick definition is below:

>**DEFINITION:** An AI agent is a software system that uses artificial intelligence to perform tasks autonomously on behalf of a user.
>These agents can reason, plan, and have a memory to complete goals and adapt to new information.
>Terminal versions like Gemini CLI and Claude Code function as AI agents by
>integrating into a developer's command-line workflow to assist with tasks like writing and debugging code.

Before going deep into Claude Code,
familiarize yourself with it nearest competitor, [Gemini CLI][11].

Setting up Gemini CLI is quick and easy, but first we must have Node.js properly installed.
Here we will establish a local version of Node.js for the users login account.

```bash
# Step 1: Prerequisites
# The first step is to install Node 20+ on your machine.
# Lets find out what is currently install
whereis node
which node
node --version

# Step 2: Install "nvm" which is a cross-platform Node.js version manager
# See https://nodejs.org/en/download
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash

# in lieu of restarting the shell
\. "$HOME/.nvm/nvm.sh"

# Step 3: Download and install Node.js
nvm install 24

# Verify the Node.js version:
node -v # Should print "v24.11.0".

# Verify npm version:
npm -v # Should print "11.6.1".
```

Now let's install the Google Gemini CLI AI agent:

```bash
# Step 4: install Gemini CLI globally
npm install -g @google/gemini-cli

# Step 5: Start a Session
# Launching gemini will prompt you to choose a theme, followed by a login method:
gemini
```

The installation of Claude Code is very similar to Gemini CLI.
Here is the install:

```bash
# To installs Claude Code globally on your system,
# Run the following command in your terminal:
npm install -g @anthropic-ai/claude-code


Step 2: Start a Session
Navigate into any project directory and launch the CLI:

cd /path/to/your/project

claude
```

Sources:
* [Claude Code CLI vs Codex CLI vs Gemini CLI: Best AI CLI Tool for Developers in 2025?][10]
* [Gemini CLI: your open-source AI agent][11]

[10]:https://www.codeant.ai/blogs/claude-code-cli-vs-codex-cli-vs-gemini-cli-best-ai-cli-tool-for-developers-in-2025
[11]:https://blog.google/technology/developers/introducing-gemini-cli-open-source-ai-agent/


---------------


## Model Context Protocol (MCP)

The Model Context Protocol (MCP) is an open standard and open-source framework that aims to standardize how AI systems,
particularly large language models (LLMs), interact with external tools, data sources, and services.
It essentially acts as a universal translator,
allowing AI models to seamlessly access and utilize information from diverse systems.

* [Model Context Protocol (MCP), clearly explained (why it matters)](https://www.youtube.com/watch?v=7j_NE6Pjv-E)
* [Why MCP really is a big deal | Model Context Protocol with Tim Berglund](https://www.youtube.com/watch?v=FLpS7OfD5-s)
* [How to Build Your First MCP Server using FastMCP](https://medium.com/data-science-collective/how-to-build-your-first-mcp-server-using-fastmcp-170873fb7f1e)
* [The Complete Guide to Model Context Protocol](https://machinelearningmastery.com/the-complete-guide-to-model-context-protocol/)
* [Introducing the Model Context Protocol](https://www.anthropic.com/news/model-context-protocol)
* [Model Context Protocol (MCP)](https://modelcontextprotocol.io/introduction)
* [GitHub: modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers)
* Tutorial: [MCP Servers](https://www.youtube.com/playlist?list=PLMVV8yyL2GN_bCpeCPYG40rs7ySxu3gna)

### MCP Server Example Code
* [How I Built My First Python MCP Server (And Made AI More Useful)](https://python.plainenglish.io/how-i-built-my-first-python-mcp-server-and-made-ai-more-useful-880db4ed23a8)
* [Build a Python MCP Client to Test Servers From Your Terminal](https://realpython.com/python-mcp-client/)
* [FastMCP Quickstart: Build Remote MCP Servers w/ Python](https://www.youtube.com/watch?v=bOYkbXP-GGo)
  * FastMCP - [GitHub: jlowin/fastmcp](https://github.com/jlowin/fastmcp)
* [Model Context Protocol Isn't Confusing If You Understand It This Way](https://intoai.pub/p/model-context-protocol)
* [Building Your First AI Agent (That Will Actually Improve You As An AI Engineer)](https://intoai.pub/p/building-your-first-ai-agent)
* [List of Model Context Protocol Servers](https://github.com/modelcontextprotocol/servers)
* [This is my favorite MCP server to use with my local LLM](https://www.xda-developers.com/favorite-mcp-server-use-local-llm/)

## Claude Code
[Claude Code][01] is an agentic coding tool that lives in your terminal, understands your codebase,
and helps you code faster by executing routine tasks, explaining complex code, and handling git workflows - all through natural language commands.

```bash
# Install Claude Code
npm install -g @anthropic-ai/claude-code

# --OR --

# alternative native install
curl -fsSL https://claude.ai/install.sh | bash

# Navigate to your project
cd your-awesome-project

# Start coding with Claude
claude
# You'll be prompted to log in on first use
```

Claude provides a [quickstart guide][02] to get you using AI-powered coding assistance in just a few minutes.
By the end, you’ll understand how to use Claude Code for common development tasks.

Sources:
* [Claude Docs: Claude Code Overview](https://docs.claude.com/en/docs/claude-code/overview)
* [Claude Code Setup Guide: Clearing Up Common Myths (FULL DEMO)](https://www.youtube.com/watch?v=0F_jW4XC1NM)
* [Claude Code Tutorial](https://www.youtube.com/playlist?list=PL4cUxeGkcC9g4YJeBqChhFJwKQ9TRiivY)
* [6 Months of Claude Code Lessons in 27 Minutes](https://www.youtube.com/watch?v=rfDvkSkelhg)

## Claude Code Sandboxing
Claude Code runs on a permission-based model:
by default, it's read-only, which means it asks for permission before making modifications or running any commands.
There are some exceptions to this: we auto-allow safe commands like echo or cat, but most operations still need explicit approval.

Constantly clicking "approve" slows down development cycles and can lead to ‘approval fatigue’,
where users might not pay close attention to what they're approving, and in turn making development less safe.
Sandboxing creates pre-defined boundaries within which Claude can work more freely,
instead of asking for permission for each action. With sandboxing enabled,
you get drastically fewer permission prompts and increased safety.

Source:
* [Beyond permission prompts: making Claude Code more secure and autonomous](https://www.anthropic.com/engineering/claude-code-sandboxing)

## Claude Code & NeoVim
* [GitHub: greggh/claude-code.nvim][03] - Seamless integration between Claude Code AI assistant and Neovim
* [GitHub: coder/claudecode.nvim][04] - Claude Code Neovim IDE Extension
* [Replacing Cursor With Neovim and Claude Code](https://danielmiessler.com/blog/replacing-cursor-with-neovim-claude-code)
* [Claude Code is Killing My Neovim Addiction](https://levelup.gitconnected.com/claude-code-is-killing-my-neovim-addiction-8d2c4768a6a0)
* [Why Vim and Neovim Developers Should Embrace Claude Code for App Development](https://techxtrasol.com/resources/why-vim-and-neovim-developers-should-embrace-claude-code-for-app-development)
* [Top Community Integrations for Using Claude in Neovim (2025)](https://skywork.ai/blog/claude-neovim-plugins-2025/)

## Claude Code Web
Sources:
* [Claude Code on the web](https://www.youtube.com/watch?v=s-avRazvmLg)
* [Claude Code Web Is the Future of AI Development](https://www.youtube.com/watch?v=LDScpaOP2mA)

## Claude Desktop
Claude Desktop is a dedicated application that brings Claude AI directly to your computer,
allowing you to use its features like file creation and editing without a web browser.
The desktop app integrates seamlessly into your workflow, offering capabilities such as accessing files,
and in some cases, direct control over the computer to perform tasks like creating Excel files or analyzing screenshots,
according to the Claude Help Center and Reddit users.

>**NOTE:** As of July 22, 2025,
>_Claude Desktop is not yet available on Linux.
>Linux users can proceed to the [building a client tutorial](https://modelcontextprotocol.io/quickstart/client)
>to build an MCP client that connects to the server you are building._

* [Install Claude Desktop in Linux](https://medium.com/@abhirupkonwar04/install-claude-desktop-in-linux-a8da40237c0a)
* [Claude Desktop for Linux](https://github.com/aaddrick/claude-desktop-debian)
* [How to Install Claude Desktop with MCP Desktop Commander on Ubuntu/Debian Linux](https://studiozandra.com/how-to-install-claude-desktop-with-mcp-desktop-commander-on-ubuntu-debian-systems/)
* [How to Install Claude-Desktop on Ubuntu & Build an MCP Project](https://www.youtube.com/watch?v=NqMU9cL2LfE)

## Claude Skills
In simple terms, Claude Skills are just folders that contain information that Claude can load whenever it thinks they might be relevant.
Skills tell Claude how to complete a task, such as generating a report, a presentation,
or a coding task in a repeatable way that is customized to your own company’s needs.
As Anthropic’s product lead put it,
these Skills are a way to teach agents to do a good job “in their specific context”.

Claude Skills are pre-programmed instructions, context, and code that users can create and add to Claude to give it specialized,
reusable behaviors and make it an "expert" at specific tasks.
Instead of relying on a single, lengthy prompt for a complex or repeated task, a user can trigger a skill,
which bundles the necessary expertise into a manageable component.
This allows for more consistent and reliable performance on tasks like generating documents in a specific company format or processing data in a certain way.

A Skill is a directory that contains a `SKILL.md` file.
Skills are simply `folders/` directories that include instructions, scripts, and resources that Claude can discover and load on a task-specific basis.
Each Skill teaches Claude instructions to achieve a task better.
This could range from guidance on working with various file types (such as PDFs, CSV files, and others) to adhering to an organization’s brand guidelines.

Sources:
* [What are Claude Skills and how can you use them for product-related work?](https://departmentofproduct.substack.com/p/what-are-claude-skills-and-how-can)
* [Introducing Agent Skills](https://www.anthropic.com/news/skills)
* [Build Your Own Claude SKILLS in under 15 Minutes!](https://www.youtube.com/watch?v=zqkmlYeNU3w)
* [Public repository for Skills](https://github.com/anthropics/skills)
* [Claude Skills - SOPs For Agents](https://www.youtube.com/watch?v=fvUGQFtJaT4)
* [The Complete Guide to Anthropic Agent Skills: Cloud.ai, Claude Code & API](https://www.youtube.com/watch?v=Ihoxov5x66k)
* [I Tried Anthropic's NEW Claude Skills Feature (You Need to See This)](https://www.youtube.com/watch?v=mXkU36dvRi0)
* [Claude Skills: Everything That You Need To Get Started](https://intoai.pub/p/claude-skills)
* [What to know about Claude Skills (and why it's a big deal)](https://bdtechtalks.substack.com/p/what-to-know-about-claude-skills)

## Claude Developer Platform
The Claude Developer Platform is a suite of tools and APIs that allows developers to integrate
Anthropic's Claude AI models into their own applications and products.
It includes APIs, SDKs, documentation, and console experiences for building AI-powered features like
chatbots, automated agents, and other tools for tasks such as customer support and productivity enhancement.

Sources:
* [Building the future of agents with Claude](https://www.youtube.com/watch?v=XuvKFsktX0Q)

## Claude Computer Use
**What are Computer Use Agents?**
Computer-use agents (CUA) are AI programs designed to interact with a computer's graphical user interface (GUI),
simulating human actions to perform tasks like browsing websites, filling out forms, and using applications.
They combine reasoning from large language models (LLMs) with vision models to understand what's on the screen
and interact with it by performing clicks, typing, and other inputs.
This enables automation of digital tasks without needing direct API access,
making them powerful tools for AI-driven automation in various applications,
from customer service to business workflows.

Source:
* [What is Claude Computer Use and How Do I Use It (Beginner's Tutorial)](https://www.youtube.com/watch?v=8xRNlhkHBU0&t=10s)
* [Computer Use Agents DEEP DIVE](https://www.youtube.com/watch?v=t9kz9P6cEYM)



[03]:https://github.com/greggh/claude-code.nvim
[04]:https://github.com/coder/claudecode.nvim


---------------


## Claude Code Tutorial
* [Claude Code Tutorial](https://www.youtube.com/playlist?list=PL4cUxeGkcC9g4YJeBqChhFJwKQ9TRiivY)
* [Engineering at Anthropic](https://www.anthropic.com/engineering)
* [Claude Code: Best practices for agentic coding](https://www.anthropic.com/engineering/claude-code-best-practices)

## Slash Commands & Prompt Systems for Claude Code
* [Stop Telling Claude Code What To Do](https://www.youtube.com/watch?v=8_7Sq6Vu0S4)
  * [GitHub: glittercowboy/taches-cc-prompts](https://github.com/glittercowboy/taches-cc-prompts)
