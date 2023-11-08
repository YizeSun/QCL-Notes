# Build Quantum Computer
[toc]

Opencourse for building quantum computer from TU-Delft

This course has two parts, [part 1](https://ocw.tudelft.nl/courses/building-blocks-quantum-computer-part-1/) for the layer -- qubits and [part 2](https://ocw.tudelft.nl/courses/building-blocks-quantum-computer-part-2/) for other layers to build and operate real quantum computer.

## Part I

## Part II

### Module 1 - Introduction to the building blocks of a quantum computer
structure of quantum computer ![see](./images/m1-QCstructure.png), path of temperature ![see](./images/m1-Qprocessor2classic.png) and scalability of QC ![see](./images/m1-ScalableQC.png)

Key:
1. Structure of base: two parts, quantum processor and electronic interface which are connected with wires
   Quantum Processor <---(control using pulse) electronic interface
                   --->(measurement using charge sensor)

2. The bottleneck for scalability:
    is the number of wires. Thus they try to move the electronic interface as close as possible to quantum processor.

3. Challenges:
   1. Equipment performance(timing accuracy, tight pulses frequency, stability, read out noise), 
   2. power dissipation(the lower the temperature, the less available the power).
   3. cryogenic technology(electronics that works in the very low temperature)

4. CMOS is the only operator that can work near 30mK temperature with scalability.


Additional reading:
1. [Time line](https://en.wikipedia.org/wiki/Timeline_of_quantum_computing_and_communication) of quantum computing and communication
2. Feynman mentions for the first time the potential of building a quantum computer [ [paper](https://catonmat.net/ftp/simulating-physics-with-computers-richard-feynman.pdf)]
3. Scalable solution for system integration (Cryo-CMOS Circuits and Systems for Quantum
Computing Applications) [ [paper](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=8036394)]
4. [Dilution refrigerator](https://nanoscience.oxinst.com/assets/uploads/NanoScience/Brochures/Principles%20of%20dilution%20refrigeration_Sept15.pdf)  

### Module 2 -- Micro-architecture, compiler and programming languages
1. Qubit Addressing Table, which allows us to keep track of qubits and their location. This table is crucial for accommodating the routing mechanism.
Programming langes list:
   1. [ScaffCC](https://github.com/epiqc/ScaffCC)
   2. [ProjectQ](https://github.com/ProjectQ-Framework/ProjectQ)
   3. [LIQUid](https://github.com/StationQ/Liquid)
   4. [OpenQL](https://github.com/QuTech-Delft/OpenQL)
2. Quantum Compiler (providing part of quantum instruction set):
   1. Decomposition of quantum gates
   2. Optimization of circuits to reduce #qubits or #operations
   3. Schedule the operations to maximize the parallelism of the algorithsm.(reduce latency, build a dependency graph based on ”as soon/late as“ principles)
   4. Map quantum circuit such that chip constraints are satisfied.
   5. Create a Fault-tolerant version of circuit
3. Quantum Compiler list:
   1. ProjectQ from ETH
   2. ScaffCC from Chicago University
   3. Liquid from Microsoft
   4. OpenQL from Qutech(TU-Delft)
### Module 3 -- Quantum Algorithm and Error Correction
1. Phase kickback
   1. given an arbitrary unitary, and one eigenstate as input for the target qubits, then the phase of the component of state of target qubit is transferred to the control qubit, which can then be read out($|0\rangle\langel 0|+e^{i\theta_k}|1\rangel\langel 1|$ is applied to the control qubit). This trick can also be used to read out the action of an arbitrary large unitary.
   2. To measure phase, apply a inverse QFT at the end of circuit. Binary fractions is the way to describe the phase. Apply phase kickback multiple times through applying Unitary multiple times.
2. Grover's algorithm
   1. Prepare $G=U_+ U_f$ where $U_f = I-2|w \rangle \langle w|$ and $U_+=2|+ \rangle \langle +| - I$
   2. $G^k |+\rangle^{\otimes n}$ is close to $|w\rangle$ for a certain k
   3. root squart speedup
3. Error correction
   1. lower than $10^{-15}$.
   2. Bit-flip Error
   3. Phase-flip Error
   4. Surface code together with 49 qubits are used to describe one logical qubit, it is a way for error correction
### Module 4 Quantum Internet I
1. Quantum Internet is the network of quantum devices, the edges are channels for transfering quantum information.
2. Quantum Communicaion, the probability of receiving photon from one side is $P(d) = 10^{-d\tau} $ where d is the distance and $\tau$ is the attenuation
   1. a repeater is needed for long distance communication
   2. Free-space channels or fiber-optical channels
### Module 5 Quantum Internet II
1. Secure communication using the one-time pad (pre-shared key)
   1. Encode: Message + Key = ciphertext
   2. Decoder: ciphtext+ key = message
   3. ciphertext1 + cipertext2 = message21 + message2
2. Quantum Key Distribution
   1. Using qubits
   2. postprocessing(nothingantum)
   3. Process: ![see](./images/m5-quantum-key-distribution.png)
3. [Entanglement distillatio protocol](https://en.wikipedia.org/wiki/Entanglement_distillation)n for long distance
   1. the quantum correlation becomes weaker in long distance.
   2. using fidelity as the quality of entanglement after distillation
   3. [examples](https://www.youtube.com/watch?time_continue=291&v=Re0T4nHaY1U&embeds_referring_euri=https%3A%2F%2Focw.tudelft.nl%2F&source_ve_path=Mjg2NjY&feature=emb_logo)
   

### Module 6 Wrapping up the building blocks of a quantum computer
1. Surface code:
   1. XZ = -ZX
   2. $|\psi \rangle \in C, s|\psi \rangle = |\psi \rangle s\in S$, $S$ is a set of operators; $S$ stabilize $\psi$ because $\psi$ is the eigenstate of $s \in S$.
   3. $|\psi\rangle \rightarrow E|\psi\rangle$ $E$is error that may or may not occur.
   4. Then $\langle \psi|EsE\psi\rangle$ = -1 if E occur else 1
   5. did'n really get the point, learn it later if I really need it.
2. [Quantum Fourier Transformer](https://ocw.tudelft.nl/course-lectures/6-2-2-small-quantum-fourier-transforms/?course_id=31394)
   $QFT_k$ on k qubits is described as a superposition with uniform magnitude but varies in phase: "$|Z\rangle = \frac{1}{\sqrt{2^k}} \sum_b exp(2\pi i \frac{Zb}{2^k} |b \rangle)$", Z, the input, here is the speed of QFT proceeds around the unit circle. The each row of the QFT matrix is described by state from possible Z times b. e.g., the first row is rotation results on the unit circle by 0 times all b , the second row is the rotation results on the unit circle by 1 times all b, ...  
3. Quantum Libraries:
   1. [Quantum programming softwares](https://en.wikipedia.org/wiki/Quantum_programming)
   2. [Quantum information for jobs, conference, simulators...](https://www.quantiki.org/)
   3. [Github for quantum software libraries](https://github.com/qosf/awesome-quantum-software), e.g., quantum full stack libraries, quantum simulators, quantum anealing classified by programming languages.