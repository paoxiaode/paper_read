# Graph Neural Networks: Foundations, Frontiers, Applications

[TOC]

## Graph Generation & Transformation

### Graph Generation

Application:

![image-20220920110245376](./assets/image-20220920110245376.png)

Two main methods: 

* One-shot generation
* Sequential generation

<img src="./assets/image-20220920110406463.png" alt="image-20220920110406463" style="zoom: 67%;" />

#### GraphVAE(One-shot generation)

<img src="./assets/image-20220920110449985.png" alt="image-20220920110449985" style="zoom: 67%;" />

* Encoder: GNN graph to vector 

* Decoder(generator): MLP vector to A E F (graph)

### Graph Translation

#### GT-GAN

GT-GANs learn a conditional generative model, which is a graph translator that is conditioned on input graph and generate the associated target graph.

Aim at translating a graph with one modality to a new one with other modality using deep neural networks architecture. Eg: Examples include generating the traffic jam situation given a road network without traffic jam.

![image-20220920110716974](./assets/image-20220920110716974.png)

* Graph translator
  * Encoder + decoder 
* Conditional graph discriminator

### Benchmark dataset

#### GraphGT

![image-20220920112505346](./assets/image-20220920112505346.png)

### Future Opportunities

* Scalability.
* Validity constraint
* Interpretability and Controllability.

## Dynamic Graph

### Two dynamic graph types (diff?)

![image-20220920115034597](./assets/image-20220920115034597.png)



Operations of graph dynamics:
- Node addition/deletion
- Feature update
- edge addition/deletion
- edge weight updates

### Task types

-  Dynamic Node classification/regression
-  Dynamic graph classification
-  Dynamic link prediction
-  Time prediction



### RNN-GNN(TGN)

<img src="./assets/image-20220921104506062.png" alt="image-20220921104506062" style="zoom:67%;" />

TGN network arch

![image-20220921104636655](./assets/image-20220921104636655.png)

#### Future directions

-  Node addition and removal are still challenges.
-  Inverse problem of graph dynamics
-  Spatiotemporal
