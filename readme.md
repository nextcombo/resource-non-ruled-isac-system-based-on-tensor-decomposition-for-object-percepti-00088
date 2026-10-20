# Resource-Non-Ruled ISAC System Based on Tensor Decomposition for Object Perception [with MATLAB Code]

Resource-Nonregular ISAC System with Object Perception Based on Tensor Decomposition
I. Topic based on the resource non-regular integration perception and communication (ISAC) system objective perception
II. Abstract: The current ISAC system target perception methods mostly assume the rule-based allocation of time-frequency resources, but in real scenarios, the randomness of user scheduling leads to a non-regular distribution of time-frequency resources, rendering traditional algorithms ineffective.
This paper combines CPD tensor decomposition with tensor completion, proposing a structured tensor completion and decomposition method (STCD).
1  
It can utilize the echo signal of non-regularly allocated resources and interpolate and reconstruct signals in unallocated resource areas.
2  
Recover the Van Dam structure of the steering matrix by tensor completion, introduce tensor rank - 1 constraint, which is more relaxed than traditional CPD.
3  
The Cramér-Rao lower bound (CRB) for the joint estimation of angle, distance, and velocity in non-regular resource scenarios is derived. This extends the traditional CRB analysis to any arbitrary non-regular resource pattern.
Simulation results show that the proposed STCD method has better perception accuracy and algorithm success rate than traditional algorithms such as 2D-DFT, MUSIC, OMP, VCPD, IMDF in non-regular ISAC scenarios.
III. Introduction
The core task of ISAC system target perception is to utilize base station received echo signals to complete the joint estimation of multiple parameters such as target angle, distance, and velocity. The mainstream relies on MIMO-OFDM architecture to achieve parameter joint resolution.
Existing method pain points 1.
1. Traditional algorithms rely on the assumption that 2D-DFT is only applicable to regular time-frequency resource scenarios, where DFT spectrum is completely disrupted and fails under non-regular scenarios, constrained by system bandwidth and coherent processing intervals, leading to limited resolution; MUSIC can only estimate angles in non-regular resource scenarios, unable to achieve simultaneous estimation of distance and velocity, and its subspace decomposition precision sharply decreases under low signal-to-noise ratio; Compressive Sensing OMP can adapt to small-scale non-regular scenarios, but the construction of a three-dimensional dictionary introduces exponential computational complexity, significantly reducing estimation accuracy or even causing algorithm failure under non-sparse targets.
2. Current limitations of tensor-based methods are based on CPD tensor decomposition, which retains the high-dimensional structure of echo signals and enhances estimation accuracy, but is only applicable to regular resource allocation; the absence of time-frequency units under non-regular resources leads to missing elements in tensor elements, destroying the low-rank property of tensors and the Van der Waals structure of the steering matrix, making traditional tensor decomposition methods inapplicable directly.
3. Research gaps lack a high-resolution, low-complexity, multi-parameter joint target perception framework for resource-non-regular ISAC scenarios, and lack uniqueness conditions for tensor decomposition under non-regular resources and CRB theory support.
The core motivation of this paper: Addressing the pain points of non-random and non-periodic distribution of time-frequency resources in actual ISAC systems, integrating tensor completion with structured CPD decomposition, designing target perception algorithms that can adapt to any non-regular resource patterns, and completing theoretical uniqueness analysis, CRB derivation, and algorithm performance verification.
IV. Methodology Theory
1. System and Signal Model Construction - A single-cell multi-user MIMO-OFDM ISAC system is constructed, with a base station using a single-base array configuration, and transmit/receive antennas as uniform linear arrays; the downlink OFDM signal simultaneously carries communication transmission and target perception functions, and the received echo signals can be modeled as a three-dimensional tensor form, utilizing CPD decomposition to disassemble into angle factor matrices, distance delay factor matrices, and Doppler velocity factor matrices, each factor matrix naturally possessing a Van der Waals structure.
In the context of non-regular resource scenarios, introducing binary mask tensors to mark the availability / absence of time-frequency resources, and disrupting the low rank structure with damaged echo tensors, is the core starting point for modeling and algorithm design in this paper.
2. Core algorithms: STCD (Structured Tensor Completion and Decomposition)
(1) The foundational framework first proposes Unconstrained Tensor Completion and Decomposition (UTCD), using mask constraints to minimize the error in fitting a distorted tensor; further leveraging the direction matrix's Van Damm properties, introduces Hankel transforms, mapping the Van Damm matrix into the Hankel domain with rank - 1 tensors, constructing an STCD optimization model with rank - 1 structural constraints.
(2) Alternating Minimization AM solver framework introduces an auxiliary variable to decouple the tensor completion and tensor decomposition subproblems, adopting alternating minimization iteration updates:
Utilizing Projection Gradient Descent (PGD) to update the angle and distance factor matrices with respect to the rank - 1 constraints;
Minimizing the closed-form update of coupling factors matrices;
Linear projection to complete the unknown elements of the distorted tensor.
(3) Multi-parameter estimation methods After outputting the factor matrix, combining PUMA, Root-MUSIC, and polynomial root-finding methods, closed-formly solving for the target angle, distance, and velocity from the structured factor matrix.
3. Theoretical analysis (1) CPD (Completeness Condition Reduction) uniqueness condition relaxation utilizes Hankel domain rank - 1 constraints and spatial smoothing techniques to break through the traditional tensor decomposition uniqueness limitations; under non-regular resource scenarios where time-frequency resources are limited and available resources are low, relaxing the CPD rank unique identification upper bound allows for more targets to be distinguished with finite resources.
(2) Non-regular resource CRB lower bound derivation Builds a log likelihood function under non-regular resource masks, derives the Fisher information matrix, obtains the Cramer-Rao lower bounds for angle, delay, Doppler frequency deviation, and maps these to distance and velocity estimation CRB; for the first time, extends the traditional rule resource CRB theory to arbitrary random / block non-regular resource scenarios, providing a theoretical benchmark for algorithm performance.
(3) Structural Initialization and Complexity Analysis
For both fully random and block-random non-regular resource masks, a dual-scenario structural initialization strategy is designed to avoid local optima in non-convex optimization. By comparing the complexity of algorithms such as MUSIC, VCPD, IMDF, UTCD, STCD achieves significant perceptual performance gains with acceptable complexity overhead, and can be extended to uniformly spaced UPA architectures.
4. Benchmarking Method
The comparison includes: 2D-DFT, MUSIC, OMP, IMDF, VCPD, UTCD. Only OMP, UTCD, and STCD can estimate angle-distance-velocity jointly under non-regular resource conditions. Other traditional methods lack parameter estimation or have scene adaptation limitations.
V. Conclusion
1. Algorithm Level: The proposed STCD method for structural tensor completion and decomposition fills in missing time-frequency resources due to non-regularity by means of tensor interpolation, restores the Van dermonde structure of the steering matrix, achieving high-precision joint perception of angle-distance-velocity under ISAC scenarios with irregular resources, breaking through the inherent resolution limits of system bandwidth and coherence interval.
2. Performance Level: Simulation verification shows that STCD has lower estimation RMSE and higher algorithm success rate compared to traditional algorithms under full random and block-random resource masks. It is particularly advantageous in low resource allocation, multi-objective, and low signal-to-noise ratio scenarios, with controllable computational complexity and scalability to complex array configurations like uniformly spaced arrays.
3. Application Value: The proposed STCD method adapts to the irregular temporal-frequency resource characteristics brought about by user random scheduling in actual ISAC systems, directly applicable to engineering scenarios such as 6G mmWave / Terahertz ISAC, low-altitude target detection, and high-precision positioning.

