# SDC-Unscented-Kalman-Filter-P7

## Kidnapped Vehicle Project - Particle Filter
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

In this project I implemented a 2 dimensional particle filter in C++. My particle filter was given a map and some initial localization information (analogous to what a GPS would provide). At each time step my filter also got observation and control data. [project reburic](https://review.udacity.com/#!/rubrics/747/view). 

## Overview
This repository contains all the code I neededed to complete the final project for the Localization course in Udacity's Self-Driving Car Nanodegree.

## Project Introduction
My robot has been kidnapped and transported to a new location! Luckily it has a map of this location, a (noisy) GPS estimate of its initial location, and lots of (noisy) sensor and control data.


## Running the Code

Here is the main protcol that main.cpp uses for uWebSocketIO in communicating with the simulator.

INPUT: values provided by the simulator to the c++ program

// sense noisy position data from the simulator

["sense_x"] 

["sense_y"] 

["sense_theta"] 

// get the previous velocity and yaw rate to predict the particle's transitioned state

["previous_velocity"]

["previous_yawrate"]

// receive noisy observation data from the simulator, in a respective list of x/y values

["sense_observations_x"] 

["sense_observations_y"] 


OUTPUT: values provided by the c++ program to the simulator

// best particle values used for calculating the error evaluation

["best_particle_x"]

["best_particle_y"]

["best_particle_theta"] 

//Optional message data used for debugging particle's sensing and associations

// for respective (x,y) sensed positions ID label 

["best_particle_associations"]

// for respective (x,y) sensed positions

["best_particle_sense_x"] <= list of sensed x positions

["best_particle_sense_y"] <= list of sensed y positions


My job was to build out the methods in `particle_filter.cpp` so the simulator could output the following message:

```
Success! Your particle filter passed!
```

## Implementing the Particle Filter
The directory structure of this repository - with the required files for the project - is as follows:

```
root
|   build.sh
|   clean.sh
|   CMakeLists.txt
|   README.md
|   run.sh
|
|___data
|   |   
|   |   map_data.txt
|   
|   
|___src
    |   helper_functions.h
    |   main.cpp
    |   map.h
    |   particle_filter.cpp
    |   particle_filter.h
```

I was responsible for modifying the `particle_filter.cpp` file in the `src` directory. The file contains the `ParticleFilter` class and all the associated methods - initialization, prediction, update and resampling. 

### Inputs to the Particle Filter
You can find the inputs to the particle filter in the `data` directory. 

#### The Map*
`map_data.txt` includes the position of landmarks (in meters) on an arbitrary Cartesian coordinate system. Each row has three columns
1. x position
2. y position
3. landmark id

### All other data the simulator provides, such as observations and controls.

> * Map data provided by 3D Mapping Solutions GmbH.

## Success Criteria
The things the grading code was looking for were:


1. **Accuracy**: my particle filter should localize vehicle position and yaw to within the values specified in the parameters `max_translation_error` and `max_yaw_error` in `src/main.cpp`.

2. **Performance**: my particle filter should complete execution within the time of 100 seconds.

## Video with Results

A video of the results named "Particle-Filter-P8.mov" is located in the repository. The blue circle indicates the predicted location of the car. The video shows what the simulator looks like when it is successfully able to track the car to a particle. The simulator provides the script the noisy position data, vehicle controls, and noisy observations. the script feeds back the best particle state.

