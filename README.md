# Ford-Fulkerson Algorithm

This repository contains my implementation of Ford Fulkerson's algorithm. I created this repository to explains this remarkable algorithm, which has an story behind it. Furthermore, I've come across websites attempting to explain this algorithm that are either incorrect or employ a suboptimal approach.

Ford Fulkerson's algorithm was developed by Lester Randolph Ford, Jr. and Delbert Ray Fulkerson. The algorithm is designed to find the maximum flow in a flow network.

#### A bit of history – it is always good  

  The origin of the interest in maximum flow and minimum cut problems can be traced back to the **Cold War** era. The United States Air Force, particularly concerned about the Soviet Union Railway System, sought to understand the minimum set of railway tracks that, if disrupted, would completely halt movement between the Soviet Union and Eastern Europe during a bombing. This historical context led to the development and study of maximum flow and minimum cut problems, offering a mathematical framework for optimizing the disruption of transportation networks during conflicts. These algorithms have since found applications beyond military contexts in various fields, such as transportation and communication networks.
#### Problem
Formulated by T.E. Harris ([Schrijver, 2002](https://homepages.cwi.nl/~lex/files/histtrpclean.pdf)), the problem is as follows: 

`Consider a rail network connecting two cities by way of a number of intermediate cities, where each link of the network has a number assigned to it representing its capacity.
Assuming a steady state condition, find a maximal flow from one given city to the other.
`

Visualized in the figure below are the vertices (cities) and their interconnections, each marked with its respective edge capacity.

`
What is the maximum flow that we can send from Madrid to Warsaw?
`
<p align="center">
  <img src="https://github.com/andredame/FordFulkerson/assets/109314147/b4acd52f-f893-4710-878d-5e5d1740ec7b" width="400">
</p>

###


### Solution

1. **Start with an initial flow of 0.**

2. **While there's a way to increase the flow from the source to the sink:**

   - Look for a path from the source to the sink using any method (``Depth first Search`` ``Breadth First Search``).

   - Determine how much more flow can be sent along this path. It's going to be the minimum capacity of the path.

   - Increase the flow along the path by this amount.

3. **Repeat step 2 until you can't find any more ways to increase the flow.**

4. **Return the maximum flow achieved.**

``Let's find Maximum flow for the graph above:

Initiate each edge with ``0 flow``.

Find a Path from ``Madrid`` to ``Warsaw`` ==========> ``Madrid`` -> ``London`` -> ``Hamburg`` -> ``Warsaw`` ``Warsaw``. Find the minimum capacity along these edges, which is **2** from ``Hamburg`` -> ``Warsaw``.
Update the values of each edge by decrementing the capacity according to the flow.


``








<p align="center">
  <img src="https://github.com/andredame/FordFulkerson/assets/109314147/ae32d178-abe0-42bf-b91b-e605abe7ef24" width="400">
</p>

### References
For more in-depth information on the history of transportation and maximum flow problems, you can refer to the following source:
- [Schrijver, Alexander. "On the history of the transportation and maximum flow problems." Mathematical Programming 91.3 (2002): 437-445.](https://homepages.cwi.nl/~lex/files/histtrpclean.pdf)
