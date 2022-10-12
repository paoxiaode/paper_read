# Where2comm: Communication-Efficient Collaborative Perception via Spatial Confidence Maps



## Intro

Task: Multi-agent collaborative perception

Scenarios: 

* vehicle-to-everything-communication-aided autonomous driving 
* multirobot warehouse automation system
* multi-UAVs (unmanned aerial vehicles) for search and rescue.

Current challenge: how to optimize the trade-off between perception performance and communication bandwidth.

![image-20220927225259317](./assets/image-20220927225259317.png)

The core idea is to enable a **spatial confidence map** for each agent, where each element reflects the perceptually critical level of a corresponding spatial area

Three key module:

* A spatial confidence generator
  * produce spatial confidence map
* A spatial confidence-aware communication module
  * where and who to communicate
* A spatial confidence-aware message fusion module
  * fuses messages received from other agents



## Formulation

Objective: achieve the maximized perception performance of all agents as a function of the total communication budge $B$ and communication round $K$

![image-20220927230147401](./assets/image-20220927230147401.png)

* $g$ perception evaluation metric
* $\Phi$ perception network
* $P_{i\rightarrow j}^{(k)}$: the message transmitted from the $i$ th agent to the $j$ th agent at the $k$ th communication round

consider the perception task of 3D object detection and present three contributions: 

* communication more efficient by designing compact messages and sparse communication graphs;
* boost the perception performance by implementing more comprehensive message fusion;
* enable the overall system to adapt to varying communication conditions by dynamically adjusting where and who to communicate.



## Module

![image-20220927231133612](./assets/image-20220927231133612.png)

Module includes: observation encoder, a spatial confidence generator, the spatial confidence-aware communication module, the spatial confidence-aware message fusion module and a detection decoder



### Observation encoder

![image-20220927232426226](./assets/image-20220927232426226.png)

$H,W,D$: height, width, channel



### Spatial confidence generator

the area with high perceptually critical level $\Rightarrow$ a high confidence score.

![image-20220927232243959](./assets/image-20220927232243959.png)

generate map from feature map $F$



### Spatial confidence-aware communication

#### Massage packing

consider two areas

* low confidence score
  * no objects or something missing 
  * indicates there could be missing information at that location.
* high confidence score

Define the request map: 

![image-20220927233121076](./assets/image-20220927233121076.png)

![image-20220927233150358](./assets/image-20220927233150358.png)

* $\odot$ element-wise multiple
* why element-wise multiple?
  * R: the lost information in previous round, C: the important area in current round 



Define the selected feature map:

![image-20220928102123364](./assets/image-20220928102123364.png)

Define the message transmitted from the $i$ th agent to the $j$ th agent at the $k$ th communication round: 

<img src="./assets/image-20220928102301293.png" alt="image-20220928102301293" style="zoom:50%;" />

* $R^{(k)}_i$ provides spatial priors to request **complementary information** for the $i$ th agent’s need in the next round; 

* $Z_{i\rightarrow j}^{(k)}$ provides supportive information for the $i$ th agent’s need in the this round. 



#### Communication graph construction

The necessity of communication between the $i$ th and the $j$ th agents:  the overlap between the information that the $i$ th agent has and the information that the $j$ th agent needs.

$A^{(k)}$: the adjacency matrix of communication graph (**if agent $i$ and $j$ communicate**)

![image-20220928104114378](./assets/image-20220928104114378.png)



### Spatial confidence-aware message fusion