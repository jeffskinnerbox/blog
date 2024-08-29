<!--
Maintainer:   <jeffskinnerbox@yahoo.com> / <www.jeffskinnerbox.me>
Version:      0.0.0
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>

* [Quantum Computing with Andrea Morello](https://www.youtube.com/watch?v=jDW9bWSepB0&t=0s)
* [Inside a Quantum Computer! with Andrea Morello (Part 1 of 2)](https://www.youtube.com/watch?v=k_QeSOIDiEM)
* [UNSW Quantum Computer Lab Visit - Part 2](https://www.youtube.com/watch?v=yT0Znr0Et4w)

---------------

_"I cannot forecast to you the action of Russia. It is a riddle wrapped in a mystery inside an enigma, but perhaps there is a key. That key is Russian national interest."_
... Sir Winston Churchill in 1939 about what role the Soviet Union might play in World War II

_“The mathematics of quantum physics fits on a postcard. But there are thousands of pages of popular science trying to make that mathematics into a rewarding analogy. That property of quantum mechanics to resist analogy carries through to the computer.”_ ... Peter Shadboldt, PsiQuantum

_"Perhaps the only thing harder than building a quantum computer is explaining how it works."_ ... Adam Bluestein, Fast Company

_"The Talk" by Zach Weinersmith & Scott Aaronson_ - <https://www.smbc-comics.com/comic/the-talk-3>

_"...the gyroscope that I bought when I was eight ... seems mysterious or paradoxical in the context of common experience that excludes gyroscopes ... a paradox may remain if the intuition cannot reach out to connect with it."_
[What is Entanglement? Stretching Your Mind to Understand Quantum Entanglement](https://thequantuminsider.com/2024/08/22/what-is-entanglement-stretching-your-mind-to-understand-quantum-entanglement-a-guest-post-by-carl-kocher/)



* [Quantum Computing Since Democritus, by Scott Aaronson](https://www.amazon.com/dp/0521199565) - DONE
* [Introduction to Classical and Quantum Computing, by Dr Thomas G Wong](https://www.amazon.com/dp/B09QP2ML3P)
* [Quantum in Pictures: A New Way to Understand the Quantum World Paperback, by Bob Coecke, Stefano Gogioso](https://www.amazon.com/dp/1739214714) - IN PROGRESS

* [ZX Quantum-Py: A beginner's guide to Quantum Computing and ZX-Calculus using PyZX, by Mahnoor Fatima, Subhojit Halder, Maria Fernanda, Jyoti Faujdar](https://www.amazon.com/dp/B0B1RD2Z84/)
* [Picturing Quantum Processes: A First Course in Quantum Theory and Diagrammatic Reasoning, by Bob Coecke, Aleks Kissinger](https://www.amazon.com/dp/110710422X)
* [Introduction to the Theory of Computation, by Michael Sipser](https://www.amazon.com/dp/0357670582)

* [The Unexaggerated Magic Of Quantum](https://thequantuminsider.com/?s=The+Unexaggerated+Magic+Of+Quantum)
* [Quantum Computing in ELI5 terms](https://qubitninja.substack.com/p/quantum-computing-eli5)

I found the word to describe what I was looking for in the description of the Tufts University's course [CS 150: Quantum Computer Science](https://www.cs.tufts.edu/comp/150QCS/).
The key sentence: _This is an elementary-level introduction to quantum computing through the computer science lens._
Never the less, if you read the course description and syllabus further,
this course appears to contain much of the material and approach that has disappointed me in the past.

> They say that superposition means “both at once,” so that a quantum bit, or qubit, is just a bit that can be “both 0 and 1 at the same time,” while a classical bit can be only one or the other. They go on to say that a quantum computer would achieve its speed by using qubits to try all possible solutions in superposition — that is, at the same time, or in parallel.
> This is what I’ve come to think of as the fundamental misstep of quantum computing popularization, the one that leads to all the rest.
> What superposition really means is “complex linear combination.” Here, we mean “complex” not in the sense of “complicated” but in the sense of a real plus an imaginary number, while “linear combination” means we add together different multiples of states. So a qubit is a bit that has a complex number called an amplitude attached to the possibility that it’s 0, and a different amplitude attached to the possibility that it’s 1. These amplitudes are closely related to probabilities, in that the further some outcome’s amplitude is from zero, the larger the chance of seeing that outcome; more precisely, the probability equals the distance squared.
> Compounding the difficulty is that, if you want to talk honestly about quantum computing, then you also need the conceptual vocabulary of theoretical computer science. I’m often asked how many times faster a quantum computer will be than today’s computers. A million times? A billion?
> This question misses the point of quantum computers, which is to achieve better “scaling behavior,” or running time as a function of n, the number of bits of input data. This could mean taking a problem where the best classical algorithm needs a number of steps that grows exponentially with n, and solving it using a number of steps that grows only as n2. In such cases, for small n, solving the problem with a quantum computer will actually be slower and more expensive than solving it classically. It’s only as n grows that the quantum speedup first appears and then eventually comes to dominate.
> Note that, after explaining all this, I still haven’t said a word about the practical difficulty of building quantum computers. The problem, in a word, is decoherence, which means unwanted interaction between a quantum computer and its environment — nearby electric fields, warm objects, and other things that can record information about the qubits. This can result in premature “measurement” of the qubits, which collapses them down to classical bits that are either definitely 0 or definitely 1.
> Once someone understands these concepts, I’d say they’re ready to start reading — or possibly even writing — an article on the latest claimed advance in quantum computing. They’ll know which questions to ask in the constant struggle to distinguish reality from hype. Understanding this stuff really is possible — after all, it isn’t rocket science; it’s just quantum computing!
> [Scott Aaronson, What Makes Quantum Computing So Hard to Explain?](https://www.quantamagazine.org/why-is-quantum-computing-so-hard-to-explain-20210608)

Barriers to getting your head around quantum computing:

* Nobel prize winner Alan Aspect on quantum physics “Quantum phenomena do not occur in a Hilbert space, they occur in a laboratory,” meaning it’s not enough to have a mathematical model of quantum mechanics — we also need the physical experiments and a physical interpretation.
* Quantum theory is often regarded as challenging to learn and teach, with advanced mathematical prerequisites ranging from complex numbers and probability theory to matrix multiplication, vector space algebra and symbolic manipulation within the Hilbert space formalism. It is traditionally considered an advanced undergraduate or graduate-level subject.
* What is Hilbert space and why is it such a big deal in quantum physics? - <https://medium.com/predict/hilbert-space-explained-cc33de334979>
* the language & concepts used in quantum physics and how it obscures your understanding
* the mathematics of vector spaces / tensors / Bra–ket notation / probability / complex numbers and how it relates to the physics & computation
* Governments and organisations around the world stress the need to train young people, and make stakeholders aware of and familiar with quantum computing & technologies. ... BUT HOW!
* what does it mean to "compute"
* computational complexity theory
* the concept of randomness and how it can aid in computation
* What are the type of problems suitable for a quantum computer? - The fact that quantum computers can solve any problems that classical computers can, but quantum and classical computers really are a category apart — that even in a world where classical computers succeed beyond all realistic dreams, quantum computers would still stand beyond them. ([Raz and Tal’s paper](https://eccc.weizmann.ac.il/report/2018/107/)). The work of Raz and Tal’s provides an ironclad assurance that quantum computers exist in a different computational realm than classical computers (at least relative to an oracle). Even in a world where P equals NP — one where the traveling salesman problem is as simple as finding a best-fit line on a spreadsheet — Raz and Tal’s proof demonstrates that there would still be problems only quantum computers could solve.
* “Even if P were equal to NP, even making that strong assumption,” said Fortnow, “that’s not going to be enough to capture quantum computing.”


# Quantum Analogies
The reason we like analogies is essentially because we don’t have to do work to build a model in our brain to understand something. A good analogy allows us to map something complex onto models we already did the work to build in our brain. This is great when it works.
But, quantum mechanics just doesn’t map into anything in the normal human experience. It is a new concept that must be built up from zero for each person that learns it.

* [Quantum Analogies](https://www.vlatkovedral.com/quantum-analogies/)
* [Quantum Computing: Some Analogies](https://cronokirby.com/posts/2021/07/quantum_computing_analogies/)
* [Quantum entanglement is tough to dumb down, but this analogy can help detangle it](https://aeon.co/videos/quantum-entanglement-is-tough-to-dumb-down-but-this-analogy-can-help-detangle-it)
* [Understanding Quantum Computing](https://www.microwavejournal.com/articles/34557-understanding-quantum-computing)
* [Quantum entanglement vs classical analogy](https://physics.stackexchange.com/questions/12286/quantum-entanglement-vs-classical-analogy)


# Quantum Mechanics with Real Numbers

* [Quantum mechanics with real numbers: entanglement, superselection rules and gauges](https://arxiv.org/pdf/2308.05473)


# Quantum Hype

* [The Limits of Quantum Computers, by Scott Aaronson](https://www.cs.virginia.edu/~robins/The_Limits_of_Quantum_Computers.pdf)
* [Scott Aaronson | Quantum Computing: Dismantling the Hype | The Cartesian Cafe with Timothy Nguyen](https://youtu.be/qs0D9sdbKPU?si=PoNJvb6b0mhGfECe)
* [The Unexaggerated Magic Of Quantum](https://thequantuminsider.com/?s=The+Unexaggerated+Magic+Of+Quantum)
    * [Guest Post: The Unexaggerated Magic Of Quantum](https://thequantuminsider.com/2024/01/17/guest-post-the-unexaggerated-magic-of-quantum/)
    * [Guest Post: The Unexaggerated Magic Of Quantum – Part II](https://thequantuminsider.com/2024/02/15/guest-post-the-unexaggerated-magic-of-quantum-part-ii/)
    * [Guest Post: The Unexaggerated Magic Of Quantum – Part III](https://thequantuminsider.com/2024/03/13/guest-post-the-unexaggerated-magic-of-quantum-part-iii/)
    * [Guest Post: The Unexaggerated Magic Of Quantum – Part IV](https://thequantuminsider.com/2024/04/24/guest-post-the-unexaggerated-magic-of-quantum-part-iv/)
    * [Guest Post: The Unexaggerated Magic Of Quantum – Part V Special Quantum Artificial Intelligence Edition](https://thequantuminsider.com/2024/05/24/guest-post-the-unexaggerated-magic-of-quantum-part-v-special-quantum-artificial-intelligence-edition/)

* [Quantum Computing in the NISQ era and beyond](https://quantum-journal.org/papers/q-2018-08-06-79/pdf/)


# Origin Stories

Richard Feynman wrote his famous paper titled "Simulating Physics with Computers" concerning the need for quantum computing in May of 1981.
I often wonder why he had an interest in computation.
The web article ["Richard Feynman and The Connection Machine"](https://longnow.org/essays/richard-feynman-and-connection-machine/)
concerning his work at [Thinking Machines Corporation](https://en.wikipedia.org/wiki/Thinking_Machines_Corporation)
on the [Connection Machine](https://en.wikipedia.org/wiki/Connection_Machine) in the 1980's sheds some light on how and why.

While the Connection Machine only [lives in museums today](https://tamikothiel.com/cm/),
its design (both its computation architecture and physical form) has had an interesting impact.
See ["The Design of the Connection Machine"](https://www.tamikothiel.com/theory/cm_txts/index.html)
and ["Dan Bentley on The Connection Machine"](https://www.youtube.com/watch?v=zD-UYbm8Ksg&t=26s).

* Richard Feynman
    * [Simulating Physics with Computers](https://s2.smu.edu/~mitch/class/5395/papers/feynman-quantum-1981.pdf)
    * [Simulating Physics with Computers: Presented by Pinchas Birnbaum and Eran Tromer](https://www.wisdom.weizmann.ac.il/~naor/COURSE/feynman-simulating.pdf)
    * [Quantum Machanical Computers](http://www.quantum-dynamic.eu/doc/feynman85_qmc_optics_letters.pdf)
    * [Richard Feynman: Simulating Physics with Computers](https://www.researchgate.net/publication/254705307_RICHARD_FEYNMAN_SIMULATING_PHYSICS_WITH_COMPUTERS)
    * [A Summary of Feynman's "Simulating Physics with Computers"](<https://chem.libretexts.org/Bookshelves/Physical_and_Theoretical_Chemistry_Textbook_Maps/Quantum_Tutorials_(Rioux)/08%3A_Quantum_Teleportation/8.42%3A_A_Summary_of_Feynman's_Simulating_Physics_with_Computers>)


# Port of Los Angeles Pier 300

* [SavantX: Logistics Optimization at the Port of Los Angeles](https://www.dwavesys.com/media/y3hl22va/dwave_port_of_la_case_story_v7.pdf)
* [Logistics Optimization with Quantum: Port of Los Angeles](https://www.youtube.com/watch?v=jA7iopqDm94)


# Thermodynamic Computing

* [A Vision to Compute like Nature: Thermodynamically](https://cacm.acm.org/opinion/a-vision-to-compute-like-nature/)
* [Extropic](https://www.extropic.ai/future)
    * [Thermodynamic Computing: Better than Quantum? | Guillaume Verdon and Trevor McCourt, Extropic](https://www.youtube.com/watch?v=OwDWOtFNsKQ)
    * [The Next Era of Computing | Extropic](https://www.youtube.com/watch?v=fyVudfvYNKo)
    * [Guillaume Verdon: Why Accelerate](https://www.youtube.com/watch?v=QjVOfM2EBnE)


---------------



# Types of Quantum Computers

* [Top 10: Quantum Computing Companies](https://technologymagazine.com/top10/top-10-quantum-computing-companies)


# Hybrid Quantum Computing
“Hybrid quantum computing” is the preferred industry term for a simple idea: a quantum computer and a classical computer working together to solve a problem.
In a sense, this describes all of quantum computing: we rely on classical computers for almost every aspect of running a quantum computer.
In practice, though, when we talk about “hybrid” computation, we mean an approach that takes the form of a back-and-forth collaboration where different aspects of a problem are passed between the quantum and classical tools best suited for each stage.
For example,  [Variational Quantum Eigensolver (VQE) algorithm](https://towardsdatascience.com/the-variational-quantum-eigensolver-explained-adcbc9659c3a),
a hybrid algorithm useful in a variety of chemistry applications, as an example. VQE can be used to calculate the “ground state”—the most chemically stable configuration—of a molecule by iteratively calculating the energy of a given configuration and comparing it to previously calculated energies classically, changing the inputs until an optimal answer is achieved.

* The Many Faces of Hybrid Classical-Quantum Computing
    * [Part 1: Basics and Cloud Vendors](https://quantumcomputingreport.com/the-many-faces-of-hybrid-classical-quantum-computing/)
    * [Part 2: Colocation, High Performance Computers, and Co-Design](https://quantumcomputingreport.com/the-many-faces-of-hybrid-classical-quantum-computing-part-2/)
    * [Part 3: The primary algorithms VQA, VQE and QAOA](https://quantumcomputingreport.com/the-many-faces-of-hybrid-classical-quantum-computing-part-3/)


# Optical Computing / Photonic Computing

* [What Is Optical Computing | Photonic Computing Explained (Light Speed Computing)](https://www.youtube.com/watch?v=UWMEKex6nYA)
* [How Optical Chips Compute in Femtoseconds](https://www.youtube.com/watch?v=TJ8vywX9asU)


# Linear Optical Quantum Computing
Linear Optical Quantum Computing or linear optics quantum computation (LOQC), also photonic quantum computing (PQC), is a paradigm of quantum computation.


# PsiQuantum

* [PsiQuantum To Build First US-Based Utility-Scale Quantum Computer in Chicago, Illinois](https://www.psiquantum.com/featured-news/illinois-iqmp)
* [PsiQuantum Receives $940 Million (AUD) From Australian Government — May Now Be World’s Highest Funded Independent Quantum Firm](https://thequantuminsider.com/2024/04/29/psiquantum-receives-940-million-aud-from-australian-government/)
* [PsiQuantum Likely Less Than Six Years Away From Commercial Quantum Computer](https://thequantuminsider.com/2024/04/13/psiquantum-likely-less-than-six-years-away-from-commercial-quantum-computer/)
* [This startup is building the country’s most powerful quantum computer on Chicago’s South Side](https://www.fastcompany.com/91162286/psiquantum-quantum-computing-chicago-south-sid)

---------------


# Building a Visceral Understanding of Quantum Phenomena
How does a person develop a viseral understanding of quantum computing?

>Cambridge Dictionary definition: **Visceral** - based on deep feeling and emotional reactions rather than on reason or thought.
>So **Visceral Understanding** is a deep feeling or gut instinct that comes from strong emotions rather than logic or reason.


## Quantum Gamification

* [Making Quantum Games: QJam2024](https://qworld.net/qjam2024/)


### Quantum Tic-Tac-Toe

* [Quantum Tic-Tac-Toe](https://vickynititi.itch.io/quantum-tic-tac-toe)
* [Quantum tic-tac-toe](https://en.wikipedia.org/wiki/Quantum_tic-tac-toe)
* [Quantum Tic Tac Toe](https://quantum-ttt.herokuapp.com/)
* [Quantum Tic Tac Toe](https://dbroemme.itch.io/quantum-tic-tac-toe)

* [Quantum tic-tac-toe: A teaching metaphor for superposition in quantum mechanics](https://pubs.aip.org/aapt/ajp/article-abstract/74/11/962/864424/Quantum-tic-tac-toe-A-teaching-metaphor-for?redirectedFrom=fulltex)
* [Quantum tic-tac-toe: A teaching metaphor for superposition in quantum mechanics](hhttps://perruchenautomne.eu/wordpress/wp-content/uploads/2015/05/QT3-AJP-10-20-06.pdf)
* [Quantum Tic‐Tac‐Toe: A Game of Entanglement](https://mathwithbaddrawings.com/wp-content/uploads/2020/10/Game-19-Quantum-Tic-Tac-Toe.pdf)
* [Introducing a new game: Quantum TiqTaqToe](https://quantumfrontiers.com/2019/07/15/tiqtaqtoe/)
* [Quantum Tic Tac Toe](https://physlab.org/wp-content/uploads/2023/05/QuantumTicTacToe_23100002_Fin.pdf)
* [Quantum Tic-Tac-Toe: the best game you’ve never played, or have you?](https://darren-broemmer.medium.com/quantum-tic-tac-toe-the-best-game-youve-never-played-or-have-you-d689cd110b64)

 formulate a quantum strategy which allows a quantum player to consistently win over a classical player, with a certain probability. This result can be seen as another proof of the superior computational power of a quantum system with respect to a classical one.

* [Quantum Tic-Tac-Toe: A Genuine Probabilistic Approach](https://academic.timwylie.com/17CSCI4341/quantum_tictactoe.pdf)
* [Quantum Tic Tac Toe Reinforcement Learning](https://www.youtube.com/watch?v=WXiUDKCsXa0)


### Coin Flip Game

* [A beginner's guide to quantum computing | Shohini Ghose](https://www.youtube.com/watch?v=QuR969uMICM)
    * [A beginner's guide to quantum computing | Shohini Ghose | Summary and Q&A](https://glasp.co/youtube/QuR969uMICM)
* [Quantum Computing With an Example of Coin](https://www.youtube.com/watch?v=Rjx_11oHYT4)
* [QEF06 - The Penny Flip Game](https://www.youtube.com/watch?v=oXdlpj2IrRU)
    * [How can quantum computing win 97% of times in coin flipping experiment?](https://quantumcomputing.stackexchange.com/questions/5273/how-can-quantum-computing-win-97-of-times-in-coin-flipping-experiment/5277#5277)
    * [Hello Quantum: Taking your first steps into quantum computation](https://medium.com/qiskit/hello-quantum-2c1c00fe830c)
    * [Quantum Coding Tutorial | How To Win a Quantum Coin Flip](https://www.youtube.com/watch?v=9nHNHgGGivM)
    * [Playing with a Quantum Computer](https://arxiv.org/pdf/2108.06271)
    * [Quantum Coin Toss](https://www.maplesoft.com/applications/download.aspx?id=154938/Quantum_Coin_Toss.pdf)
    * [QEF06 - The Penny Flip Game](https://www.youtube.com/watch?v=oXdlpj2IrRU)
    * [I created a quantum mini-game!](https://medium.com/@PhilNadeau/i-created-a-quantum-mini-game-fc4299a75758)
    * [Qiskit for Beginners: Create and Play A game of Quantum Coin Flip](https://medium.com/@v.tiwari/qiskit-for-beginners-create-and-play-a-game-of-quantum-coin-flip-ebcc4fb75711)


### Quantum Economics and Finance

* [Quantum Economics and Finance](https://www.youtube.com/playlist?list=PLXQuDqjDYq23fUB_zyX6-wJYVeHlfreyM)


### Card Game: Find the Ace

* [Quantum computing explained with a deck of cards | Dario Gil, IBM Research](https://www.youtube.com/watch?v=yy6TV9Dntlw)


### Quantum Mechanics Toys / Pauli Cubes

* [For Some Reason, These Quantum Mechanics Toys Didn’t Catch On](https://spectrum.ieee.org/for-some-reason-these-quantum-mechanics-toys-didnt-catch-on)
    * [Playing with Quantum Toys: Julian Schwinger’s Measurement Algebra and the Material Culture of Quantum Mechanics Pedagogy at Harvard in the 1960s](https://link.springer.com/epdf/10.1007/s00016-018-0213-3?sharing_token=gXaCU8sTKZDz9CD74pHysve4RwlQNchNByi7wbcMAY6Qp8JObREiurDKlz9hr9xVlcI2yDj0ksf3Q2AQ4u_5cE3RbNMLJ_VW55jnhIIAUcXmDue2Id6rteXlgC8XR3pvN5K6jYRUbaMvjoQhkNb4heBvWeO1o3ArIWPDJfGmgGI%3D)
    * [PLAYING WITH QUANTUM TOYS: Introducing the history of quantum mechanics with historical objects](https://agenda.centrofermi.it/event/17/contributions/47/attachments/29/30/Jean-Francois_Gauvin_-_Playing_Quantum_Toys_Rome_1.pdf)
    * [Playing with Science History – Jean-François Gauvin](https://www.parsingscience.org/2018/10/30/jean-francois-gauvin/)

The Pauli Cubes appear to be working with the same principles that this "Homemade Quantum Computer" is using.
All you'll need is:

* a weak red laser pointer (the type in cat toys are generally safe)
* polarizing film or polarizing filter. If you have polaroid glasses or certain camera ND filters you may already have this. Otherwise it's available on amazon
* half waveplate (the plastic thing) is this one: <https://www.edmundoptics.co.uk/f/poly>... (λ/2 Retarder Film (WP280))
* You don't need calcite, but if you want to play with it, you can find it on etsy usually. Look for a sample that's exceptionally clear

* [I made a (useless) quantum computer at home](https://www.youtube.com/watch?v=muoIG732fQA)
* [What can my homemade quantum computer do?](https://www.youtube.com/watch?v=tHfGucHtLqo)


### Qbit Factory

* [Qbit Factory](https://www.qubitfactory.io/)
* [GitHub: awslabs/the-qubit-factory](https://github.com/awslabs/the-qubit-factory/wiki)
* [Building a Visceral Understanding of Quantum Phenomena](https://quantumfrontiers.com/)
* [Exploring Gamification in Quantum Computing: The Qubit Factory](https://arxiv.org/pdf/2406.11995)


### Quirk

* [How to use Quirk - Toy Quantum Circuit Simulator](https://www.youtube.com/watch?v=aloFwlBUwsQ)
* [Welcome to Quirk](https://algassert.com/quirk)

* [Quantum Searching in Your Browser](https://hackaday.com/2018/02/07/quantum-searching-in-your-browser/)
* [Quantum Weirdness in Your Browser](https://hackaday.com/2018/01/24/quantum-weirdness-in-your-browser/)
* [Craig Gidney's quantum circuit simulator: Quirk](http://algassert.com/quirk)
* [How to use Quirk - Toy Quantum Circuit Simulator](https://www.youtube.com/watch?v=aloFwlBUwsQ)
* [Quantum Computers Animated](https://www.youtube.com/watch?v=T2DXrs0OpHU)
* [Quantum Computers Explained – Limits of Human Technology](https://www.youtube.com/watch?v=JhHMJCUmq28)
* [The Mathematics of Quantum Computers](https://www.youtube.com/watch?v=IrbJYsep45E)
* [Building the Bits and Qubits](https://www.youtube.com/watch?v=F8U1d2Hqark)
* [You don't know how Quantum Computers work](https://www.youtube.com/watch?v=ZoT82NDpcvQ)
* [Quantum computing for the determined](https://www.youtube.com/watch?v=X2q1PuI2RFI&list=PL1826E60FD05B44E4)


#### The Qbit Game

* [The Qbit Game](https://quantumai.google/education/thequbitgame)
* [The Qubit Game by Google](https://q12education.org/wp-content/uploads/2024/04/Google-Qubit-Game-Activity-Guide.pdf)


---------------


## Quantum Computing Pedagogy

Pedagogy is the method and practice of teaching, especially as an academic subject or theoretical concept.
As education researchers gain a broader understanding of how students learn quantum mechanics, new pedagogical and technical resources are being developed to facilitate student learning.


### ScienceAtHome Quantum Tools

* [ScienceAtHome Quantum Tools](https://www.scienceathome.org/quantum/tools/)


### QEngine

QEngine is our software library for quantum simulation and - optimization.

* [QEngine](https://www.quatomic.com/)


### Learning Quantum Computing Concepts

* Quantum Computing Concepts
    * [Quantum Computing Course – Math and Theory for Beginners](https://www.youtube.com/watch?v=tsbCSkvHhMo)
    * [IBM Quantum Learning](https://learning.quantum.ibm.com/)
    * [Black Opal](https://black.q-ctrl.com/)
* Quantum Algorithms Development
    * [IBM Quantum Documentation](https://docs.quantum.ibm.com/)
    * [Penny Lane](https://pennylane.ai/qml/)


---------------


# Preparatory Mathematics and Quantum Mechanics for Quantum Computing

* Mathematics (Linear Algebra, Tensors, Probability)
    * [An Introduction to Differential Geometry](https://www.youtube.com/playlist?list=PLlXfTHzgMRUKG7lkye7DQAmNB0cfWNgWG)
    * [Essence of linear algebra](https://www.youtube.com/watch?v=fNk_zzaMoSs&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab&index=2)
    * [Matrix Algebra for Engineers](https://www.youtube.com/playlist?list=PLkZjai-2Jcxlg-Z1roB0pUwFU-P58tvOx)
    * [Linear algebra for Quantum Mechanics](https://www.youtube.com/watch?v=FF05fXg03A0)
    * [Preliminary Mathematics for Quantum Computing](https://www.cs.tufts.edu/comp/150QCS/Premath.pdf)
    * [The Geometric Tool That Solved Einstein’s Relativity Problem](https://www.quantamagazine.org/the-geometric-tool-that-solved-einsteins-relativity-problem-20240812/)
    * [Why are tensors EVERYWHERE? | Tensors for beginners](https://www.youtube.com/watch?v=AJSHZkVnbXc)
    * [An Introduction to Tensor Calculus](https://grinfeld.org/books/An-Introduction-To-Tensor-Calculus/)
        * [Introduction to Tensor Calculus](https://www.youtube.com/playlist?list=PLlXfTHzgMRULkodlIEqfgTS-H1AY_bNtq)
    * [Tensor Calculus](https://www.youtube.com/playlist?list=PLdgVBOaXkb9D6zw47gsrtE5XqLeRPh27_)
    * [Tensors and Vectors - 2023](https://www.youtube.com/playlist?list=PL2n-gxsZ_8LBC0zhYvDjPF8eF8PvygM2T)
* Concept and Theories in Physical Science
    * [Harvard Project Physics](https://archive.org/details/projectphysicscollection)
* Quantum Physics
    * DONE - [MIT STS.042J Einstein, Oppenheimer, Feynman: Physics in the 20th Century](https://www.youtube.com/playlist?list=PLUl4u3cNGP63bAfjGas3TuA4ZCPUtN6Xf)
    * [Quantum Physics](https://www.youtube.com/watch?v=qtIsYbYdzCI&list=PLjH5ujQJt_IeW2qFkDRIBrZpIgx4ZX4AR)
* Quantum Mechanics
    * [The Maths of Quantum Mechanics in 13 Minutes | Functional Operators and Fourier Transforms](https://www.youtube.com/watch?v=thRKIYr9LwQ&list=PL748m8SU9Q0cwbh4YDrZCgcNTXVZHwRBc&index=5)
    * [The math trick that revolutionized physics](https://www.youtube.com/watch?v=gXeAp_lyj9s) - DONE
    * [Fundamentals of Quantum Physics - Brant Carlson](https://www.youtube.com/playlist?list=PLNZRbvSM6olzbOKl-JtNSZdLiroAhhpE7) - IN PROGRESS
    * [Maths of Quantum Mechanics](https://www.youtube.com/playlist?list=PL8ER5-vAoiHAWm1UcZsiauUGPlJChgNXC)
    * [Quantum mechanics essentials: Everything you need for quantum computation](https://www.youtube.com/watch?v=28ABEInFxBQ)
    * [Understanding Quantum Mechanics](https://www.youtube.com/watch?v=Wsjgtp9XZxo&list=PLwgQsqtH9H5djIfFhXE6We207beTgUnyL)
    * [Quantum Physics Full Course | Quantum Mechanics Course](https://www.youtube.com/watch?v=hyctIDPRSqY)
* Computer Science
    * [Undergrad Complexity at CMU](https://www.youtube.com/playlist?list=PLm3J0oaFux3YL5vLXpzOyJiLtqLp6dCW2)
    * [Great Ideas in Theoretical Computer Science at CMU](https://www.youtube.com/playlist?list=PLm3J0oaFux3aafQm568blS9blxtA_EWQv)
    * [CS Theory Toolkit at CMU](https://www.youtube.com/playlist?list=PLm3J0oaFux3ZYpFLwwrlv_EHH9wtH6pnX)
* Understanding Quantum Computing
    * [Quantum Computing Book Recommendations](https://www.youtube.com/watch?v=xpSevVullcQ)
    * [Quantum Book Recommendations Part 2!](https://www.youtube.com/watch?v=rbcNQB7VMtI)
    * [How To Make a Quantum Bit](https://www.youtube.com/watch?v=zNzzGgr2mhk)


# Skepticism

* [Quantum Computing’s Hard, Cold Reality Check](https://spectrum.ieee.org/quantum-computing-skeptics)


# What is Computation?

What is computation? - The rigorous study of manipulation of information / data.
What is Computer Science? - Computer Science is the science of computation.
What do computes do? - Perform computation, by using knowledge, under your direction. These directions are algorithms.
Types of knowledge? - Declarative Knowledge which are statement of facts. Imperative Knowledge which is a recipe or "sequence of steps" or "how-to".
What is a recipe? - An algorithm. This is a (1) sequence of simple steps, (2) flow of control that specifies when each step is executed, (3) a means of determining when to stop.

* [What is Computation?](https://www.youtube.com/results?search_query=What+is+Computation%3F) - start at 7 minutes
* [Was There Life Before Computers?](https://www.nicolamarras.it/Was-There-Life-Before-Computer-en.pdf)
* [Mechanical circuits: electronics without electricity](https://www.youtube.com/watch?v=QrkiJZKJfpY)
* [Analog vs Digital vs Quantum, Explained - Learn Science of Data, Waves, Bits, Qubits and more!](https://www.youtube.com/watch?v=ZMkLPvOVkNo)


# What is Computational Complexity?

* [A Short Guide to Hard Problems](https://www.quantamagazine.org/a-short-guide-to-hard-problems-20180716/)
* [Finally, a Problem That Only Quantum Computers Will Ever Be Able to Solve](https://www.quantamagazine.org/finally-a-problem-that-only-quantum-computers-will-ever-be-able-to-solve-20180621/)


# Examples of Computing Machines

* [The Babbage Engine](https://www.computerhistory.org/babbage/)
* [Digi-Comp I](https://mindsontoys.com/kits.htm?dc1_main.htm)
* [Lego Mechanical Computer](https://www.drmoron.org/posts/mechanical-computer/)
* [Mechanical Implementation of a Turing Machine](http://rubens.ens-lyon.fr/)
* [Lord Kelvin and His Analog Computer](https://spectrum.ieee.org/tide-predictions)
* [Manchester Differerential Analyser](https://en.wikipedia.org/wiki/Differential_analyser)
    * [Are Thinking Machines Possible?](https://medium.com/thought-thinkers/are-thinking-machines-possible-ea8e2e0f9dc1)
    * [Machine Solves Mathematical Problems](https://meccano.us/documents/anon_1934b.pdf)


# What is Neuromorphic Computing?

* [The AI Hardware Problem](https://www.youtube.com/watch?v=owe9cPEdm7k)
* [Neuromorphic Computing-How The Brain-Inspired Technology | Neuromorphic Artificial Intelligence |](https://www.youtube.com/watch?v=u9pulFlavIM)


## What is Spike Neuromorphic Computing?

Spiking Neural Networks are neural networks that replicate the neuronal-firing mechanisms of the brain and thus possess many capabilities of the brain e.g. energy efficiency and Spatio-temporal data processing.

* [Mike Davies: Realizing the Promise of Spiking Neuromorphic Hardware](https://www.youtube.com/watch?v=jhQgElvtb1s)


## Computable and Not-Computable

* [The Boundary of Computation](https://www.youtube.com/watch?v=kmAc1nDizu0)
    * [The Most Difficult Program to Compute? - Computerphile](https://www.youtube.com/watch?v=i7sm9dzFtEI)
    * [Busy Beaver Turing Machines - Computerphile](https://www.youtube.com/watch?v=CE8UhcyJS0I)
    * [With Fifth Busy Beaver, Researchers Approach Computation’s Limits](https://www.quantamagazine.org/amateur-mathematicians-find-fifth-busy-beaver-turing-machine-20240702/)
        * [The Busy Beaver Challenge](https://bbchallenge.org/)


# What is Quantum Computation?

* [The Quantum Computing Advantage](https://www.youtube.com/watch?v=PXQ-sh07eBw)
* [Scott Aaronson on Computational Complexity Theory and Quantum Computers](https://www.youtube.com/watch?v=0jrybODBUpA)
* Using Scratch: [Scratch Quantum Computer](https://scratch.mit.edu/projects/875118011/editor/)
    * [This ONE Instruction Instantly Makes Scratch Into A Quantum Computer!!](https://www.youtube.com/watch?v=zw6C_UTDZEY)
    * [The Math Behind Quantum Algorithms (in Scratch!)](https://www.youtube.com/watch?v=VuWklQM_3q8)


## Control Flow in Quantum Programming

* [A blueprint for making quantum computers easier to program](https://news.mit.edu/2024/mit-researchers-propose-blueprint-how-make-quantum-computers-easier-program-0416)
    * [Quantum Control Machine: The Limits of Control Flow in Quantum Programming](https://arxiv.org/pdf/2304.15000.pdf)


# What is Quantum Advantage?

* [Scientists figure out how to surpass ‘quantum advantage’ with binary computers](https://cointelegraph.com/news/scientists-surpass-quantum-advantage-binary-computers)
* [Quantum Advantage in Learning from Experiments](https://blog.research.google/2022/06/quantum-advantage-in-learning-from.html)


# Is Quantum Computing Really Probabilistic Computing?

In a quantum computation, we are not controlling probabilities but amplitudes, which can be positive, negative, or even imaginary. This makes it possible to extract the solution by canceling out the amplitudes of the other bit vectors. This phenomenon is called interference.

* [What is Probabilistic Computing, and how does it work?](https://medium.com/digital-architecture-lab/what-is-probabilistic-computing-and-how-does-it-work-1efea7d780c9)
* [Probability vs quantum computing](https://www.linkedin.com/pulse/probability-vs-quantum-computing-david-radcliffe/)


# Learning to Live With Quantum Weirdness

* [Understanding Quantum Mechanics](https://www.youtube.com/watch?v=Wsjgtp9XZxo&list=PLwgQsqtH9H5djIfFhXE6We207beTgUnyL)


# Quantum Mechanics & Chaos

* [Quantum computing in the 21st Century – with David Jamieson](https://www.youtube.com/watch?v=zxml8UQSwC0)
* [Chaos: The real problem with quantum mechanics](https://www.youtube.com/watch?v=LJzKLTavk-w&t=10s)
* [Chaos and the semiclassical limit of quantum mechanics (is the moon there when somebody looks?)](https://michaelberryphysics.files.wordpress.com/2013/07/berry337.pdf)
* [Quantum Hyperion](https://www.preposterousuniverse.com/blog/2008/10/23/quantum-hyperion/)
* [Quantum Chaos](https://www.scientificamerican.com/article/quantum-chaos-subatomic-worlds/)

* [Fluid dynamics feels natural once you start with quantum mechanics](https://www.youtube.com/playlist?list=PLMoTR49uj6ld32zLVWmcGXaW7w2ey7Vh4)


# When Will Quantum Computing Be Useful

* [Quantum computing: What leaders need to know now](https://mitsloan.mit.edu/ideas-made-to-matter/quantum-computing-what-leaders-need-to-know-now)
    * [The Quantum Tortoise and the Classical Hare: A simple framework for understanding which problems quantum computing will accelerate (and which it won’t)](https://arxiv.org/pdf/2310.15505.pdf)
* [Google launches $5m prize to find actual uses for quantum computers](https://www.newscientist.com/article/2420137-google-launches-5m-prize-to-find-actual-uses-for-quantum-computers/)

* [Physicists Finally Find a Problem That Only Quantum Computers Can Do](https://www.quantamagazine.org/physicists-finally-find-a-problem-only-quantum-computers-can-do-20240312/)

---------------


# Quantum Computing

* [Quantum Computing for Beginners](https://dev.to/taradev/series/23332)
* [A Beginner's Guide to Starting Your Journey in Quantum Computing](https://dev.to/taradev/a-beginners-guide-to-starting-your-journey-in-quantum-computing-300o)
* [Open source as a path to learning Quantum Computing](https://dev.to/taradev/open-source-as-a-path-to-learning-quantum-computing-4dkb)
* [Universal Quantum Computer](https://www.youtube.com/watch?v=z5-XI__LfT8&t=107s)
* [Quantum Computing for Computer Scientists](https://www.youtube.com/watch?v=F_Riqjdh2oM&list=PLD7HFcN7LXRcKEiyRxdTDVRaMZQDhojhb)
* [Quantum Computing](https://www.youtube.com/playlist?list=PLxP0p--aBHmIe--9rczWe4AZmw03e2bz0)

* [Learning About Quantum States](https://www.youtube.com/playlist?list=PLm3J0oaFux3biM7DgkmjSWAikhgQm6xbv)
* [Quantum Computation and Information at CMU](https://www.youtube.com/playlist?list=PLm3J0oaFux3YL5qLskC6xQ24JpMwOAeJz)


# How Does a Quantum Computer Work?

* [How Does a Quantum Computer Work?](https://www.youtube.com/watch?v=g_IaVepNDT4)
* [How To Make a Quantum Bit](https://www.youtube.com/watch?v=zNzzGgr2mhk)

* [Introduction to Grover’s Algorithm](https://www.geeksforgeeks.org/introduction-to-grovers-algorithm/)
* [Grover's Algorithm](https://en.wikipedia.org/wiki/Grover%27s_algorithm)
* [Grover's Algorithm | Understanding Quantum Information & Computation: Lesson 08](https://www.youtube.com/watch?v=hnpjC8WQVrQ&t=73s)
* [A Visual Introduction to Grover's Algorithm and Reflections](https://www.youtube.com/watch?v=c30KrWjHaw4)

* [The Quantum Computing Speed Boost Is NOT What You Think](https://www.youtube.com/watch?v=KdK391DqONc)
* [Quantum Computers: How They Work and What Can They Do?](https://www.youtube.com/watch?v=6eJVVCO6GRM)
* [You don't know how Quantum Computers work!](https://www.youtube.com/watch?v=ZoT82NDpcvQ)
* [Bits, Gates, and Matrices | Quantum Computing Part 1](https://www.youtube.com/watch?v=5z-Fesb7b40)
* [Quantum Computing](https://www.youtube.com/playlist?list=PLV4qsET9ZdOR-pf6ZMJZx2auIZScXhCaW)
* [How does a COMPUTER CPU actually WORK?](https://www.youtube.com/watch?v=EsDyGfh8bnM)
* [The Insane Mechanism of a Quantum Computer?](https://www.youtube.com/watch?v=RCj_BJ6BddM)
* [Single qubit and its logic gates](https://www.youtube.com/watch?v=rD_fH7O-D5Y)
* [The Quantum Computing Speed Boost Is NOT What You Think](https://www.youtube.com/watch?v=KdK391DqONc)
* [The Mathematics of Quantum Computers](https://www.youtube.com/watch?v=IrbJYsep45E)
* [Building the Bits and Qubits](https://www.youtube.com/watch?v=F8U1d2Hqark)


# How or What is a Quantum Computer Computing?

Does this tell us enough about the distinction between the classical & quantum computing?

| Classical Computing                                                 | Quantum Computing                                                               |
| :------------------------------------------------------------------ | :------------------------------------------------------------------------------ |
| discrete number of states (zero & one), calcuations with binary bit | infinite, continuious range of states (complex vectors), calculation with qbits |
| power increase 1-to-1 rleative to number of transistors             | power increases expodentially relative to number of qbits                       |
| high error rates and must operate at ultra-low tempatures           | low error rates and operate at room tempature                                   |
| well suited for most everyday computational needs                   | best suited for optiomization problems, simulations, and data analysis          |
| calculations are deterministic (same input creates the same result) | calculations are probalistic (same input creates multiple outputs)              |
| operations are define by boolien algrabra                           | operatons are defined by linear algrabra over Hilbert Space                     |
| circuits are defined by classical physics                           | circuits are defined by quantum physics                                         |

* [Quantum Computing vs. Classical Computing: Which One Should You Use?](https://levelup.gitconnected.com/quantum-computing-vs-classical-computing-which-one-should-you-use-efab33a09c2f)
* [Quantum and Classical Computing: Key Differences to Understand](https://www.quantumcomputinginc.com/blog/quantum-and-classical-key-differences/)
* [Conventional Computing vs Quantum Computing](https://www.geeksforgeeks.org/conventional-computing-vs-quantum-computing/)

| Super Computing                                                                                                                                   | Quantum Computing                                                                                                                      |
| :------------------------------------------------------------------------------------------------------------------------------------------------ | :------------------------------------------------------------------------------------------------------------------------------------- |
| Supercomputing is defined as the processing of highly complex problems using the very large and concentrated compute resources of supercomputer   | Quantum computing is defined as the use of quantum-mechanical phenomena such as superposition and entanglement to perform computation. |
| Supercomputers are used for supercomputing.                                                                                                       | While quantum computer are used for Quantum computing.                                                                                 |
| It enables problem solving and data analysis more easily and simply.                                                                              | It performs calculations based on the probability                                                                                      |
| They plays a significant role in providing national security and knowledge in scientific discovery.                                               | While, quantum computers is still a work in progress.                                                                                  |
| Supercomputer is a system that operates at a high compute to I/O ratio and delivers a very large number of effective computing cycles per second. | Quantum computer is a computer aimed at utilizing new quantum algorithms to accelerate digital computation.                            |
| Common applications of supercomputing are simulation and modeling of physical phenomena such as climate change, explosions, etc.                  | There is no real world applications of Quantum computing.                                                                              |
| It is something that connects people, organizations, products and technologies.                                                                   | Whereas, these are about changing the notion of computation itself.                                                                    |


# Probabilistic Computing

Probabilistic computing is a field of computer science and artificial intelligence that focuses on the study and implementation of probabilistic algorithms, models, and methods for computation. It aims to build systems that can reason about and handle uncertainty, making probabilistic predictions about the world and making decisions based on those predictions.

* Probabilistic computing is motivated by the fact that real-world problems often involve uncertain and incomplete information. In these cases, it is often more appropriate to represent knowledge as probabilities rather than definite truths. By using probabilistic models, computers can learn from data, make predictions, and solve problems in uncertain environments.
* Some of the key concepts in probabilistic computing include Bayesian networks, Markov models, Monte Carlo methods, and probabilistic programming languages. These tools and techniques allow computers to perform tasks such as uncertainty quantification, probabilistic inference, and decision-making under uncertainty.
* Probabilistic computing has a wide range of applications, including machine learning, robotics, computer vision, natural language processing, and cognitive computing. In recent years, the field has seen significant advances, driven by the increasing availability of large amounts of data and the development of powerful computational tools.


---------------


# Learning Quantum Physics & Quantum Computing

* [How Randomness Improves Algorithms](https://www.quantamagazine.org/how-randomness-improves-algorithms-20230403/)
* [Waiting for Quantum Computing? Try Probabilistic Computing](https://spectrum.ieee.org/computing/hardware/waiting-for-quantum-computing-try-probabilistic-computing)
* [MIT Probabilistic Computing Project](http://probcomp.csail.mit.edu/)
* [WHAT IS PROBABILISTIC COMPUTING?](https://www.lonja.de/what-is-probabilistic-computing/)
* [Probabilistic Computation](https://betanalpha.github.io/assets/case_studies/probabilistic_computation.html)

* [Richard Feynman paper on “Simulating Physics with Computers”](http://physics.whu.edu.cn/dfiles/wenjian/1_00_QIC_Feynman.pdf)

* [Hello Many Worlds in Seven Quantum Languages](https://ionq.com/posts/june-24-2021-hello-many-worlds)

* [A Primer On Quantum Computing For Investors](https://seekingalpha.com/article/4469128-hon-ibm-ionq-sniia-primer-on-quantum-computing-for-investors)
* [Quantum Computing for Computer Scientists](https://www.youtube.com/watch?v=F_Riqjdh2oM)
* [HackadayU: Quantum Computing - Qubits, Superposition Class 1.1](https://www.youtube.com/watch?v=XPjYORvisxc&list=PL_tws4AXg7avHFquKAB6q6cep2pnueLpM&t=3s)

* [Quantum Computing: How it Works](https://www.youtube.com/watch?v=nrp89bkwQ4o)
* [Quantum Computers, Explained With Quantum Physics](https://www.youtube.com/watch?v=jHoEjvuPoB8)
* [Quantum Mechanics Isn’t Weird, We’re Just Too Big](https://www.youtube.com/watch?v=q1O11kP6x1k)
* [What's the Real Meaning of Quantum Mechanics?](https://www.youtube.com/watch?v=LqY3TUW7skI&t=133s)

* [The Three Pillars of Quantum Computing](https://medium.com/digital-diplomacy/the-three-pillars-of-quantum-computing-d80ff5f50ec7)
* [The Ultimate Beginner’s Guide to Quantum Computing and its Applications](https://towardsdatascience.com/the-ultimate-beginners-guide-to-quantum-computing-and-its-applications-5b43c8fbcd8f)
* [Quantum computing for the very curious](https://quantum.country/qcvc)
* [Quantum Computing as a High School Module](https://arxiv.org/pdf/1905.00282.pdf)

* [how to teach yourself physics](https://www.youtube.com/watch?v=Cw97Tj5zxvA)
* [How to learn Quantum Mechanics on your own (a self-study guide)](https://www.youtube.com/watch?v=Rs572Cf4zkk&feature=youtu.be)
* [Quantum Computing: Untangling the Hype](https://www.youtube.com/watch?v=wE1OCXvaDtc)

* [Google Sees Long, Expensive Road Ahead For Quantum Computing](http://www.theplatform.net/2015/07/22/google-sees-long-expensive-road-ahead-for-quantum-computing/)
* [The Golden Age Of Quantum Computing Is Upon Us (Once We Solve These Tiny Problems)](http://www.fastcompany.com/3045708/big-tiny-problems-for-quantum-computing)
* [Quantum Computing And The End Of Encryption](https://hackaday.com/2020/06/11/quantum-computing-and-the-end-of-encryption/)

* [Preparing students to be leaders of the quantum information revolution](https://physicstoday.scitation.org/do/10.1063/PT.6.5.20210927a/full/)

* [From ‘chandeliers’ to entangled qubits, here’s what happens inside a quantum computer](https://aeon.co/videos/from-chandeliers-to-entangled-qubits-heres-what-happens-inside-a-quantum-computer)

* [University of Maryland: Quantum Atlas](https://quantumatlas.umd.edu/)
* [Build your own quantum computer with Google's latest 'simulator'](https://www.engadget.com/build-your-own-quantum-computer-with-googles-latest-simulator-124513737.html)
* [Quantum computing cheat sheet for circuit designers](https://www.eenewseurope.com/en/quantum-computing-cheat-sheet-for-circuit-designers/)
* [Quantum Computing](https://www.youtube.com/playlist?list=PLzH6n4zXucko55y-YFE4ng1CLiui_3DUr)


# IBM Quantum Developer Certification

Seems like it is no longer offered

* [Learn More About the IBM Quantum Developer Certification — And How to Take it For Free](https://medium.com/qiskit/learn-more-about-the-ibm-quantum-developer-certification-and-how-to-take-it-for-free-d237f9765dc5)

* [Quantum Computing for Dummies: New guide helps beginners run quantum algorithms on IBM’s quantum computers over the cloud](https://spectrum.ieee.org/quantum-computing-for-dummies)
    * [Quantum Algorithm Implementations for Beginners](https://dl.acm.org/doi/10.1145/3517340)
    * [GitHub: lanl/quantum_algorithms](https://github.com/lanl/quantum_algorithms)
    * [Quantum Glasses](https://github.com/Jayshah25/Quantum-Glasses) package is a GUI app designed to help users visualize the effects of single-qubit quantum gates via interactive [Bloch Sphere](https://learn.qiskit.org/course/ch-states/representing-qubit-states#bloch-sphere) simulations.
    * [Quantum Glasses (Member of IBM Qiskit Ecosystem) | Quantum Computing explained](https://www.youtube.com/watch?v=wCrdbL5taj0)
    * [Quantum Computing Tutorials (Visual) for Beginners](https://www.youtube.com/playlist?list=PLJk_IGUjQllfCDHYmFNfaCoUgXImxmZIA)


# History of Quantum Computing

* [The History of Quantum Computing](https://www.youtube.com/playlist?list=PLOFEBzvs-VvpNNq221OCZzCZjHadM2NHR)


# Some Potential Useful Quantum Algorithm

* [Introducing Quantum Algorithms with Konstantin Lakic](https://www.youtube.com/playlist?list=PLl0eQOWl7mnUTNF7KlDJVI3PUgyaXQUHS)

Quantum Fourier Transform - central to many quantum algorithms
Shor’s Algorithm - factoring large numbers
Grover’s Algorithm - find a specific item in a database of N items in roughly sqrt(N) operations, classical algorithms require N operations
Harrow-Hassidim-Lloyd (HHL) Algorithm - solving linear equations


## Shor’s Algorithm

* [Thirty Years Later, a Speed Boost for Quantum Factoring](https://www.quantamagazine.org/thirty-years-later-a-speed-boost-for-quantum-factoring-20231017)
* [How Quantum Computers Will Correct Their Errors](https://www.quantamagazine.org/how-quantum-computers-will-correct-their-errors-20211116)
* [New Codes Could Make Quantum Computing 10 Times More Efficient](https://www.quantamagazine.org/new-codes-could-make-quantum-computing-10-times-more-efficient-20230825/)


# Scott Aaronson's Course "Quantum Computing Since Democritus"

* [PHYS771 Quantum Computing Since Democritus](https://www.scottaaronson.com/democritus/default.html)
* [Quantum Computing since Democritus](https://www.amazon.com/Quantum-Computing-since-Democritus-ebook/dp/B00B4V6IZK/)
* [What Makes Quantum Computing So Hard to Explain?](https://www.quantamagazine.org/why-is-quantum-computing-so-hard-to-explain-20210608)
* [Ricoh Printers: Intelligent Model](https://www.youtube.com/watch?v=saWCyZupO4U)


# Quantumpedia

Quantumpedia is a comprehensive online encyclopedia on quantum computing, founded by Louis Chen, an IBM Q Researcher and PhD candidate at Imperial College.

* [Quantumpedia](https://quantumpedia.uk/lists)


# Quantum Computing Origins

* [A Brief History of Quantum Computing](https://quantumpedia.uk/a-brief-history-of-quantum-computing-e0bbd05893d0)
* [Feynman’s Three Papers Related to Quantum Computing](https://jackkrupansky.medium.com/feynmans-three-papers-related-to-quantum-computing-dd6f9847e6ad)


# Why Quantum Computing?

As physicist Charlie Bennett describes the [relationship between quantum and classical computers](https://www.youtube.com/watch?v=rslt-LwtDK4)

> A classical computer is a quantum computer ... so we shouldn't be asking about "where do quantum speedups come from?"
> We should say, "well, all computers are quantum. ... Where do classical slowdowns come from?"

* [Unconventional Computing](https://www.youtube.com/watch?v=szTtg302Hic&list=PLC7a8fNahjQ8IkiD5f7blIYrro9oeIfJU&index=9)
* [Quantum Programming - Part 1](https://www.youtube.com/watch?v=2Eswqed8agg)
* [Quantum Parallelism: When to use a quantum computer](https://pyqml.medium.com/quantum-parallelism-fe1c58db53bd)
* [The Unvarnished Truth About What Quantum Computing Really Is](https://pyqml.medium.com/the-unvarnished-truth-about-what-quantum-computing-really-is-526e517df5a2)
* [Quantum Instruction Set - Computerphile](https://www.youtube.com/watch?v=ZN0lhYU1f5Q)
* [Current State of Quantum Computing - Computerphile](https://www.youtube.com/watch?v=PN7mPYcWFKg)


# Why are Quantum Computing so Fast?

Is this why or is it bull shit?

* [](https://medium.com/@hasnainistz/quantum-computing-why-it-is-so-fast-ddc93f3dffdc)
* [What Is Entanglement and Why Is It Important?](https://scienceexchange.caltech.edu/topics/quantum-science-explained/entanglement)


# Quantum Error Correction

* [How Quantum Computers Will Correct Their Errors](https://www.quantamagazine.org/how-quantum-computers-will-correct-their-errors-20211116)
* [The Best Qubits for Quantum Computing Might Just Be Atoms](https://www.quantamagazine.org/the-best-qubits-for-quantum-computing-might-just-be-atoms-20240325/)


# Negative Probability

The probability axioms require that P(E)≥0 for every event E, and that the probability P(Ω) of the entire sample space is 1. So a system with negative probability, or probabilities greater than 1, does not satisfy the axioms of being a probability space.

In probability theory, probabilities are always non-negative. Therefore, a negative probability does not have a mathematical meaning. Probabilities are used to quantify the likelihood of an event occurring and are always between 0 and 1, with 0 indicating that an event is impossible and 1 indicating that an event is certain.

But in quantum mechanics, you do have negative probabilities. However events with negative probabilities can never be observable. Although technically not a probability relaxing the axioms to allow negative probabilities is extremely useful in the quantum world. They have a name: QuasiProbabilities.
In quantum mechanics,
you are operating with a 2-norm probability. In this case, we are generalize probability so that instead of P(x)+P(not x)=1 for an event x, we have P(x)2+P(not x)2=1. Then P(x) can be negative, or complex.

* [Can Probabilities Be Negative? – What this question teaches us about quantum theory](https://www.youtube.com/watch?v=std9EBbtOC0)
* [Can Probability be Negative? | Quantum Mechanics | Quantum Computing](https://www.youtube.com/watch?v=ZCrjRCwjPbw)
    * Quantum theory is about information, and about how probabilities behave when information is fundamentally inaccessible to observers.


# Quantum Computing Categories

Quantum computing is divided into two categories:
Quantum Annealers and Logic Gate Based Quantum Computers.
These two different types of quantum computers have two different purposes
and use very different systems and hardware.


## Quantum Annealers (Adiabatic Quantum Computing)

* [Quantum Annealers: Solving The World's Optimization Problems](https://www.linkedin.com/pulse/quantum-annealers-solving-worlds-optimization-problems-brianna-gopaul/)


## Logic Gate Based Quantum Computers


# Vectors & Kets / Dirac Notation

* [Maths of Quantum Mechanics](https://www.youtube.com/playlist?list=PL8ER5-vAoiHAWm1UcZsiauUGPlJChgNXC)
* [The Language of Quantum Physics](https://medium.com/quantafy/the-language-of-quantum-physics-8f35cdf85b34)
* [Quantum Formalism: Vectors](https://medium.com/quantafy/quantum-formalism-vectors-4284251f550a)
* [The Eigenvalue Equation: Explained](https://medium.com/quantafy/the-eigenvalue-equation-explained-a1265321e59f)

* [Bra-Ket Notation](https://www.mathsisfun.com/physics/bra-ket-notation.html)
* [Linear Algebra In Dirac Notation](https://quantum.phys.cmu.edu/CQT/chaps/cqt03.pdf)


# Free Quantum Computing Platforms

A cross-platform Python library for differentiable programming of quantum computers.
Train a quantum computer the same way as a neural network.

* [A Quick Look at Free Platforms and Libraries for Quantum Machine Learning](https://www.opensourceforu.com/2023/07/a-quick-look-at-free-platforms-and-libraries-for-quantum-machine-learning/)
* [PennyLane](https://pennylane.ai/)


# Google Quantum AI

* [Google Quantum AI](https://quantumai.google/)


# Towards a Demystification of Quantum Mechanics

* [episode 1: the concept of state](https://medium.com/carre4/towards-a-demystification-of-quantum-mechanics-de9053357cb8)
* [episode 2: forces and interactions](https://medium.com/carre4/towards-a-demystification-of-quantum-mechanics-e9c519c9b184)
* [episode 3: what is a beam of electrons made of?](https://medium.com/carre4/towards-a-demystification-of-quantum-mechanics-9b7b1659e4)
* [episode 4: an introduction to quantum field theory](https://medium.com/carre4/towards-a-demystification-of-quantum-mechanics-dddcabf25ad3)
* [episode 5: the collapse of the wavefunction](https://medium.com/carre4/towards-a-demystification-of-quantum-mechanics-91bcada12348)
* [The Karpinsky Interpretation of Quantum Mechanics](https://medium.com/@john_99387/the-karpinsky-interpretation-of-quantum-mechanics-7013db304c4d)
* [Duality Of Light Explored By Revisiting The Double-Slit Experiment](https://hackaday.com/2020/10/18/duality-of-light-explored-by-revisiting-the-double-slit-experiment/)
* [The 9 Experiments That Will Change Your View of Light (And Blow Your Mind)](https://www.youtube.com/watch?v=QqY8fY0TqaQ)


# Towards a Demystification of Quantum Computers

* [Quantum Computers, explained with MKBHD](https://www.youtube.com/watch?v=e3fz3dqhN44)
* [What Could Make Quantum Computing Easy to Explain?](https://csferrie.medium.com/what-could-make-quantum-computing-easy-to-explain-647599468c4c)
* [What Makes Quantum Computing So Hard to Explain?](https://www.quantamagazine.org/why-is-quantum-computing-so-hard-to-explain-20210608)
* [Why Everything You Thought You Knew About Quantum Physics is Different - with Philip Ball](https://www.youtube.com/watch?v=q7v5NtV8v6I)
* [Here’s why superposition and entanglement have nothing to do with understanding quantum computers](https://csferrie.medium.com/heres-why-superposition-and-entanglement-have-nothing-to-do-with-understanding-quantum-computers-b2557ed7b5a2)
* [Q-CTRL: Black Opal](https://q-ctrl.com/products/black-opal/)
* [The Quantum Atlas](https://quantumatlas.umd.edu/)


# Phononic Quantum Computer

* [Scientists Just Showed How to Make a Quantum Computer Using Sound Waves](https://singularityhub.com/2023/06/09/scientists-just-showed-how-quantum-computers-could-be-based-on-sound-waves/)
* [Pritzker Molecular Engineering Researchers ‘Split’ Phonons – or Sound – in Step Toward New Type of Quantum Computer](https://www.hpcwire.com/off-the-wire/pritzker-molecular-engineering-researchers-split-phonons-or-sound-in-step-toward-new-type-of-quantum-computer/)
* [How splitting sound might lead to a new kind of quantum computer](https://theconversation.com/how-splitting-sound-might-lead-to-a-new-kind-of-quantum-computer-207974)


# Quokka
[Eigensystems](https://www.eigensystems.com.au/), a quantum computing educational startup
(created by [Chris Ferrie](https://www.youtube.com/watch?v=3DhbSsoFc0g)),
has created a quantum computer emulator, the Quokka.
Its designed to be an indistinguishable emulation of a 30-qubit fault-tolerant quantum computer.
Quokka is an emulation of future quantum computers.
Unlike other quantum simulators, which allow you to inspect the internal state of the quantum information,
a “real” future quantum computer would not allow such capability.

But "why" the Quokka device?
What advantage does it give that can't be provided by other quantum computer simulators?

* [Quokka: the little device set to democratize quantum computing](https://interestingengineering.com/podcast/lexicon/ep-53-quokka-the-little-device-set-to-democratize-quantum-computing)
* [Quokka: Your Personal Quantum Computer](https://www.kickstarter.com/projects/chrisferrie/quokka-your-personal-quantum-computer)
* ["Quokka: Quantum Computing in the Palm of Your Hand" by Chris Ferrie](https://www.youtube.com/watch?v=sziZoUB04zc)


# Quantum Programming Languages

* Python: Used to write quantum algorithms, Python is supported by numerous quantum computing frameworks, such as Ocean and Qiskit.
* QuTiP: An open-source software for simulating the dynamics of open quantum systems. The QuTiP library depends on the excellent Numpy, Scipy, and Cython numerical packages.
* Ocean: A set of quantum computing tools written in Python that include tools for simulating quantum computers, developing and executing quantum circuits, and running quantum algorithms.
* Qiskit: An open-source quantum computing framework that’s also written in Python, Qiskit offers tools to enable you to create and execute quantum circuits, simulate quantum computers, and run quantum algorithms. Qiskit can be installed on Windows7 or higher, Linux, and macOS 10.12.6 or later operating systems. Install - <https://qiskit.org/documentation/install.html>
* Q#: Developed by Microsoft, this quantum computing programming language is used to write quantum algorithms. It also integrates with Visual Studio and other Microsoft development tools.
* Cirq: Developed by Google, Cirq is used to write quantum algorithms. It works with Google’s quantum computing framework. Cirq can be installed on Linux, Mac OS X and Windows operating systems, as well as on the Docker. Install -  <https://cirq.readthedocs.io/en/stable/install.html>
* QDK: QDK has four ways to work: develop with Q# command line applications, develop with Q# Jupyter Notebooks, develop with Q# and Python - Enables you to combine Python and Q# and develop with Q# and .NET. Install - <https://docs.microsoft.com/en-us/quantum/quickstarts/>
* Silq: Silq can be installed on Linux, macOS and Windows. Install - <https://silq.ethz.ch/install>
* Strawberry Fields: Strawberry Fields is a full-stack Python library for designing, optimizing, and utilizing photonic quantum computers. Install - <https://strawberryfields.readthedocs.io/en/stable/_static/install.html>


## QuTiP

* [Quantum Toolbox in Python (QuTiP)](https://qutip.org/)


## Ocean


## Qiskit

Qiskit [kiss-kit] is an open source SDK for working with quantum computers at the level of pulses, circuits, and application modules.
Qiskit accelerates the development of quantum applications by providing the complete set of tools needed for interacting withquantum systems and simulators.

* [Qiskit is the open-source toolkit for useful quantum](https://www.ibm.com/qiskit)

* [How To Use A Quantum Computer - Quantum Computing Tutorial](https://www.youtube.com/watch?v=AoiI507OpEY&list=PLI4lUS6saNgVnzkGCauWSU0FOnZH7VW8x)
* [Getting started with Qiskit](https://www.youtube.com/playlist?list=PLOFEBzvs-VvpHs84vFdRVIl3Wlg81j8_x)
* [Getting Started with Qiskit (explained by a software developer, not a quantum physicist)](https://medium.com/queen-of-qiskit/getting-started-with-qiskit-explained-by-a-software-developer-not-a-quantum-physicist-b8ba820685e5)
* [Qiskit Textbook](https://qiskit.org/learn)
* [Qiskit Videos](https://www.youtube.com/channel/UClBNq7mCMf5xm8baE_VMl3A)
* [A guide to the Qiskit circuit library](https://medium.com/qiskit/a-guide-to-the-qiskit-circuit-library-36ee0f189956)
* [Quantum Computer Coin Flips in Python Are Pure Fun](https://towardsdatascience.com/flip-a-coin-on-a-real-quantum-computer-in-python-df51e5f2367b)
* [Quantum Computing With QISKit](https://hackaday.com/2019/04/02/quantum-computing-with-qiskit/)
* [Coding with Qiskit](https://www.youtube.com/playlist?list=PLOFEBzvs-Vvp2xg9-POLJhQwtVktlYGbY)
* [Using Qiskit with IBM QX to generate quantum circuits](https://hub.packtpub.com/using-qiskit-with-ibm-qx-to-generate-quantum-circuits-tutorial/)

* [Harshit Gupta series of article](https://medium.com/@harshit.11235)
* [Quantum Untangled](https://medium.com/quantum-untangled)

* [Programming for Quantum Computing Pt. 1: NumPy](https://medium.com/quantum-untangled/programming-for-quantum-computing-pt-1-numpy-d3e0c5a843ef)
* [Programming for Quantum Computing Pt. 2: Qiskit](https://medium.com/quantum-untangled/programming-for-quantum-computing-pt-2-qiskit-53a4c05be281)

* IBM Quantum Challenge: Spring 2023
    * [Lab 1](https://medium.com/@_monitsharma/ibm-quantum-challenge-spring-2023-lab-1-fd80c4b5cda1)
    * [Lab 2](https://medium.com/@_monitsharma/ibm-quantum-challenge-spring-2023-lab-2-d3b993807b61)
    * [Lab 3](https://medium.com/@_monitsharma/ibm-quantum-challenge-spring-2023-lab-3-9b92e3152bfc)
    * [Lab 4](https://medium.com/@_monitsharma/ibm-quantum-challenge-spring-2023-lab-4-541a7e0e6478)
    * [Lab 5](https://medium.com/@_monitsharma/ibm-quantum-challenge-spring-2023-lab-5-6d932eb1922)


### QWorld QEducation
[QEducation](https://qworld.net/qeducation/) is the department of QWorld working on for educational and related activities
and makes use of IBM's Qiskit.


### Qiskit + Raspberry Pi

* Qrasp (Quantum RASPberry PI)
    * [Qrasp — Quantum on a Raspberry Pi](https://medium.com/qiskit/qrasp-a-wee-quantum-computer-74ef7f927b1e)
    * [GitHub: ordmoj/qrasp](https://github.com/ordmoj/qrasp)
* RasQberry
    * [RasQberry: Quantum Computing is the Coolest Project for Raspberry Pi](https://medium.com/qiskit/rasqberry-quantum-computing-is-the-coolest-project-for-raspberry-pi-3f64bec5a133)
* Other
    * [GitHub: KPRoche/quantum-raspberry-tie](https://github.com/KPRoche/quantum-raspberry-tie)


### Qiskit Metal

* [Qiskit Metal | Quantum Device Design](https://www.qiskit.org/metal/)


## Q #


## Cirq

Cirq is an open source framework for programming quantum computers.
Cirq is a Python software library for writing, manipulating, and optimizing quantum circuits, and then running them on quantum computers and quantum simulators. Cirq provides useful abstractions for dealing with today’s noisy intermediate-scale quantum computers, where details of the hardware are vital to achieving state-of-the-art results.

* [Cirq](https://quantumai.google/cirq)
* [Google Quantum AI](https://quantumai.google)


# TKET

TKET is an advanced software development kit for the creation and execution of programs for gate-based quantum computers.

* [TKET](https://www.quantinuum.com/developers/tket)


# Making a Quantum Computer

* [Making a Quantum Computer at Home](https://okezuebell.medium.com/making-a-quantum-computer-at-home-bc59afe72d7d)


## Simple Simulator

* [Simple Quantum Computing in 150 Lines of Python](https://hackaday.com/2018/04/10/simple-quantum-computing-in-150-lines-of-python/)



## QuTiP

QuTiP is open-source software for simulating the dynamics of open quantum systems.

* [Taking Python to the Next Level](http://www.linuxjournal.com/content/taking-python-next-level)
* [QuTiP](http://qutip.org/)


# Tutorials on Quantum Physics

* [Before You Start On Quantum Mechanics, Learn This](https://www.youtube.com/watch?v=Nd4b0_vJZUk)
* [Quantum Mechanics](https://www.youtube.com/playlist?list=PL193BC0532FE7B02C)
* [Quantum Computing](https://www.youtube.com/playlist?list=PLd6LlmQSrtAH6-M2YZVbHYHt4kwo1bpuo)
* [Our quantum problem](http://aeon.co/magazine/science/our-quantum-reality-problem/)
* [Quantum entanglement is tough to dumb down, but this analogy can help detangle it](https://aeon.co/videos/quantum-entanglement-is-tough-to-dumb-down-but-this-analogy-can-help-detangle-it)
* [encyclopedia of quantum information](http://www.quantiki.org/wiki/Main_Page)
* [Online course trains students in the bizarre world of quantum computing](https://www.livescience.com/quantum-computing-students-online-course.html)


# Tutorials / Books on Quantum Computing

* [Qiskit Blog](https://medium.com/@qiskit)
* [NEW Qiskit Blog](https://www.ibm.com/quantum/blog)
* [IBM Quantum Learning](https://learning.quantum.ibm.com/)

* [Qiskit Textbook](https://qiskit.org/learn/)

    * [Understanding Quantum Information and Computation](https://www.youtube.com/watch?v=0Av89fZenSY&list=PLOFEBzvs-VvqKKMXX4vbi4EB1uaErFMSO&index=2)
    * [Getting started with Qiskit](https://www.youtube.com/watch?v=P5cGeDKOIP0&list=PLOFEBzvs-VvpHs84vFdRVIl3Wlg81j8_x)

* [How does quantum computing work?](https://plus.maths.org/content/how-does-quantum-commuting-work)
* [Quantum computing: Some (not so) gruesome details](https://plus.maths.org/content/really-how-do-quantum-computers-work)
* [Quantum Computing as a High School Module](https://arxiv.org/pdf/1905.00282.pdf)
    * [Fermilab scientists publish quantum computing course for high school students](https://news.fnal.gov/2020/06/fermilab-scientists-publish-quantum-computing-course-for-high-school-students/)
* [A free Quantum Computing Tutorial](https://medium.com/@vinven7/a-free-quantum-computing-tutorial-d13a099c91ca)
* [Learn Quantum Computing With These Seven Projects](https://medium.com/qiskit/learn-quantum-computing-with-these-seven-projects-7478d90d125a)
* [Quantum Machine Learning](https://www.youtube.com/watch?v=xgA4Dx_7q34&list=PLOFEBzvs-VvqJwybFxkTiDzhf5E11p8BI)
* [Hands-On Quantum Machine Learning With Python](https://leanpub.com/pyqml-vol1)
* [Hands-On Quantum Machine Learning With Python Volume 2](https://www.kickstarter.com/projects/pyqml/hands-on-quantum-machine-learning-with-python-volume-2)
* [Hands-On Quantum Machine Learning With Python](https://pyqml.substack.com/)
* [Towards Solving Optimization Problems With A Quantum Computer](https://pyqml.substack.com/p/towards-solving-optimization-problems)
* [Quantum Machine Learning: An Advanced End-to-End Project](https://medium.com/@SPX701/quantum-machine-learning-an-advanced-end-to-end-guide-3316c542226d)

* [Introduction to Quantum Computing](https://csferrie.medium.com/introduction-to-quantum-computing-df9e1182a831)
    * [Resources for Quantum Computing](https://csferrie.medium.com/introduction-to-quantum-computing-619068d48667)
    * [Introduction to Quantum Computing](https://www.youtube.com/playlist?list=PLtvBHm6EzL47oFXGRB7Oe-kfcn_0ZnJE2)
    * [A free introduction to quantum computing and quantum mechanics](https://quantum.country/)


# IBM Q

* [IBM A Experience Documentation: Beginners Guide](https://quantumexperience.ng.bluemix.net/qx/tutorial?sectionId=beginners-guide&page=introduction)
* [IBM Q Experience](https://quantumexperience.ng.bluemix.net/qx/experience)
* [IBM Q announces a host of new tools geared towards making quantum computing more accessible](https://www.neowin.net/news/ibm-q-announces-a-host-of-new-tools-geared-towards-making-quantum-computing-more-accessible)


# Quantum Computing Simulation

* [Quantum Simulation Explained in 9 Slides](https://www.youtube.com/watch?v=kD370qyxTyw)
    * [Qiskit](https://www.youtube.com/qiskit)
    * [The Variational Quantum Eigensolver — Programming on Quantum Computers — Coding with Qiskit S2E4](https://www.youtube.com/watch?v=Z-A6G0WVI9w)
* [List of Quantum Computing Simulators](https://www.quantiki.org/wiki/list-qc-simulators)
* [Taste the future -- try out a cloud-based quantum computer](http://betanews.com/2013/09/06/taste-the-future-try-out-a-cloud-based-quantum-computer/)
* [jQuantum - Quantum Computer Simulator](http://jquantum.sourceforge.net/)
* [Google’s Quantum Computing Playground turns your PC into a quantum computer](http://www.extremetech.com/extreme/182913-googles-quantum-computing-playground-turns-your-pc-into-a-quantum-computer)
* [Quantum Computing Playground](http://www.quantumplayground.net/#/home)
* [Quantum computer emulated by a classical system](http://phys.org/news/2015-05-quantum-emulated-classical.html)
* [Our new Quantum Virtual Machine will accelerate research and help people learn quantum computing](https://blog.google/technology/research/our-new-quantum-virtual-machine-will-accelerate-research-and-help-people-learn-quantum-computing/)


# Quantum Communication

* [Quantum Communications in Your Browser](https://hackaday.com/2018/01/31/quantum-communications-in-your-browser/)


# Build Your Own Quantum Computer

* [36C3: Build Your Own Quantum Computer At Home](https://hackaday.com/2019/12/30/36c3-build-your-own-quantum-computer-at-home/)


# Classic Physics Analogs for Quantum Systems

* [The Amazing Physics Of The Wilberforce Pendulum](https://www.youtube.com/watch?v=M0Zjl_tMOZg)


# Hilbert Space

Hilbert Space is an indispensable tools in the theories of partial differential equations, quantum mechanics, Fourier analysis (which includes applications to signal processing and heat transfer), control theory, machine learning, and ergodic theory (which forms the mathematical underpinning of thermodynamics).
The term “Hilbert space” is often reserved for an infinite-dimensional inner product space having the property that it is complete or closed. However, the term is often used nowadays, in a way that includes finite-dimensional spaces, which automatically satisfy the condition of completeness.

* [Hilbert Space Explained](https://medium.com/predict/hilbert-space-explained-cc33de334979)
* [Hilbert Space](https://medium.com/@brcsomnath/hilbert-space-7a36e3badac2)


# ZX Calculus / Quantum in Pictures

The ZX-calculus is a rigorous graphical language for reasoning about linear maps between qubits, which are represented as string diagrams called ZX-diagrams.
ZX-calculus is a set of rewrite rules that allows you to distill quantum circuits into a reduced form; ie. You optimize a quantum circuit allowing for it to be more easily run.

ZXW calculus is an extension of ZX calculus. ZXW calculus was developed by Quantinuum scientists as they work on a series of foundational problems relating to quantum computing and compositional intelligence.

* Calculus: A particular method or system of calculation or reasoning.
* Linear Map: Mapping C → W between two vector spaces that preserves the operations of vector addition and scalar multiplication.

* [Bob Coecke: From Quantum in Pictures to Quantum AI | QHack 2023](https://www.youtube.com/watch?v=5694S6hceJE)

* [Quantum in Pictures](https://www.quantinuum.com/news/quantum-in-pictures)
    * [Everyone can learn quantum now, even at a cutting-edge level…and we have the test scores to prove it!](https://medium.com/quantinuum/everyone-can-learn-quantum-now-even-at-a-cutting-edge-level-and-we-have-the-test-scores-to-prove-49e7fdc5c509)
    * [Quantum in Pictures: A New Way to Understand the Quantum World](https://www.amazon.com/Quantum-Pictures-New-Understand-World/dp/1739214714/)
    * [Picturing Quantum Processes](https://www.amazon.com/Picturing-Quantum-Processes-Diagrammatic-Reasoning/dp/110710422X)
* [The ZX-calculus](https://zxcalculus.com/)
    * [How ZX-calculus reveals the logic and processes of quantum mechanics to everyone](https://medium.com/quantinuum/how-zx-calculus-reveals-the-logic-and-processes-of-quantum-mechanics-to-everyone-944fc3bbbb2c)
    * [ZX Quantum-Py: A beginner's guide to Quantum Computing and ZX-Calculus using PyZX](https://www.amazon.com/ZX-Quantum-Py-beginners-Computing-ZX-Calculus/dp/B0B1RD2Z84/)
    * [Categories for Quantum Theory](https://www.amazon.com/Categories-Quantum-Theory-Introduction-Mathematics/dp/0198739613)
    * [pyZX - quantum circuit optimisation with the ZX calculus](https://www.youtube.com/watch?v=iC-KVdB8pf0)
    * [QNLP 2019: Working with PyZX - Aleks Kissinger](https://www.youtube.com/watch?v=JafI_LZts2g)
    * [Kindergarden quantum mechanics graduates ...or how I learned to stop gluing LEGO together and love the ZX-calculus](https://www.sciencedirect.com/science/article/abs/pii/S0304397521004308)
* Tools
    * [ZXLive - An Interactive GUI for the ZX Calculus - Razin A. Shaikh](https://www.youtube.com/watch?v=J--c2q-KOc8)


# Tensor Diagram / Tensor Networks

Tensor network theory is a branch of mathematics that deals with the representation of high-dimensional tensors. Tensors are mathematical objects that generalize matrices to higher dimensions. Tensor network theory provides a way to represent these high-dimensional objects using a lower-dimensional network. This theory has applications in machine learning, where it can be used to represent high-dimensional data.

* [Tensor Network](https://tensornetwork.org/)


## Tensor Network Algorithm Out Perfroming Quantum Computer

* [A Moving Target for Quantum Advantage](https://physics.aps.org/articles/v17/13)
    * [Efficient Tensor Network Simulation of IBM’s Eagle Kicked Ising Experiment](https://journals.aps.org/prxquantum/abstract/10.1103/PRXQuantum.5.010308)


