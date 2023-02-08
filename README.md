# DMOOP_and_DL

## Main idea
This work presents a novel approach for solving Dynamic Multi-Objective Optimisation Problems (DMOOPs) using Deep Learning (DL). Our approach involves training a DL model to predict the Pareto Optimal Set (POS) based on Pareto Set (PS) data obtained from the Dynamic Non-dominated Sorting Genetic Algorithm 2 (DNSGA2) in different DMOOPs benchmarks. We evaluate the performance of our DL model by comparing the results to the DNSGA2 algorithm and quantify the difference using Inverted Generational Distance (IGD), Generational Distance (GD), and Hypervolume (HV) metrics.



## Data Splitting for Model Training and Evaluation

In this study, we aim to split our data into two sets: training and testing. This is done to train and evaluate our models. The split used is 80/20, where 80 percent of the data is designated as the training set (X_General_training) and the remaining 20 percent is designated as the test set (X_General_test).

The training set is further split into two sets, X_train and X_test, which will be used to train our models. After the models are trained, they will be used to predict the POS using the X_General_test set. The metrics IGD, GD, and HV will then be calculated and compared to the results of DNSGA2 in generations 400 to 500.

It's important to note that the same splitting process will be applied to the POS dataset.
