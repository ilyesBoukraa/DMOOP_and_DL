# DMOOP_and_DL

## Main idea
This work presents a novel approach for solving Dynamic Multi-Objective Optimisation Problems (DMOOPs) using Deep Learning (DL). Our approach involves training a DL model to predict the Pareto Optimal Set (POS) based on Pareto Set (PS) data obtained from the Dynamic Non-dominated Sorting Genetic Algorithm 2 (DNSGA2) in different DMOOPs benchmarks. We evaluate the performance of our DL model by comparing the results to the DNSGA2 algorithm and quantify the difference using Inverted Generational Distance (IGD), Generational Distance (GD).

## Data Splitting for Model Training and Evaluation

In this study, we aim to split our data into two sets: training and testing. This is done to train and evaluate our models. The split used is 80/20, where 80 percent of the data is designated as the training set (data_general_training) and the remaining 20 percent is designated as the test set (data_general_testing).

The training set is further split into two sets, X_train and X_test, which will be used to train our models. After the models are trained, they will be used to predict the POS using the data_general_test set. The metrics IGD and GD will then be calculated and compared to the results of DNSGA2 in generations 400 to 500.

It's important to note that the same splitting process will be applied to the POS dataset.

## build_datasets-v1 Notebook
In this notebook we obtain our PSs and POSs from each benchmark (DF1 to DF14) then save it as a csv file(ex: /PS/ps_DF_1.csv, /PS/ps_DF_2.csv, /POS/pos_DF_1.csv and /POS/pos_DF_2.csv).

Note** the use of zero-padding in order to make every POSs (generated by DNSGA2) of every benchmark have the same size is a common solution to address variable-length data in some applications. However, we alredy implemented a better solution that will get commited later on.

## Build_X_Y_For_Training_Later_v1 notebook
In this notebook, we first conduct a simple exploratory data analysis to gain a better understanding of the data we are working with. We have selected one benchmark randomly for this analysis, but the same steps will be applied to all benchmarks.

To further evaluate our models, we split the data into a training set and a test set using a 80/20 percent split. The training set, designated as data_general_training, consists of the first 400 generations (500 * 0.8 = 400) and will be used to train our models. The remaining 100 generations will be used for evaluation purposes.

In our analysis, we gather data from five generations in each sample, assuming that each generation has some relation with the next ones. This number, five, was chosen arbitrarily(at the moment). The gathered data is then saved as numpy arrays (e.g. x.npy, y.npy).

## Build_Model_Train_X_Y_v1 notebook
In this notebook, we have loaded the X and Y data which was previously gathered from the "Build_X_Y_For_Training_Later_v1" notebook, then we split the data into a training and testing sets with 60/40 percent split. Our goal is to train the data using three different techniques: Recurrent Neural Network (RNN), Long-Short-Term Memory (LSTM), and Gated Recurrent Unit (GRU). The hyperparameters have been selected through our own experimentation, though we have not yet utilized grid search to test all possible combinations. Our focus will be on observing the losses and their respective curves to check for overfitting, allowing us to make necessary adjustments to the models.

### Model Performance through Examination of the Respective Loss Curves(Performance and Overfitting).
![RNN_model_loss_70_30](https://github.com/ilyesBoukraa/DMOOP_and_DL/blob/main/performance/RNN_model_loss_60_40_5_gen.png)
![LSTM](https://github.com/ilyesBoukraa/DMOOP_and_DL/blob/main/performance/LSTM_model_loss_60_40_5_gen.png)
![GRU](https://github.com/ilyesBoukraa/DMOOP_and_DL/blob/main/performance/GRU_model_loss_60_40_5_gen.png)

## Evaluating_Our_Models notebook.
In this notebook, we are loading and evaluating our previously trained models on the data_General_testing set. During the training process, we trained our models on 80% of the 500 generations, which is 400 generations, and now we are using the remaining 100 generations to assess our models based on DMOOPS metrics.

To visualize the Inverted Generational Distance (IGD) with respect to the number of generations, we first obtained the real Pareto Front (referenced_PF) from our Problem Class. This was done in the 'build_datasets-v1' notebook in order to ensure that the tau values were the same for all models. Next, we obtained the models' outputs (POS) and used the _evaluate function to calculate the POFs from the POSs. Then, we calculated the IGD value for each generation and plotted the results for comparison.

# Conclusion
In conclusion, the comparison of our models with DNSGA2 in DF10 benchmark highlights the necessity for further refinement or the consideration of alternative DEep Learning models. The results suggest that there is potential for improvement and the challenging task of enhancing our models adds to the motivation to continue striving for better outcomes. This iteration is just the starting point, and the implementation of other techniques that may result in improved performance has yet to be pursued. Nevertheless, the encouraging results merit further examination and investigation.

Note that: the results from other benchmarks will be submitted later on.
