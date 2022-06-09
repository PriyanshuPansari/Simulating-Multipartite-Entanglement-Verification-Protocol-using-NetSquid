# Simulating-Multipartite-Entanglement-Verification-Protocol-using-NetSquid
## Problem Statement
The goal of this project is to simulate the Multipartite Entanglement Verification protocol in a quantum network with N participating nodes. The choice of the verifier may be random or fixed. The verification protocol should then be tested for the following input states:

The input state is the N-partite GHZ state.
The input state is |0> on all N-qubits.
The input state is the maximally mixed state on N-qubits (optional).
For each case, indicate the probability with which the input state will be accepted.

## Implementaion
This [Paper](https://arxiv.org/abs/1112.5064) was implemented as a solution to the problem.

### Network
The netwoek implemented consisted of N+1 nodes-
-1 source node
-1 verifier node
-(n-1) party node

There is a bi-directional classical channel between verfier node and each party, while there is a quantum channel between source node and verifier and party node. 

### Protocols
Three types of protocols were defined-
1)Source protocol for source node
2)Verifier Protocol for verifer node
3)Party Protocol for party node.

###The Protocol-
#### Source protocol
Source node sends an qubit to verifier node and each party nodes. It can be either honest or dishonest, if it is honest it will create a n-party GHZ state and distribute it to the n parties.

#### Verifier protocol
On reciving data the qubit from source node, it will  select for each i ∈ [n] a random input X<sub>i</sub> ∈ {0, 1}, such that <br/>
![image 1](https://bit.ly/3aF1ei7), <br/>
and sends it to the corresponding party via a private classical channel.

#### Party protocol
After reciving the bit from Verifier node, it perfoms an operation on qubit recived from source node.
If Xi = 0, party i performs a Z operation.
If Xi = 1, party i performs a Hadamard operation.
Party i measures in the {|0i, |1i} basis and sends
the corresponding outcome Yi ∈ {0, 1} to the Verifier via the private channel.

#### Verifier protocol
 The Verifier accepts the result if and only if: <br/>
![equation](https://bit.ly/3mzRMPM)
