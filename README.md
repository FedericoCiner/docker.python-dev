# Docker for Python Development

A set of Docker images that copied/modified so I could have a standardized Python development environment across my Mac and Linux machines.

The following is a brief description of the images:
* _ubuntu_: Lightweight Ubuntu image based off the latest distribution of Xenial.
* _python-base_: Contains a standard Python 2.7 installation, with selected packages for scientific computing, machine learning, and data science.
* _python-notebook_: Basically the standard Jupyter Notebook and Jupyter Lab image from the Dockerhub, with some slight modifications/simplifications for the base user and groups.