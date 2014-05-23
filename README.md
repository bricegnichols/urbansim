urbansim
========

[![build status](http://img.shields.io/travis/synthicity/urbansim.svg)](https://travis-ci.org/synthicity/urbansim) [![test coverage](http://img.shields.io/coveralls/synthicity/urbansim.svg)](https://coveralls.io/r/synthicity/urbansim)

New lightweight version of UrbanSim, a tool for modeling metropolitan real estate markets

![synthicity](http://www.synthicity.com/uploads/1/8/3/2/18327643/9164254_orig.png)

Documentation is on the github wiki: https://github.com/synthicity/urbansim/wiki

UrbanSim
-------
UrbanSim [1] is a model system for analyzing urban development.  It is an open source platform that has been continuously refined and distributed for planning applications around the world for over 15 years.  Part of the evolution of the platform is the necessary process of re-engineering the code to take advantage of new developments in computational libraries and infrastructure.  We implemented UrbanSim initially in Java in the late 1990's, and by 2005 determined that it was time to re-implement it in Python, and created the Open Platform for Urban Simulation (OPUS) software implementation at that time.  Now, almost a decade later, it is time again to revisit the implementation to take advantage of an amazing amount of innovation in the scientific computing community. The new implementation is hosted on this GitHub site, and maintained by Synthicity and hopefully a growing community of contributors.

New UrbanSim Implementation
-------

This new code base is a streamlined complete re-implementation of the longstanding UrbanSim project  aimed at *reducing the complexity* of using the UrbanSim methodology.  Redesigned from the ground up, it is a tool to make installation as trivial as any other Python package available today, and making modeling much more widely accessible to planners and new modelers.

This UrbanSim package uses no code from the svn repository currently hosted on urbansim.org, though it makes every effort to implement the exact same methodology, but with a lighter footprint.  We lean heavily on the PyData [2] community to make our work easier - *Pandas, HDF5 file storage, and statsmodels* are ubiquitous in this work.  These Python libraries essentially replace the UrbanSim Dataset class, tools to read and write from other storage, and some of the statistical estimation currently present in UrbanSim.

This makes our task easier as we can focus on urban modeling and leave the infrastructure to the wider Python community.  The Pandas [3] library is the core of the new UrbanSim, and is an extremely well documented library that has a large community providing support, and a very helpful *book* [4].  So please refer to those resources for detailed information on Pandas.

We are building a 'model factory' that uses configuration information stored in JSON syntax to create standard Python code that implements the model.  JSON [5] is widely used for web programming, and we are leveraging it to build a web service for estimating models and interacting with model inputs and predictions.  

We have now converted a full set of UrbanSim models in the new framework, enabling a complete UrbanSim application, and have these running for applications in Paris, Albuquerque, Denver, and others currently being implemented or converted from the earlier OPUS implementation.  These models include 1) *hedonic price models* 2) MNL and nested *location choice models* 3) transition models for increasing population, jobs, and development and 4) relocation rate models to specify the movement of population and jobs.  We have also implemented a new real estate development model using proforma analysis.

**If you just want to begin experimenting and creating regression and choice models and map their inputs and outputs, you've also come to the right place.**

[1] http://urbansim.org/

[2] http://pydata.org

[3] http://pandas.pydata.org

[4] http://www.amazon.com/Python-Data-Analysis-Wes-McKinney/dp/1449319793

[5] http://en.wikipedia.org/wiki/JSON

Installation instructions for UrbanSim users
---------------
Coming soon.  As soon as we are ready, we will create an installer that will make installation trivial for end-users.
We do strongly recommend that you contact info@synthicity.org about your project to make sure you can get professional support when you need it, and know what you are getting into.  For major applied projects, professional support is highly recommended.

Installation instructions for UrbanSim programmers
---------------

Download and install Anaconda Python distribution (early reviews on the v1.8 Anaconda installer are that there's something wrong with Pandas - not sure what the specifiecs are yet, but we suggest v1.6 of the installer with Pandas v0.11 - upgrading will cause Pandas to crash on many operations!):

http://www.continuum.io/downloads

Get repository:

```
>> git clone https://github.com/synthicity/urbansim.git
```

Set environment variables:

```
>> cd urbansim
>> export PYTHONPATH=$PWD
>> export DATA_HOME=$PWD
```

!!! Contact info@synthicity.com to get sample dataset - this example won't run without it. !!!
<!--Download data:

```
>> curl -k -o data/mrcog.zip https://dl.dropboxusercontent.com/u/2815546/mrcog.zip
>> unzip -d data data/mrcog.zip
```-->

Run:

```
>> cd example
>> ./run.sh
```