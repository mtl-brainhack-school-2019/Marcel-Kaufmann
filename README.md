# ECG Pupillometry Pipeline
### Brain Hack School 2019 Project by Marcel Kaufmann
---
# Summary

This Brain Hack project is to create a processing pipeline for ECG and pupillometry data. The motivation behind this task is that our lab (MIST Lab @ Polytechnique Montreal) is currently conducting a Human-Robot-Interaction user study in which we collect the following data:
* Pupillometry (Pupil Labs Eye Tracker)

![Eye Tracker Image](img/pupillometer.png)

* Heart rate and RR intervals (Polar 700 fitness tracker)
* ECG, EDA from Biopac (as acq files)
In addition, the idea is to use this pipeline to process signals that have been collected outside our lab. E.g., there is biopac recordings that have been recorded inside of MRI scanners. This data is very noisy, hence looking into different data pre-processing and cleaning techniques can be part of this project, too. 

# Datasets

The data that is going to be processed is unfortunately not openly available due to ethics reasons. It is planned to add a personal or simulated dataset as an example.  

# Tools I plan to use / want to learn

* Docker
* Pandas
* NeuroKit
* Ipython Notebooks

# Planned Deliverable

Ideally, at the end of this project, there will be a dockerized tool to process and visualize the collected and filtered data in *fancy* plots. The docker container could be use as a pure processing pipeline, but can contain a Notebook-Tutorial on how to process the data and use above mentioned tools. If possible, one of the outputs should be cognitive work load so that this data (output) can be used for future projects.



