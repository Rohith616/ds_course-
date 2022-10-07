# Decision Tree

Decision Tree is a **Supervised Machine learning algorithm** that can be used for both classification and Regression problems, but mostly it is preferred for solving Classification problems. It is a tree-structured classifier, where **internal nodes represent the features of a dataset, branches represent the decision rules and each leaf node represents the outcome.** 


In a **Decision tree**, there are two nodes, which are the Decision Node and Leaf Node. Decision nodes are used to make any decision and have multiple branches, whereas Leaf nodes are the output of those decisions and do not contain any further branches. It is called a decision tree because, similar to a tree, it starts with the root node, which expands on further branches and constructs a tree-like structure.


- In order to build a tree, we use the **CART (Classification and Regression Tree) algorithm,** which stands for **Classification and Regression Tree algorithm.** 
- A decision tree simply asks a question, and based on the answer **( Yes/No )**, it further split the tree into subtrees.
- Below diagram explains the general structure of a decision tree: 

<img src="https://i.imgur.com/TviJJgY.png" width="650" height="450" style="margin:4% 15% 6% 15%;"> <br>



***
## Why use Decision Tree? 

There are various algorithms in Machine learning, so choosing the best algorithm for the given dataset and problem is the main point to remember while creating a machine learning model. Below are the two reasons for using the Decision tree:

- Decision Trees usually mimic human thinking ability while making a decision, so it is easy to understand.
- The logic behind the decision tree can be easily understood because it shows a tree-like structure. 



## Decision Tree Terminologies
- **Root Node:** Root node is from where the decision tree starts. It represents the entire dataset, which further gets divided into two or more homogeneous sets.
- **Leaf Node:** Leaf nodes are the final output node, and the tree cannot be segregated further after getting a leaf node.
- **Splitting:** Splitting is the process of dividing the decision node/root node into sub-nodes according to the given conditions.
- **Branch/Sub Tree:** A tree formed by splitting the tree.
Pruning: Pruning is the process of removing the unwanted branches from the tree.
- **Parent/Child node:** The root node of the tree is called the parent node, and other nodes are called the child nodes.

## How does the Decision Tree algorithm Work?

In a decision tree, for predicting the class of the given dataset, the algorithm starts from the root node of the tree. This algorithm compares the values of root attribute with the record (real dataset) attribute and, based on the comparison, follows the branch and jumps to the next node.


For the next node, the algorithm again compares the attribute value with the other sub-nodes and move further. It continues the process until it reaches the leaf node of the tree. The complete process can be better understood using the below algorithm:

- **Step-1:** Begin the tree with the root node, says S, which contains the complete dataset.
- **Step-2:** Find the best attribute in the dataset using Attribute Selection Measure (ASM).
- **Step-3:** Divide the S into subsets that contains possible values for the best attributes.
- **Step-4:** Generate the decision tree node, which contains the best attribute.
- **Step-5:** Recursively make new decision trees using the subsets of the dataset created in **step-3**. Continue this process until a stage is reached where you cannot further classify the nodes and called the final node as a leaf node.



**Example:** Suppose there is a candidate who has a job offer and wants to decide whether he should accept the offer or Not. So, to solve this problem, the decision tree starts with the root node (Salary attribute by ASM). The root node splits further into the next decision node (distance from the office) and one leaf node based on the corresponding labels. The next decision node further gets split into one decision node (Cab facility) and one leaf node. Finally, the decision node splits into two leaf nodes (Accepted offers and Declined offer). Consider the below diagram:

<img src="https://i.imgur.com/1LTSr8I.png" width="550" height="300" style="margin:4% 25% 8% 25%;"> <br>


## Attribute Selection Measures 

While implementing a Decision tree, the main issue arises that how to select the best attribute for the root node and for sub-nodes. So, to solve such problems there is a technique which is called as **Attribute selection measure or ASM.** By this measurement, we can easily select the best attribute for the nodes of the tree. There are two popular techniques for ASM, which are:


- **Entropy**
- **Information Gain**
- **Gini Index**

<img src="https://i.imgur.com/Mem9IAX.png" width="1450" > 
<img src="https://i.imgur.com/H4xvXQy.png" width="500" style="margin:6% 25% 0 25%;"> <br>

<img src="https://i.imgur.com/oxF826T.png" width="1450" > 




## Working procedure
    
Using a decision algorithm, we start at the tree root and split the data on the feature that results in the largest **information gain (IG)**.We repeat this splitting procedure at each child node down to the empty leaves. This means that the samples at each node all belong to the same class.

## Advantages of the Decision Tree
   
- It is simple to understand as it follows the same process which a human follow while making any decision in real-life.
- It can be very useful for solving decision-related problems.
- It helps to think about all the possible outcomes for a problem.
- here is less requirement of data cleaning compared to other algorithms.
   
    
## Disadvantages of the Decision Tree

- The decision tree contains lots of layers, which makes it complex.
- It may have an overfitting issue, which can be resolved using the **Random Forest algorithm**.
- There is less requirement of data cleaning compared to other algorithms.


***
## Resources
- Video: [Decision Tree](https://www.youtube.com/watch?v=7VeUPuFGJHk&list=PLblh5JKOoLUICTaGLRoHQDuF_7q2GfuJF&index=38&pbjreload=101) (17 minutes)








