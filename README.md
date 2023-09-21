# Persistent Forecast for Cloud Resource Usage
This repository contains the code that tests a cloud resource usage forecasting method based on the insight of data persistence, using timeseries of resource usage from publicly available datasets released by Alibaba, Azure, Google and Bitbrains.

## Repository Structure <br />

* `lstm-experiments.ipynb`: This notebook corresponds to the experiments run for the 2.1 section, Motivational Experiments. The LSTM models used for inference are the ones deployed in the cloud-forecast-lstm repository and can be found here: https://github.com/muse-research-lab/cloud-forecast-lstm. 
We conduct three sets of experiments, that define different test datasets to use during inference over the trained models, where there is one model per job. In more detail:
    * Experiment A defines as test dataset the data used during training, to evaluate the achieved prediction accuracy per model.
    * Experiment B uses as test data the time series of 10 randomly selected tasks of the same job, excluding the training data,running inference with the model corresponding to the same job.
    * Experiment C uses the trained model of the job with identifier 113, to run inference against test data of 10 tasks belonging to the other jobs, namely 374, 399, 917 (x-axis).     
We generate three plots, that correspond to each experiment and capture the resource usage prediction error when using ML models (LSTMs) vs a non-ML prediction. More details on the non-ML prediction can be found in section 2.2 of the paper.

* `insight.ipynb`: This notebook creates the visualisations of a part of the time series of CPU usage (y-axis) across time (x-axis) for job 113, as shown in the Figure 2 of the paper, that allows to better understand the ML-based predictions. The first figure compares the predicted time series to the ground truth and the second with the non-ML prediction. Each box depicts different parts of the time series, where the predicted one is derived following the three different experiments described in the section 2.1 of the paper, using the trained model of job 113 for experiments A, B and job 917 for experiment C. The number on the upper right of each box shows the Pearson correlation coefficient value between the two depicted time series. The LSTM models used for inference are the ones deployed in the cloud-forecast-lstm repository that can be found here: https://github.com/muse-research-lab/cloud-forecast-lstm. 

* `ARD_experiments.ipynb`: In this notebook we define the experiments regarding the degree of data persistency over time across 4 datasets. The details of the datasets and the resource metrics we use can be found in the table below. First, in the Data Processing section, we extract the data for the experiments that follow. In the section Paper Graphs, we plot the Figures 3 and 4 of the paper that capture the cumulative distribution of the average relative delta (ARD) metric per time series and the the average ARD value across all time series of the corresponding resource metric (x-axis) for the Google dataset, respectively. To run this code, it is necessary to install the package gtd that can be found here: https://github.com/muse-research-lab/cloud-traces-comparison, along with instructions for its instalation. <br /> 

* `alibaba/`, `azure/`, `bitbrains/`, `google/`: These folders contain the timeseries of resource usage of the respective datasets that we use for the ARD related experiments.
* `pretrained_lstm_models/`: These folders contain the LSTM models used for inference in the notebooks `lstm-experiments.ipynb` and `insight.ipynb`. These models are trained on the data of the jobs that their respective subfolder name indicates. 

**Table: Cloud resource usage data used in experiments.**  <br />  <br /> 
<img src="docs/images/Cloud Resource Usage Data.png" width="1000"/> 


## Paper Reference <br />
Georgia Christofidi, Konstantinos Papaioannou, and Thaleia Dimitra Doudali. 2023. <br /><br /> Is Machine Learning Necessary for Cloud Resource
Usage Forecasting? <br /><br />  In 14th Symposium on Cloud Computing (ACM SoCC’23), October 30 - November 1, 2023, Santa Cruz, California.  <br /> <br /> 

## Licence <br />
The MIT License (MIT).
 
## Acknowledgements <br />
This work is part of the grant FJC2021-047102-I, funded by MCIN/AEI/10.13039/501100011033 and the European Union «NextGenerationEU»/PRTR.<br />  <br /> 
<img src="docs/images/micin-financiadoUEnextgeneration-prtr-aei-1.png" width="1000"/>
