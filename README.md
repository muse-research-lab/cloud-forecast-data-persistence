# Cloud Resource Forecast using a method based on data persistence
This repository contains the code that tests a cloud resource usage forecasting method based on the insight of data persistence, using timeseries of resource usage from publicly available datasets released by Alibaba, Azure, Google and Bitbrains.

## Repository Structure <br />

* lstm-experiments.ipynb: This notebook corresponds to the experiments run for the 2.1 section, Motivational Experiments. The LSTM models used for inference are the ones deployed in the cloud-forecast-lstm repository that can be found here: https://github.com/muse-research-lab/cloud-forecast-lstm. 
We conduct three sets of experiments, that define different test datasets to use during inference over the trained models, where there is one model per job. In more detail:
• Experiment A defines as test dataset the data used during training, to evaluate the achieved prediction accuracy per model.
• Experiment B uses as test data the time series of 10 randomly selected tasks of the same job, excluding the training data,running inference with the model corresponding to the same job.
• Experiment C uses the trained model of the job with identifier 113, to run inference against test data of 10 tasks belonging to the other jobs, namely 374, 399, 917 (x-axis).
We generate three plots, that correspond to each experiment and capture the resource usage prediction error when using ML models (LSTMs) vs a non-ML prediction. More details on the non-ML prediction can be found in section 2.2 of the paper.

*




## Paper Reference <br />
Georgia Christofidi, Konstantinos Papaioannou, and Thaleia Dimitra Doudali. 2023. <br /><br /> Is Machine Learning Necessary for Cloud Resource
Usage Forecasting? <br /><br />  In 14th Symposium on Cloud Computing (ACM SoCC’23), October 30 - November 1, 2023, Santa Cruz, California.  <br /> <br /> 

## Licence <br />
The MIT License (MIT)
 
## Acknowledgements <br />
This work is part of the grant FJC2021-047102-I, funded by MCIN/AEI/10.13039/501100011033 and the European Union «NextGenerationEU»/PRTR.<br /> 
<img src="docs/images/micin-financiadoUEnextgeneration-prtr-aei-1.png" width="1000"/>
