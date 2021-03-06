# ShowMeTheMoney-QCHack-IBM-Challenge
By Tyler Schon, Ray Zhang, Inho Choi, Irham Arfakhsadz Putra, and Hyun Jin Kim

This is our repository for the Quantum Coalition hackathon.  It will include our solutions to the IBM technical challenge!

## Project Overview: ##

Our goal was to implement Grover's algorithm on a ternary quantum computer by using Qiskit pulse.  With Qiskit Pulse, we could theoretically differentiate between the first three energy states of the superconducting qubit to create a 3-dimensional orthonormal basis.  The idea was to follow the theoretical framework mapped out in (https://www.researchgate.net/publication/265335475_Synthesis_of_Ternary_Grover%27s_Algorithm), so we would just need to recreate all of the ternary gates with Qiskit Pulse and implement the circuit from the paper.  However, we ran into many problems, preventing us from finishing.

## Challenges and Roadblocks: ##

First, the only backend simulator with access to pulse was not working very well.  When applying the Qiskit textbook code from (https://qiskit.org/textbook/ch-quantum-hardware/accessing_higher_energy_states.html) to the backend FakeArmonk simulator, results were completely different than expected.  Other teams in discord seemed to be having the same issues, and mentors recommended not to use the simulator.  Thus, we had to wait over 8 hours for the textbook code to run on the open `ibmq_armonk` due to the long wait time by large amount of usage and number of jobs sent from the Qiskit community. Once that ran, I was going to wrap the 0/1/2 discrimination classifiers in an object and save it to github, but the device was so noisy that the exact textbook code gave ridiculous results that weren't even classifiable to the LinearDiscriminantAnalysis tool.  Thus, even if we finished the rest of Grover's algorithm, we had no way of measuring the 0/1/2 states with Pulse.  I uploaded pictures of my results compared to the qiskit textbook in "Results of Accessing Higher Energy States from qiskit textbook".

Furthermore, the Qiskit Quantum Experience went down the morning that the project was due, preventing us from being able to test some of our pulse-gates.  With all the issues, we weren't able to rapidly get through the gates that we needed to construct with Pulse.  We also had trouble figuring out how to implement custom multi-qubit control gates with Pulse, which has very little documentation and is very physics/math heavy.  This soaked up a lot of our time and prevented us from finishing.  However, we still implemented most of the gates needed for the ternary Grover's algorithm with Pulse, so we have most of the framework necessary for implementation.

## Project Impact ##
The primary current limiting factors in scaling quantum processors are the connectivity between qubits, and the error rates that come with each gate applied between state preparation and measurement. While extending into ternary computation may pose increased error rates due to decoherence, as well as requiring finer levels of resolution to control, it also directly reduces these other factors and may be a worthy trade-off.

In particular, Grover???s algorithm is one that requires the use of n-ary controlled (Toffoli) gates on a quantum computer, which requires an exponentially increasing number of two-qubit gates for qubit processors. On qutrit processors, however, the extra degree of freedom enables us to design a recursion relation that only requires a number of two-qutrit gates linear in the length of the input. This theoretically allows us to out-perform binary qubits on error accumulation from running excessively many gates, especially on domains with lengths significant enough to consider quantum processing over classical searches. 

## Next Steps: ##

If we had more time, we would be able to spend more time learning the multi-qubit control pulses and adapt it to the crucial multi-control Muthukrishnan-Stroud gate.  We also did not have time to implement the ternary phase gate used in the ternary diffusion operator.

## Place in Research/Application Roadmap ##
There is little groundwork published for any ternary, let alone n-ary extensions to quantum computation, and what we were able to find were primarily limited to the theoretical domain.  

Ternary computers had been attempted before, as an implementation of classical computing, before it was abandoned in favour of the cheaper and more scalable binary models we have today. Without knowing exactly how the quantum computing race will pan out, we cannot rule out this possibility in quantum either. However, scaling to larger processors proves to be a significantly harder challenge for quantum devices as mentioned above. Attempts at fault-tolerance via error-correcting codes make this worse, as they require a large number of physical qubits to encode each logical qubit. Naturally then, it is important for the community to develop quantum computers that are as scalable as possible. Seeing as how some of the physical implementations of quantum computers naturally lend to 3-state computing, the barrier of independent hardware development does not hold us back from simply experimenting with existing systems such as Qiskit Pulse. We hope in the future that there will be more groundwork laid out for ternary/n-ary quantum systems just as there are pre-packaged logical circuits for binary qubits. With the power of quantum computers to efficiently explore a problem space regardless of the base it is working in, we bellieve there is great potential in ternary and above extensions to the standard binary algorithms we already know.

## Included Work: ##

I included my mathematical analysis of the gates in "Ternary Grover gate analysis.pdf", which shows how to implement all the Ternary 1-qutrit permutative gates with just the 0->1 pulse and the 1->2 pulse from the qiskit textbook (Accessing Higher Energy States chapter). This was later used to actually implement these gates as pulse schedules by utilizing the 0->1 and 0->2 pi pulses. This is included in the "qutrit permutative gate" jupyter notebook.  

The ternary superposition gate, or S gate was another gate that's used in the ternary Grover's algorithm that we wanted to synthesize. Although we couldn't test it and it's highly unlikely that it will yield us the desired result, we tried to make it by applying the pi/2 rotation to the qutrit in the x direction and performing Rabi experiment to it. We attempted to find the approximate amplitude of the pulse needed to rotate the qutrit around the z-axis. This is shown in the jupyter notebook "ternary superposition gate".

Working document for this project, with further outlines and rough notes:
https://docs.google.com/document/d/1Zy9Lxo0mVYq2J1ukN5AREstCB512FrNiPokVhSTMgJI/edit
