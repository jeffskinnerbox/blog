<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg"
    title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------

Much of this document was derived from a dialog with [Google's Gemini][03].
Here are the prompts I used:

* Gemini Prompt:
_I'm exploring the potential uses of programming environments that use a graphical interface of interlocking blocks, specifically Scratch and Blockly.
My target users are young people who are interested in a STEM experience in the professional fields of Robotics & AI.
For Scratch & Blockly, summarize for me their respective features, use cases, strengths, and weaknesses._

* Gemini Prompt:
_Recommend a specific Blockly-based platforms that integrate directly with Python for a robotics curriculum.
I'm particularly interested in something that would support the Robot Operating Platform (ROS2)._

# Scratch & Blockly
Learning to code can sometimes seem overwhelming.
A young student begins to learn the vocabulary and syntax to create a program,
but has difficulty making the leap to creating an entire program.
They have all the tools I needed, but don't know where to begin and experience writers block.
This is where a graphical interface could make it easier for a new programmer to take flight.

[Scratch][01] and [Blockly][02] are two programming environments that use a graphical interface of interlocking blocks
to make coding easier for new programmers.
Both Scratch and Blockly are leaders in visual programming,
but they serve different roles in a student's journey toward professional Robotics and AI.
While Scratch is a complete creative ecosystem,
Blockly is a developer tool used to build specialized coding interfaces for robots and AI hardware.

* [Blockly VS Scratch: What’s best for me?](https://www.robotlab.com/blog/blockly-vs-scratch-whats-best-for-me)

## Scratch Summary
Scratch is a development environment designed especially for programmers aged 8 to 16 (but it’s fun and useful for beginners of all ages).
It’s an all-inclusive environment that contains any block you need to manipulate this cute cast of characters through an environment of your creation.
More experienced scratcher’s can branch out and create games and animations all their own using Scratch’s extensive library of blocks.

## Blockly Summary
Blockly is more at home in a business setting than a classroom,
it utilizes smaller tool set but open-ended / customizable blocks to allow users to code real-world tools.
Blockly blocks can be translated directly into such languages as Javascript, PHP, Dart, and Python.

## Comparison Overview
Both Scratch and Blockly are leaders in visual programming,
but they serve different roles in a student's journey toward professional Robotics and AI.
While Scratch is a **complete creative ecosystem**,
Blockly is a **developer tool** used to build specialized coding interfaces for robots and AI hardware.


| Feature | Scratch | Blockly |
|:--------|:--------:|:---------:|
| Primary Goal | Creative expression (stories, games) | Practical application and tool building |
| End User | Children/Students (Ages 8–16) | Developers & Advanced Students |
| Code Output | Runs only within the Scratch environment | Generates Python, JavaScript, PHP, etc. |
| Extensibility | Limited to specific official/community extensions | Highly customizable; can create any block |
| Hardware | Supports Micro:bit, LEGO Mindstorms/SPIKE | Powers Dash & Dot, Arduino, VEX, and more |


### Scratch: The Entry Point
Developed by MIT, Scratch is designed for "creative learning."
In the context of AI and Robotics,
it is best for teaching logic and high-level concepts without technical overhead.

* **Key Features:** Users control "sprites" (characters) on a 2D stage.
  * **Built-in Assets:** Comes with a massive library of sounds, costumes, and backgrounds.
  * **AI Extensions:** Official extensions for Face Sensing and Video Sensing;
    third-party extensions (like Machine Learning for Kids) allow students to train their own AI models.
* **Strengths:**
  * **Low Barrier to Entry:** No "broken" code; blocks only snap if they make sense.
  * **Community:** Millions of shared projects provide a "remix" culture that encourages learning by example.
* **Weaknesses:**
  * **The "Walled Garden":** Code cannot be exported to a professional language like Python.
  * **Performance:** Not suitable for high-speed robot processing or heavy data analysis.

### Blockly: The Bridge to Professionalism
Blockly is a library created by Google.
It isn't a website you visit to "code" like Scratch; rather,
it is the engine behind many professional education tools (like Code.org or LEGO's software).

* **Key Features:** Professional level feel and features
  * **Code Generation:** The defining feature. It can show the student exactly how their blocks look in Python or JavaScript in real-time.
  * **Clean UI:** Lacks the "cartoony" feel of Scratch, which often appeals more to older students (12+).
  * **Developer-First:** Used by robotics companies to create custom interfaces for physical arms and drones.
* **Strengths:**
  * **Syntax Transition:** Best for students ready to move from blocks to text.
    It bridges the gap by showing the underlying logic in a "real" language.
  * **Hardware Integration:** Because it exports text code,
    it is more commonly used to program industrial-style robots (e.g., Niryo, Ozobot).
* **Weaknesses:**
  * **No Central Community:** Unlike Scratch, there isn't one "Blockly website" where students can share art or games;
    it is fragmented across different platforms.
  * **Less "Fun" Out of the Box:** Requires a specific implementation (like a robot kit) to be engaging.

## Recommendation for Robotics & AI
To prepare students for a professional career, a scaffolded approach is most effective:

1. **Phase 1 (Concepts):** Use Scratch to teach "if-then" logic, loops, and basic AI classification
   (e.g., "Is this a cat or a dog?").
1. **Phase 2 (Application):** Move to a Blockly-based robotics platform
   (like VEXcode VR or LEGO Education) to see how logic translates into physical movement and Python syntax.
1. **Phase 3 (Professional):** Use Blockly’s side-by-side view to start writing the Python code directly,
   eventually leaving the blocks behind.

### Specific Recommendation for ROS2
Most traditional block platforms (like standard Scratch)
lack the underlying middleware to handle ROS2's node-based architecture.
However, a few professional-grade educational platforms have specifically solved this "bridge" problem.
Here are the top recommendations:

* **[Niryo](https://niryo.com/): The Gold Standard for ROS2 Scaffolding**
   Niryo (makers of the Ned2 industrial-style arm) offers one of the most mature paths from blocks to ROS2.
   Their software is built entirely on ROS2 and is designed for the precise transition you described.
  * **How it works:** You program in Niryo Studio, which uses a Blockly interface. One click allows you to see the generated Python code.
  * **ROS2 Integration:** Because the arm runs a ROS2 stack internally, the blocks correspond directly to ROS2 actions and services. Advanced students can SSH into the robot and run the same Python scripts they saw in the Blockly interface as native ROS2 nodes.
  * **Target Field:** Industrial Automation & Collaborative Robotics.
* **[Robobo](https://theroboboproject.com/en/) (The Robobo Project)**
Robobo is an educational robot that uses a smartphone as its "brain."
It is explicitly designed with a "three-level" pedagogical approach.
  * **Scaffolded Tiers:** **1st** Scratch/Blockly: have high-level logic for beginners,
    **2nd** Python: For intermediate users, with libraries that mirror the block logic,
    **3rd** ROS: For advanced users. It provides a ROS Developer App that turns the robot into a remote ROS node.
  * **Why it's unique:** It includes a simulator (Unity and Gazebo) so students can test their
    ROS2/Python code in a virtual environment before deploying to the physical hardware.
* **[Robotics-Academy](https://jderobot.github.io/RoboticsAcademy/) (JDERobot)**
This is an open-source framework specifically for teaching professional Robotics and AI using ROS2.
  * **The Interface:** It uses a web-based coding environment that supports both Blockly and Python (via Jupyter Notebooks).
  * **ROS2 Focus:** It is built around "exercises" (like autonomous driving or drone obstacle avoidance) that use the Gazebo simulator and ROS2.
  * **Best For:** High school or early university students who want to work with Autonomous Vehicles and Drones.
* **[ATL Robotics IDE](https://github.com/AutreTechLab/ATL_Robotics_IDE) (Open Source / Advanced)**
If you are looking for a software-first approach rather than a specific hardware kit,
the ATL Robotics IDE is a dedicated project to modernize block-based coding for the ROS2 era.
  * **Core Tech:** It is a redesign of the Blockly Suite specifically for ROS2 Foxy/Humble.
  * **Hardware Agnostic:** It aims to support various robots (like Cozmo or Thymio) through a unified ROS2-Blockly interface.
  * **Strengths:** It helps solve the "terminal command" barrier of ROS2 by providing a GUI for launching nodes and topics via blocks.

Comparison for Your Curriculum:

| Platform | Best For... | ROS2 Depth | Ease of Use |
|:----------|:----------|:----------|:----------|
| Niryo | Industrial / Pro Skills | High (Native) | Excellent |
| Robobo | AI / Mobile Robotics | High (Node-based) | Good |
| Robotics-Academy | Self-Driving / Drones | Very High | Moderate (Technical) |
| ATL IDE | Custom Lab Setup | High | Moderate |


---------------

# Blocky
While surfing the web, I bumped into [this Reddit/rROS post][04].
It describes a very early effort to create a visual block-based IDE for ROS2 development, called [ROS Blocky][05].
This appears to be built using Blockly.

#### Step 1: Download Windows `.exe` File and Install - DONE
While viewing the [Getting Started][05] video, follow these steps:
  1. You can download the ROS Blocky executable at `https://ros-blocky.github.io/`.
  1. Double click on the download and click on the **Run anyway** button.
  1. When asked "Do you want to allow this app...", click the **Yes** button.
  1. After all the ROS Blocky components are installed

#### Step 2: Create a Project - DONE
1. Using the MS Explorer, create a new folder in your home directory titled `ros-blocky`.
1. Using the ROS Blocky app, create a test project called `my-test-project` within a filesystem called `ros-blocky`

#### Step 3: Add Package - DONE
In the `my_test_project` folder:
1. Within the "Packages" panel on the right, click on the **Add Package** button
1. Within the popup window, create the package `robot_description`.

#### Step 4: Build Simple URDF
While viewing the [Build Simple URDF][05] video, follow these steps:

#### Step 5: Simple Publisher
While viewing the [Simple Publisher][05] video, follow these steps:

#### Step 6:  Simple Subscriber
While viewing the [Simple Subscriber][05] video, follow these steps:

#### Step X: Try Out Other Features
At the top right on the ROS Blocky how screen,
try out TurtleSim, Joint State Publisher, RVis2, ROS 2 Topics



[01]:https://scratch.mit.edu/
[02]:https://developers.google.com/blockly
[03]:https://gemini.google.com/
[04]:https://www.reddit.com/r/ROS/comments/1pysd0n/ros_blocky_a_visual_ide_to_make_learning_ros_2/
[05]:https://ros-blocky.github.io/

