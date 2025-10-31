<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg"
        title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>

---------------


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
* [Claude Docs: Claude Code](https://docs.claude.com/en/docs/claude-code/quickstart)



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
* [Introducing the Model Context Protocol](https://www.anthropic.com/news/model-context-protocol)
* [Model Context Protocol (MCP)](https://modelcontextprotocol.io/introduction)
* [GitHub: modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers)

### MCP Server Example Code
* FastMCP - [GitHub: jlowin/fastmcp](https://github.com/jlowin/fastmcp)
* [Model Context Protocol Isn't Confusing If You Understand It This Way](https://intoai.pub/p/model-context-protocol)
* [Building Your First AI Agent (That Will Actually Improve You As An AI Engineer)](https://intoai.pub/p/building-your-first-ai-agent)
* [List of Model Context Protocol Servers](https://github.com/modelcontextprotocol/servers)

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



[01]:https://www.claude.com/product/claude-code
[02]:https://docs.claude.com/en/docs/claude-code/quickstart
[03]:https://github.com/greggh/claude-code.nvim
[04]:https://github.com/coder/claudecode.nvim