## Images

![Resource-Non-Ruled ISAC System Based on Tensor Decomposition for Object Perception [with MATLAB Code]](01.jpg)
![Resource-Non-Ruled ISAC System Based on Tensor Decomposition for Object Perception [with MATLAB Code]](02.jpg)
![Resource-Non-Ruled ISAC System Based on Tensor Decomposition for Object Perception [with MATLAB Code]](03.jpg)
![Resource-Non-Ruled ISAC System Based on Tensor Decomposition for Object Perception [with MATLAB Code]](04.jpg)
![Resource-Non-Ruled ISAC System Based on Tensor Decomposition for Object Perception [with MATLAB Code]](05.jpg)
![Resource-Non-Ruled ISAC System Based on Tensor Decomposition for Object Perception [with MATLAB Code]](06.jpg)
![Resource-Non-Ruled ISAC System Based on Tensor Decomposition for Object Perception [with MATLAB Code]](07.jpg)
![Resource-Non-Ruled ISAC System Based on Tensor Decomposition for Object Perception [with MATLAB Code]](08.jpg)
![Resource-Non-Ruled ISAC System Based on Tensor Decomposition for Object Perception [with MATLAB Code]](09.jpg)
![Resource-Non-Ruled ISAC System Based on Tensor Decomposition for Object Perception [with MATLAB Code]](10.jpg)
![Resource-Non-Ruled ISAC System Based on Tensor Decomposition for Object Perception [with MATLAB Code]](11.jpg)

<!-- PAYMENT_BLOCK -->

## Get this dataset

- Payment link (Stripe): [Buy now](https://buy.stripe.com/3cs8yP7sY87d0vu9AB)
- Payment QR code: ![Payment QR code](pay.png)

<!-- /PAYMENT_BLOCK -->
