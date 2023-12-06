<div align="center">
  
# Facebook Social Network Analysis

</div>

## I. Introduction

When analyzing different complex networks, it may be important
to discover communities inside them. Community detection methods 
are useful for social media algorithms to discover people with 
common interests and keep them tightly connected. Community detection
can be used in machine learning to detect groups with similar properties
and extract groups for various reasons, as well as identifying the most 
important and influential nodes.
The project divided into two tasks, determination of the top-k influential
nodes and community partition. For that, we can perform them on Facebook 
Dataset available in [[2]](#resources).


## II. Identifying influential nodes

### 1. **TOPSIS** method implementation [[2, 3]](#papers-used)

**TOPSIS**, which stands for Technique for Order of Preference by Similarity to Ideal Solution, is a multi-criteria decision analysis method used to determine the best alternative from a set of alternatives.   It was introduced by Hwang and Yoon in 1981. **TOPSIS** is widely used in fields such as operations research, management, engineering, and other areas where decision-making involves evaluating multiple criteria.
The **TOPSIS** method can be applied to identify influential nodes within complex networks by utilizing a decision matrix [[2]](#papers-used). In this matrix, the number of rows corresponds to the number of nodes, and four columns represent distinct centrality measures: BC (Betweenness Centrality), CC(Closeness Centrality), EC(Eigenvector Centrality) and DC(Degree Centrality).

![image](https://github.com/hassanInfo/Facebook_Social_Network_Analysis/assets/85229840/19d1914b-d8ea-455e-b174-2392088daaf7) 

### 2. Network Visualization

To comprehend our network, it's essential to visualize the nodes and edges in a standard display or presentation.

### 2.1. Normal display

![image](https://github.com/hassanInfo/Facebook_Social_Network_Analysis/assets/85229840/0aac37ba-c31e-4c6a-95de-867a260d9290)

### 2.2. K-cores visualization

![image](https://github.com/hassanInfo/Facebook_Social_Network_Analysis/assets/85229840/8869bc3a-56e2-4403-8e3d-045af988ccf4)

### 2.3. Visualization by DC as a creterion of node importance

![image](https://github.com/hassanInfo/Facebook_Social_Network_Analysis/assets/85229840/d4c473e5-0bbf-4713-a0a6-a04a3145fbee)

### 2.4. Visualization by BC as a creterion of node importance

![image](https://github.com/hassanInfo/Facebook_Social_Network_Analysis/assets/85229840/f150f19d-f571-4ad7-8f00-67b6abdd9daa)

### 2.5. Visualization by CC as a creterion of node importance

![image](https://github.com/hassanInfo/Facebook_Social_Network_Analysis/assets/85229840/182d082f-1448-4859-9408-d4b5c4207a5a)

### 2.6. Visualization by EC as a creterion of node importance

![image](https://github.com/hassanInfo/Facebook_Social_Network_Analysis/assets/85229840/cb50bf28-d986-4c32-809c-084e4cb66288)

### 2.7. Identifying the top k nodes by using **TOPSIS** Method

![image](https://github.com/hassanInfo/Facebook_Social_Network_Analysis/assets/85229840/f5381886-a14e-40fb-9ffc-d0b9e0837947)

### 3. **TOPSIS** effectivenss

### 3.1. ***SIR/SIS*** and ***SI*** model

The ***SIR*** (Susceptible-Infectious-Recovered), ***SIS*** (Susceptible-Infectious-Susceptible), and ***SI*** (Susceptible-Infectious) models are compartmental models commonly used in epidemiology to simulate the spread of infectious diseases within a population. These models categorize individuals into different compartments based on their disease status. The model consists of three compartments:<br>
***S***: The number of susceptible individuals.<br>
***I***: The number of infectious individuals.<br>
***R***: for the number of removed (and immune) or deceased individuals.<br>
This model can be expressed by the following system of ordinary differential equations:<br>

![image](https://github.com/hassanInfo/Facebook_Social_Network_Analysis/assets/85229840/916cfe0e-7e20-4eee-a71b-26d187ca076d)

Where ***N*** is number of nodes in the network. The ***SIS*** model that is a variation on the basic ***SIR*** model, in which an infected node can be Susceptible with some probability.

![image](https://github.com/hassanInfo/Facebook_Social_Network_Analysis/assets/85229840/0e47de79-1f74-4afd-819e-f0767d50f37d)

### 3.2. Simulation

To gain insights into the relationship among the top-k influential nodes (where ***k***=10) and to visualize the spreading process within our graph network, we employ the ***SI*** model. The figure illustrates various snapshots captured at each time step, providing a depiction of how the spreading process unfolds.

![image](https://github.com/hassanInfo/Facebook_Social_Network_Analysis/assets/85229840/5fdd12ad-fccb-4132-b08b-e7500fef899d)

![image](https://github.com/hassanInfo/Facebook_Social_Network_Analysis/assets/85229840/fe480ea0-289c-4f83-8dac-c2c19be139f3)

![image](https://github.com/hassanInfo/Facebook_Social_Network_Analysis/assets/85229840/0a4fd20d-ceaa-431f-a242-6859a548278f)

![image](https://github.com/hassanInfo/Facebook_Social_Network_Analysis/assets/85229840/e6b76054-4f1f-4d40-b66c-b65d8d4a532c)

![image](https://github.com/hassanInfo/Facebook_Social_Network_Analysis/assets/85229840/bd9ace14-2da6-45fe-877f-398feff6dd1e)

We assess the influence of nodes present in either the top-10 list generated by our proposed method or three other centrality measures. It's important to highlight that by excluding the impact of common nodes in both ranking lists, we can effectively distinguish the differences between these methods. The simulations focus on the cumulative infected nodes, denoted as ***F(t)***. The count of cumulative infected nodes grows over time, ultimately reaching a stable value.
As observed in the table below on the left, both the Betweenness Centrality (BC) and **TOPSIS** methods yield identical elements, with only two ranked elements (1821 and 352, 571 and 0) differing between the methods. To validate the accuracy of the **TOPSIS** method's ranked list, we conducted simulations of disease spread using the Susceptible-Infectious (***SI***) model. We initiated the infected nodes based on Betweenness Centrality with [1821, 571] and, alternatively, with the proposed method's list initialization of [352, 0]. The experimental results, depicted in the figure below on the right, illustrate that ***F(t)***, the cumulative number of infected nodes, is notably higher for the **TOPSIS** method compared to the BC-based rank list, indicating a more significant spread in the former method.

![image](https://github.com/hassanInfo/Facebook_Social_Network_Analysis/assets/85229840/4a213be2-aacb-4282-ae6f-fe45ceefc76b)

We replicate the identical procedure for the remaining comparisons, showcasing the effectiveness of the **TOPSIS** method:

![image](https://github.com/hassanInfo/Facebook_Social_Network_Analysis/assets/85229840/4cb93baa-6d15-4a3f-9778-40580674b0eb)

## III. Community detection

In this project phase, we employed the **KMeans** algorithm trained on the decision matrix obtained through **TOPSIS**. The algorithm was initialized with centroids determined by the top-10 influential nodes identified earlier to detect partitions. The PCA results are illustrated in the following figure.

![image](https://github.com/hassanInfo/Facebook_Social_Network_Analysis/assets/85229840/1673a670-780b-4405-979f-8e8c0f4b61e4)

## IV. Resources
[1] [Facebook Dataset](https://snap.stanford.edu/data/ego-Facebook.html)

[2] [Du, Yuxian, et al. "A new method of identifying influential nodes in complex networks based on TOPSIS." Physica A: Statistical Mechanics and its Applications 399 (2014): 57-69.](https://github.com/hassanInfo/Facebook-Social-Network-Analysis/files/9278203/1-s2.0-S0378437113011552-main.pdf)

[3] [Hu, Jiantao, et al. "A modified weighted TOPSIS to identify influential nodes in complex networks." Physica A: Statistical Mechanics and its Applications 444 (2016): 73-85.](https://github.com/hassanInfo/Facebook-Social-Network-Analysis/files/9278205/1-s2.0-S0378437115007554-main.pdf)
