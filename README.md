# QuantumStatePreparation
An implementation of a state preparation circuit in Qiskit

This file contains a python notebook with a few different useful functions in it.

The first function takes a list of real coefficients and generates the angles that need to be fed into a quantum circuit in order to generate the appropriate quantum state. The output of this function is a ``tree-like" array, meaning that it can be visualized and treated like a tree, which will be more helpful for refining this implementation and simplifying things going forward. 

The next is a simple implementation of a multicontrolled Ry gate using only one qubit gates and a single multicontrolled Rz gate.

The last is a circuit generator that takes a "tree-like" array, and outputs an appropriate quantum circuit that meets the general desired shape for quantum state preparation. While this function is currently tailored to the task at hand, the general shape could easily be modified to handle any inductive style circuit. I've created two separate versions of this function, which are essentially identical. The only difference is that one uses the built-in multicontrolled Ry gate, primarily since that allows one to see the angles that Ry is rotating by, unlike the custom implementation I've done.

Everything is put together in one final function, quantum_state_preparation, which takes a list of 2^n complex numbers (expressed as tuples (a,b)). Currently, there isn't support for non-real numbers, but that will be changed soon.

At the end is a function to test the implementation using randomly generated unit vectors of any dimension, fittingly called "testing", with the only necesssary input being the dimension.

Of particular note is that this circuit is not as efficient as it could be, since we were not allowed to use CNOT gates in the project, thus limiting my ability to do a controlled swap, which I think should have enabled significant savings in gate depth at the cost of some ancillas.
