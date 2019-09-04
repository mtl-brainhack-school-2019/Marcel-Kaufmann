## ECG Pupillometry Pipeline
### Brain Hack School 2019 Project by Marcel Kaufmann
---
# Video Introduction to this Brain Hack Project

[![](http://img.youtube.com/vi/8ZVCNeX42_A/0.jpg)](http://www.youtube.com/watch/8ZVCNeX42_A "")
(Click on image to play)

# Summary

This Brain Hack project is about creating a processing pipeline for ECG and pupillometry data. The motivation behind this task is that our lab ([MIST Lab @ Polytechnique Montreal](https://mistlab.ca)) is currently conducting a Human-Robot-Interaction user study in which we collect the following data:
* Pupillometry (Pupil Labs Eye Tracker)

<img src="img/pupillometer.png" width=353)> <img src="img/eye.png" width=300)>

* Heart rate and RR intervals (Polar H7 fitness tracker)

![Polar HR Monitor](https://www.polar.com/sites/default/files/product/main_images/h7_heart_rate_sensor2_main_action_30.jpg)

* ECG, EDA from Biopac (as acq files)
<div style="display: flex; justify-content: center;">
<img src="https://www.biopac.com/wp-content/uploads/bsladv-300x300.jpg")>
</div>

The collection pipeline has been established using ROS (the robot operating system), while the data from the biopac sensors is recorded manually for each participant. An analysis pipeline did not exist and the synchronization/merging of the collected data had not been implemented before Brain Hack.

In addition, this pipeline could be used to process signals that have been collected outside of our lab. E.g., there is Biopac recordings that have been recorded inside of MRI scanners. This data is very noisy and could possibly be filtered based on the code base of this project.

# Project Definition and Overview

To further define the project, the following figure shows a project overview:
Starting point is the different data streams that exist in either a ROSbag or text (csv) format. The ROSbag has been decoded in a pre-processing step (https://github.com/mtl-brainhack-school-2019/ecg_pupillometry_pipeline_kaufmann/blob/master/pre-processing/bag_to_csv.py), so that for this project the data can be imported into the jupyter notebooks easily.

![Overview](./img/overview.png )

#### Planned Deliverables

Ideally, at the end of this project, there will be a dockerized tool to process and visualize the collected and filtered data in *fancy* plots. The docker container could be use as a pure processing pipeline, but can contain a Notebook-Tutorial on how to process the data and use above mentioned tools. If possible, one of the outputs should be cognitive work load so that this data (output) can be used for future projects.

#### Datasets

The data that is going to be processed is unfortunately not openly available due to ethics reasons. A personal sample dataset has been added as an example of what the collected data can look like. Different experiment conditions are not reflected.

# Project Progress and Learning Experience

The project allowed me to learn about containerization with docker and exposed me extensively to Jupyter Notebooks. There is different ways to manage ones Python environment such as Anaconda and Pip. During the course of the Project I created two Jupyter Notebooks, one which evolved over time with different data visualization and analysis steps and another one for the final presentation. All code lives in this GitHub repository and is also available in a docker container.

#### Tools and Techniques I used and learned during Brain Hack

* <img src="https://upload.wikimedia.org/wikipedia/en/c/cd/Anaconda_Logo.png" width="80" alt="Anaconda">
* <img src="https://www.docker.com/sites/default/files/d8/styles/role_icon/public/2019-07/vertical-logo-monochromatic.png?itok=erja9lKc" width="80" alt="Docker">
* Pandas
* NeuroKit / HRVanalysis
* Ipython Notebooks
* Dynamic Time Warping

#### Outputs
With the scripts I created, I can calculate statistics in order to compare and correlate the following physiological signals:

* Heart Rate Variability
* De-noised ECG
* Filtered Pupillometry

A direct measurement of

* Cognitive Workload 

has yet to be derived and implementd. Brain Hack allowed me to learn a lot about my data and helped me improve the recording as well as pre-processing steps for this project. The use of containers makes it easy to reproduce my current results. When working with container, it is important to keep in mind that one is working with snapshots and needs to save and commit work in progress properly (don't close your container by accident).  

# Results

To visualize and reproduce the results, you can run this code using docker. The docker pull command is:
```bash
docker pull marcelkaufmann/brain_hack
```
Then you can launch the docker container using (it will launch into the Anaconda bh einvironment for this Brain Hack project):
```bash
docker run -it --rm -p 8888:8888 marcelkaufmann/brain_hack:latest
```
with this command port 8888 on your machine is linked to port 8888 on the docker and vice versa.

Inside the docker container run in the home directory or where this projects code lives
```bash
jupyter notebook --ip 0.0.0.0 --allow-root 
```
You will then see a URL printed on the console which looks similar to this:
![dockerJupyterConsole](./img/dockerJupyter.png)

Copy the link at the bottom of your console printout into a browser and then you can launch the Notebooks:
* EvolvingNotebook.ipynb (Working notebook with full code)
* BrainHackPresentation.ipynb (Notebook used during presentation)

## Selected Results as Graphs

The following graphs have been slected as a subset from those within the Python Notebook. 

#### Heart Rate and Variability
We can see that the input data has been sampled at different rates and thus plotting this data into the same plot does not reveal much: 
![BeforeDTW](./img/beforeDTW.png)

If dynamic time warping (DTW) is applied, it is possible to align both signals:
![AfterDTW](./img/DTWapplied.png)

We can also look at different frequency components of the Heart Rate Variability. The variation in low frequencies can be an indicator for workload.
![FrequencyAnalysis](./img/FrequencyAnalysis.png)

In addition, we can derive and visualize a set of statistical measures from the HRV data.
![HRVstats](./img/HRVstats.png)

#### Pupillometry
Here we show a screenshot of an interactive Plotly graph showing the Raw Pupil Data.
![PlotlyPupilRaw](./img/plotlyPupilRaw.png)

The Raw data is filtered and can be plotted against different physiological measurements.
![plotlyPupilRaw_Raw](./img/plotlyPupilRaw_RR.png)

All these graphs and statistics can be used to gain a first understanding of the collected data.
The analysis has shown, that it is necessary to take different sample rates and filter techniques into account.

# Acknowledgements
<img src="img/logo_fondation_arbour.png" width=100 hspace=20)> </span> <img src="img/vanier_logo.png" width=200 hspace=20)>




