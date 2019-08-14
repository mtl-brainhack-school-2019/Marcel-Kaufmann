# ECG Pupillometry Pipeline
### Brain Hack School 2019 Project by Marcel Kaufmann
---
# Summary

This Brain Hack project is to create a processing pipeline for ECG and pupillometry data. The motivation behind this task is that our lab ([MIST Lab @ Polytechnique Montreal](https://mistlab.ca)) is currently conducting a Human-Robot-Interaction user study in which we collect the following data:
* Pupillometry (Pupil Labs Eye Tracker)

<img src="img/pupillometer.png" width=353)> <img src="img/eye.png" width=300)>

* Heart rate and RR intervals (Polar H7 fitness tracker)

![Polar HR Monitor](https://www.polar.com/sites/default/files/product/main_images/h7_heart_rate_sensor2_main_action_30.jpg)

* ECG, EDA from Biopac (as acq files)
<div style="display: flex; justify-content: center;">
<img src="https://www.biopac.com/wp-content/uploads/bsladv-300x300.jpg")>
</div>

The collection pipeline has been established using ROS (the robot operating system) and biopac data is manually recorded for each participant. The analysis pipeline does not exist and synchronization/merging of data collected in ROS and via the Biopac software has yet to be implemented.

In addition, the idea is to use this pipeline to process signals that have been collected outside of our lab. E.g., there is Biopac recordings that have been recorded inside of MRI scanners. This data is very noisy, hence looking into different data pre-processing and cleaning techniques can be part of this project, too. 

# Datasets

The data that is going to be processed is unfortunately not openly available due to ethics reasons. It is planned to add a personal or simulated dataset as an example.


# Tools I plan to use / want to learn

* <img src="https://upload.wikimedia.org/wikipedia/en/c/cd/Anaconda_Logo.png" width="80" alt="Anaconda">
* <img src="https://www.docker.com/sites/default/files/d8/styles/role_icon/public/2019-07/vertical-logo-monochromatic.png?itok=erja9lKc" width="80" alt="Docker">
* Pandas
* NeuroKit
* Ipython Notebooks

# Planned Deliverables

Ideally, at the end of this project, there will be a dockerized tool to process and visualize the collected and filtered data in *fancy* plots. The docker container could be use as a pure processing pipeline, but can contain a Notebook-Tutorial on how to process the data and use above mentioned tools. If possible, one of the outputs should be cognitive work load so that this data (output) can be used for future projects.

# Planned Outputs
* Heart Rate Variability
* De-noised ECG
* Cognitive Workload Measurement



