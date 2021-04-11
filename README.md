# ShowMeTheMoney-QCHack-IBM-Challenge

This is our repository for the Quantum Coalition hackathon.  It will include our solutions to the IBM technical challenge!

Our goal was to implement Grover's algorithm on a ternary quantum computer by using Qiskit pulse.  With Qiskit Pulse, we could theoretically differentiate between the first three energy states of the superconducting qubit to create a 3-dimensional orthonormal basis.  The idea was to follow the theoretical framework mapped out in (https://www.researchgate.net/publication/265335475_Synthesis_of_Ternary_Grover%27s_Algorithm), so we would just need to recreate all of the ternary gates with Qiskit Pulse and implement the circuit from the paper.  However, we ran into many problems, preventing us from finishing.

First, the only backend simulator with access to pulse was not working very well.  When applying the Qiskit textbook code from (https://qiskit.org/textbook/ch-quantum-hardware/accessing_higher_energy_states.html) to the backend FakeArmonk simulator, results were completely different than expected.  Other teams in discord seemed to be having the same issues, and mentors recommended not to use the simulator.  Thus, we had to wait over 8 hours for the textbook code to run.  Once that ran, I was going to wrap the 0/1/2 discrimination classifiers in an object and save it to github, but the device was so noisy that the exact textbook code gave ridiculous results that weren't even classifiable to the LinearDiscriminantAnalysis tool.  Thus, even if we finished the rest of Grover's algorithm, we had no way of measuring the 0/1/2 states with Pulse.  I uploaded pictures of my results compared to the qiskit textbook in "Results of Accessing Higher Energy States from qiskit textbook".

Furthermore, the Qiskit Quantum Experience went down the morning that the project was due, preventing us from being able to test some of our pulse-gates.  With all the issues, we weren't able to rapidly get through the gates that we needed to construct with Pulse.  We also had trouble figuring out how to implement custom multi-qubit control gates with Pulse, which has very little documentation and is very physics/math heavy.  This soaked up a lot of our time and prevented us from finishing.  However, we still implemented most of the gates needed for the ternary Grover's algorithm with Pulse, so we have most of the framework necessary for implementation.

If we had more time, we would be able to spend more time learning the multi-qubit control pulses and adapt it to the crucial multi-control Muthukrishnan-Stroud gate.

I included my mathematical analysis of the gates in "Ternary Grover gate analysis.pdf", which shows how to implement all the Ternary 1-qutrit permutative gates with just the 0->1 pulse and the 1->2 pulse from the qiskit textbook (Accessing Higher Energy States chapter).
>>>>>>> Stashed changes
