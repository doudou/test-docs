---
title: "Setting up"
tagline: "From nothing to a functional (simulated) AUV"
---

We will assume here that you have successfully installed a [Rock
environment](http://rock-robotics.org/), and that you have at least followed
(and understood) the [Rock tutorials](http://rock-robotics.org/master/documentation/tutorials/index.html)

This page will deal with _what comes next_. In other words, what are the
prerequisite to start working on your actual AUV.

Create your bundle
------------------
First things first, will need to create a new Dive! bundle

~~~
$ acd
$ cd bundles
$ dive gen bundle dive_demo
~~~

Unless specified otherwise, file and directory paths given in the rest of the
documentation are relative to this bundle's root directory

Initial vehicle setup
---------------------

The first step is to describe the vehicle using the [Simulation Data
Format](http://sdformat.org) (a.k.a. SDF). Dive! exclusively uses SDF as its
description format for the world (simulation) and for the robot itself.

The first thing you will want to do with your vehicle is to move it, really.
To achieve this, the SDF basically needs to provide three things:

 1. a visual, that is an openscenegraph-supported mesh (DAE or STL are good
    choices, and easy to export from common 3D modellers)
 2. a placement of the system's thrusters
 3. some physical parameters (friction, boyancy). It's easy to get "sane
    defaults" to get started even if they don't match your system's actual
    parameters.

The default location in which to place the SDF file as well as SDF-related
information is models/sdf/name_of_robot.

On top of the SDF file, Dive! can generate for you a whole scaffold for a
simulated vehicle, that you can then use as the basis for your own vehicle. Get
it by doing

~~~
$ dive gen vehicle dive_demo
~~~

If you are really interested only by the SDF file, you can limit the generation
to that with

~~~
$ dive gen vehicle --sdf dive_demo
~~~

The generated template vehicle can be used as-is (i.e. has a thruster setup that
is valid).  The template generation also creates a new SDF world description
file in scenes/ that includes only the vehicle, to allow you to test and work on
the new vehicle right away.

Simulation
----------

You can start gazebo and attach a visualization right away. In a console do

~~~
$ dive sim scenes/dive_demo
~~~

And in another

~~~
$ dive run -rdive_demo_sim -c
~~~

There's really nothing much more that you can do for now ... but [that's going
to change](control.html)

