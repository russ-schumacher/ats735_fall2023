# Homework assignment 1 (and only)
## Due Friday, 27 October 2023

For this assignment, we'll be setting up and running [Cloud Model 1 (CM1)](https://www2.mmm.ucar.edu/people/bryan/cm1/) to conduct some numerical model simulations, and then analyzing the model output.  

## Installing the CM1 model
The first step is to download and install CM1. Some instructions for doing that are [here](cm1_instructions.md).

## Setting up a python environment to analyze and plot CM1 output
If you want to use python to analyze and plot the model output, I've put together some basic instructions and example code [here](cm1_python_instructions.md). You can wait to do these steps until after you've set up and run the model if you want. Likewise, if you're more comfortable with using a different programming language, you're more than welcome to do so! The 'original' language used by CM1 is [GrADS](http://cola.gmu.edu/grads/), and this is another good choice.

## Assignment

### Model configuration
1. George Bryan has kindly provided some example namelists for running CM1 on the website [here](http://www2.mmm.ucar.edu/people/bryan/cm1/namelists/). Get the namelist for the squall line case. Write a paragraph summarizing the model configuration that is described in this namelist (write this as if you were writing a journal article about these simulations: enough information that the reader could set up an identical (or very similar) simulation, but not simply listing off every selected option.) You can use a table if you wish.

2. Before running any simulations, we’re going to make a couple small changes to the namelist: turn on the output of pressure and potential temperature perturbations (prspert and thpert.) Also, increase the output frequency so that output files are written every 3 minutes (instead of the default 15 minutes).

### 2D vs. 3D simulations

First, we’re going to examine some of the differences that arise when running a 2-D squall-line simulation, compared with simulating it in 3 dimensions. Running a 2-D simulation is remarkably simple: just set ny = 1. It'll also run really fast. Run both a 2-D and 3-D simulation with the other model configuration settings kept at the default values. Generate any relevant figures, and summarize the similarities and differences between these two runs. Note that you will need to make some decisions about how to directly compare them (e.g., take a single slice of the 3-D simulation and compare it to 2-D? Average along the line? If so, what averaging length?) One thing to focus on in this comparison is the updraft velocities. 

### Your own experiments
Now, you can start running your own experiments. How to configure them is completely up to you, but first come up with a hypothesis that you want to test---it’s ok if this isn’t particularly original and has already been shown in the literature---and set up and run the model to test that hypothesis. (As an example, here’s a very trivial hypothesis: convection in an environment with vertical wind shear will be more organized than that in an unsheared environment. To test this, I’d set up some a run similar to my “control” run above but with zero wind shear, and investigate the differences. I trust that you will come up with slightly more interesting hypotheses than this, but it can also be instructive to test something that seems like “conventional wisdom” and confirm that it is—or isn’t—correct!) Anyway, design, run, and analyze at least two experiments, and (if applicable) compare and contrast your results to what is shown in the literature. Write up your results as if they were a short conference paper or journal article. (Emphasis on short—be concise in your writing and presentation of figures!)

## A few tips
* The “out of the box” simulations described above should be possible to run on any desktop, or even laptop, machine. The 2D simulations will be fast (a few minutes on my laptop), the 3D will take a while longer. If you have computing resources available to you and you want to do experiments that test the sensitivity to resolution, of course feel free to do so, but considering that not everyone in the class will have the capability (or desire) to run at higher resolution, it’s totally fine to do your experiments at the default grid spacing.
* You should be able to just use the output files that are interpolated to the scalar grid (for example, uinterp, vinterp, winterp) – this is generally easier to work with than dealing with the velocity components on the staggered grids.
* Note that CM1 also outputs files with useful statistics about the simulations (“cm1out stats”). These can be quite handy when trying to assess the overall behavior of the simulation over time, without having to use the full output files.
* CM1 is also nice enough to calculate useful quantities for you as they relate to squall lines, such as the cold-pool intensity c.

