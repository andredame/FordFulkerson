# Ford-Fulkerson Algorithm

This repository contains my implementation of Ford Fulkerson's algorithm. I created this repository to break down this remarkable algorithm, which has an story behind it. Furthermore, I've come across websites attempting to explain this algorithm that are either incorrect or employ a suboptimal approach. 

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
  <img src="https://github.com/andredame/FordFulkerson/assets/109314147/abf36914-1499-46f0-b295-0add2fe2111e" width="400">
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

Let's find the Maximum flow for the graph bellow:
Just a disclaimer: I've chosen this graph below because I understand the concept what this algorithm does and backtracking edges.It's easy and simple to comprehend.

Let's imagine the graph bellow and we want to know what is the maximum flow where ``T`` is the source and ``S`` is Sink.

<p align="center">
  <img src="https://github.com/andredame/FordFulkerson/assets/109314147/ac75bd5f-f4ed-4d1f-96d5-c2d0f8ab5528" width="400">
</p>




Choosing the path  ``T->A->S`` the minimum capacity is ``10`` so we decrease the value of the capacity.
<p align="center">
  <img src="https://github.com/andredame/FordFulkerson/assets/109314147/231050d7-e056-42c2-ab7d-03fb68174b11" width="400">
</p>



Choosing the path  ``T->B->S`` the minimum capacity is ``10`` so we decrease the value of the capacity.
<p align="center">
  <img src="https://github.com/andredame/FordFulkerson/assets/109314147/2903a2e0-46e5-4962-83ef-0bb361aa671b" width="400">
</p>

As we don't have any path left from our source to sink. We see that the maximum flow is ``20``.

However,something intriguing is happening here, because you could ask what would have happened if we had chosen the path ``T->B->A->S``. And that's the point of this brilliant algorithm.

Let's backtrack and see what would have happened if we had chosen the ``T->B->A->S`` at first.

Choosing the path ``T->B->A->S`` => the minimum capacity is ``10``. Decrease the value's capacity.

<p align="center">
  <img src="https://github.com/andredame/FordFulkerson/assets/109314147/4e600c88-f2e8-4388-8ebd-e5ed4c866392" width="400">
</p>


As you can see there is a huge problem here. There is no path remaining from our source vertex to the target and we found a maximum flow of ``10``.Due to this bad choice that we have chosen, Ford-Fulkerson introduced the concept of backtracking edges for those edges that we have already use. This tackles the bad choice that can be made.



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
