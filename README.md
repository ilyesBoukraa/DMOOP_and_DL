# DMOOP_and_DL

## Main idea
This work presents a novel approach for solving Dynamic Multi-Objective Optimisation Problems (DMOOPs) using Deep Learning (DL). Our approach involves training a DL model to predict the Pareto Optimal Set (POS) based on Pareto Set (PS) data obtained from the Dynamic Non-dominated Sorting Genetic Algorithm 2 (DNSGA2) in different DMOOPs benchmarks. We evaluate the performance of our DL model by comparing the results to the DNSGA2 algorithm and quantify the difference using Inverted Generational Distance (IGD), Generational Distance (GD), and Hypervolume (HV) metrics.

## Data Splitting for Model Training and Evaluation

In this study, we aim to split our data into two sets: training and testing. This is done to train and evaluate our models. The split used is 80/20, where 80 percent of the data is designated as the training set (data_general_training) and the remaining 20 percent is designated as the test set (data_general_testing).

The training set is further split into two sets, X_train and X_test, which will be used to train our models. After the models are trained, they will be used to predict the POS using the data_general_test set. The metrics IGD, GD, and HV will then be calculated and compared to the results of DNSGA2 in generations 400 to 500.

It's important to note that the same splitting process will be applied to the POS dataset.

## build_datasets-v1 Notebook
In this notebook we obtain our PSs and POSs from each benchmark (DF1 to DF14) then save it as a csv file(ex: /PS/ps_DF_1.csv, /PS/ps_DF_2.csv, /POS/pos_DF_1.csv and /POS/pos_DF_2.csv).

## Build_X_Y_For_Training_Later_v1 notebook
In this notebook, we first conduct a simple exploratory data analysis to gain a better understanding of the data we are working with. We have selected one benchmark randomly for this analysis, but the same steps will be applied to all benchmarks.

To further evaluate our models, we split the data into a training set and a test set using a 80/20 percent split. The training set, designated as data_general_training, consists of the first 400 generations (500 * 0.8 = 400) and will be used to train our models. The remaining 100 generations will be used for evaluation purposes.

In our analysis, we gather data from five generations in each sample, assuming that each generation has some relation with the next ones. This number, five, was chosen arbitrarily(at the moment). The gathered data is then saved as numpy arrays (e.g. x.npy, y.npy).

## Build_Model_Train_X_Y_v1 notebook
In this notebook, we have loaded the X and Y data which was previously gathered from the "Build_X_Y_For_Training_Later_v1" notebook. Our goal is to train the data using three different techniques: Recurrent Neural Network (RNN), Long-Short-Term Memory (LSTM), and Gated Recurrent Unit (GRU). The hyperparameters have been selected through our own experimentation, though we have not yet utilized grid search to test all possible combinations. Our focus will be on observing the losses and their respective curves to check for overfitting, allowing us to make necessary adjustments to the models.

### Our Models and there respictive Loss curves
![RNN](DMOOP_and_DL/performance/RNN_model_loss_70_30.png)

![LSTM](DMOOP_and_DL/performance/LSTM_model_loss_70_30.png)
![GRU](DMOOP_and_DL/performance/GRU_model_loss_70_30.png)
