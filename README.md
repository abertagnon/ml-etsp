# ml-etsp (2021)

This repository contains data related to extended version of the paper: *Improving the efficiency of Euclidean TSP solving in Constraint Programming by predicting effective nocrossing constraints* (Elena Bellodi, Alessandro Bertagnon, Marco Gavanelli, Riccardo Zese) submitted for the pubblication in the post-proceedings of AIxIA 2020.

* The `training-instances` directory contains 1536 Euclidean TSP instances, generated in 3 classes (uniform, clustered and morphed) using the generator of the DIMACS challenge ([8th DIMACS Implementation Challenge: The Traveling Salesman Problem](http://dimacs.rutgers.edu/archive/Challenges/TSP/)) and the functions `generateClusteredNetwork`, `morphInstances` from the ([R-package netgen](https://github.com/jakobbossek/netgen)). Each instance is provided in TSPLIB format (.tsp) and in a Prolog-like syntax (.pl). **All these instances have been solved and the collected runtime data have been used to build the `ml-dataset` used to train the Random Forest (RF) and the Multi-Layer Perceptron (MLP) classifiers**.

* The `predicted-instances` directory contains 480 Euclidean TSP instances (different from the ones above), generated in 3 classes (uniform, clustered and morphed). Each instance is provided in TSPLIB format (.tsp) and in a Prolog-like syntax (.pl). 
Each `.pl` file also contains Prolog facts in the form: `nocross(A,B)` that indicate the pairs of nodes on which the nocrossing constraint should be imposed according to the machine learning classifiers. 

    * The `rf` subfolder contains the files in which the nocrossing constraints have been predicted by the Random Forest (RF) classifier and each `.arff` (Attribute Relationship File Format) file contains the features of each constraint ready to be used for classification with ([Weka]( https://www.cs.waikato.ac.nz/ml/weka/)). 

    * The `mlp` subfolder contains the files in which the nocrossing constraints have been predicted by the Multi-Layer Perceptron (MLP) classifier.

* The `result` file contains the detailed results of the experiments presented in the paper.
