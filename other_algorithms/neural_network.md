# Artificial Neural Networks

Artificial Neural Networks are Machine Learning algorithms that work by mimicing neurons in the brain and have a long history. The first mimicked neuron was created in 1943 using circuits by Warren McCulloch and Walter Pitts. In 1959, Bernard Widrow and Marcian Hoff created a neural network to eliminate echoes on phone lines! These days, neural networks are famous for their use to read numbers in photographs.

In order to understand what is going on in a neural network, we will take a look at actual neurons in the brain.

The basic building block of the neural network is a **neuron** or node. They are connected to other neurons through weight connections.

The neural network uses a graph data structure to build out. However, a neural network borrows the idea of **layers** from the tree data structure. Nodes in a give layer can only be attached to nodes in the layer preceding or succeeding them. Below is an example of a neural network.

![Neural Network]()

The layers are split up into three different groups. The first layer group contains a single layer and is called the **input layer**. These are the nodes that take in the input of whatever you are trying to solve. The next layer group is the **hidden layers** group. It contains one or more layers of nodes that do the calculations of the neural network. They are called hidden because the user never interacts with them. The finaly layer group is a single layer and is called the **output layer**. This layer contains all of the nodes that the output the result of the neural network.

The neural network makes decisions using a process called **forward propagation**. This process takes the inputs from the input layer, does all of the computations in the hidden layer and then outputs the results through the output layer. We will start with a simple neural network to see how this occurs.

![Simple NN]()

Our neural network above has 3 neurons. The neuron on the left is the input neuron and resides in the input layer. The middle neuron does computing and is part of the hidden layer. The right neuron is the output neuron and is part of the output layer. Our goal is to get a neural network that takes a single input and outputs true if our input is positive and false if our input is negative.

