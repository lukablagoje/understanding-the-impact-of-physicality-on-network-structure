# The Impact of Physicality on Network Structure
This project is a part of the published research work "The Impact of Physicality on Network Structure", done in the emerging field of Physical Networks, which aims to understand the properties of three-dimensional networked systems (such as biological neural networks).

In this paper, a linear physical network model is introduced, along with the collision-avoiding representation graph, called a "metagraph" representation (if two edges collide physically, they share an edge in this metagraph). The concept of "generalized meta-graph" is introduced as well, which can be applied to empirical data, by encoding information on Euclidean distances between neighboring edges.

In my contribution to this project, I applied this new representation to efficiently solve a computationally challenging task: finding out how many unique neuron-to-neuron physical collisions are obtained if the thickness of the neurons is increased for 20 different additive factors. In our dataset, we had around 3000 neurons composed of more than 10^6 segments, thus, the goal was to find which labels of the segments are in collision. The results of this analysis have shown that biological neural networks are composed of highly confined objects, which have many neighbors in their local physical neighborhood, which cannot be said for mitochondrial, vascular, and plant root networks.
I further developed the representation for each individual neuron and its physical confinement (meta-degree), for a very small additive factor - there's initially no collisions, but with a small increase in thickness, this changes, as shown in the Figure below:
<img src="https://github.com/lukablagoje/the-impact-of-physicality-on-network-structure/assets/52599010/8b707c1b-eb95-453d-beaf-e965fe443869" width="750">

Figure: a) Meta-graph representation b) Neurons in their spatial environment (each color a neuron) c) Places where of the minimum neuron-to-neuron distance, thus after thickness increase, they would collide here d) Meta-graph degree distribution for a small thickness increase e) Relationship between the synaptic connections and the meta-degree.

If you want to read more about this research, please check out the links below:

Publication link: [https://www.nature.com/articles/s41567-023-02267-1](https://www.nature.com/articles/s41567-023-02267-1)

arXiv link: [https://arxiv.org/abs/2211.13265](https://arxiv.org/abs/2211.13265)

# Technical project overview
My technical contribution to this project is divided into three conceptually different parts:

[**1. obtain_neuron_skeletons.ipynb**](https://github.com/lukablagoje/the-impact-of-physicality-on-network-structure/blob/main/1.%20obtain_neuron_skeletons.ipynb) - Accessing and downloaded the neuron skeleton data, which was further processed to obtain a dataset composed only of points (point clouds).

[**2. creating_querying_labeled_kd_trees**](https://github.com/lukablagoje/the-impact-of-physicality-on-network-structure/blob/main/2.%20creating_querying_labeled_kd_trees.ipynb) - Developing an algorithm that creates a labeled point cloud, which is stored in the k-d tree, allowing for efficient search of spatial neighbors, with labeling included (as scipy.spatial k-d trees work with unlabeled points).

[**3. weighted_metagraph_results**](https://github.com/lukablagoje/understanding-the-impact-of-physicality-on-network-structure/blob/main/3.%20weighted_metagraph_results.ipynb) - Applying the labeled point cloud algorithm to find the number of physically close neurons (objects) as their radial thickness is increased, both for individual neurons and all neurons in the dataset at once.

# Data
[**neuron_regions_information**](https://github.com/lukablagoje/the-impact-of-physicality-on-network-structure/tree/main/neuron_regions_information) - Folder for storing information about the neurons in specific regions, which are in CSV format.

[**neuron_regions_points**](https://github.com/lukablagoje/the-impact-of-physicality-on-network-structure/tree/main/neuron_regions_points) - Folder for storing point clouds of neuron data, which are in CSV format.

[**querying results**](https://github.com/lukablagoje/the-impact-of-physicality-on-network-structure/tree/main/querying_results) - Folder for storing labeled kd-tree results, which are in pickle format (the number in the filename represents querying radius)

To access the original dataset, you will need to use the Python library provided by the Janelia project, which you can install from: https://pypi.org/project/neuprint-python/

If you want to understand this library more, you can read through their documentation: https://connectome-neuprint.github.io/neuprint-python/docs/index.html

