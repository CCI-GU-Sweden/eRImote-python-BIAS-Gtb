# Python environments and kernels

## What is an environment

An environment is a specific setup of python version, modules and other installed software that can be reused, repeated and distributed.

It allows you, in a convenient way, to have multiple versions of python and modules installed.

Environments can be "activted" when they should be used and "deactivated" when they are not needed anymore.

An environment can be stored as a single file and distributed to other people who want to try your experiments or run your code.

A kernel is an environment that is exported to be used in jupyter lab and notebooks.

## Download miniconda
Browse to

https://conda-forge.org/download
<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

or, in a terminal, execute

```
wget https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-x86_64.sh
```

**OBS!** On BAND make sure you download it directly to your home directory. ```wget``` will download to your current working directory but your browser might choose location for you!


## Install miniconda
Execute the following in a terminal.

```
chmod u+x miniforge3-Linux-x86._64.sh
./miniforge3-Linux-x86._64.sh
```

**_Do NOT activate conda during installation_**

NOTE: on your own computer it is absolutely possible that you want to activate conda during installation. However, on BAND, we can't do that.

## Source the conda file (Activate conda)

In your terminal type
```
source ~/miniforge3/etc/profile.d/conda.sh 
```

### Create alias to source the file (optional but recommended)

In a terminal type
```
alias condaon='source ~/miniforge3/etc/profile.d/conda.sh'
```

### Make the alias permanent
Open text editor and type
```
alias condaon='source ~/miniforge3/etc/profile.d/conda.sh'
```

in an empty file. save file as ```.bashrc``` in home folder.

In terminal execute
```
chmod u+x .bashrc
```
Open a new terminal and type
```condaon```
this will activate conda an give access to the conda command

## Create a conda environment

When conda is active, type 
```
conda create -n name_of_env python==3.10
```
Where ```python==3.10``` means we want a specific version (3.10) of python in this environment
and ```name_of_env``` is the name you want to give your environment.
Use a name that allows you to remember what it is used for.

## Activate an environment
when conda is active type
```
conda activate name_of_env
```

Now your environment is active and the packages installed (and only those) are available to you.


## Installing python modules in your environment with Pip
To install python modules we can use a program called ```pip``` like this:
```pip install module``` or ```pip install module==x.y.z``` to install a specific version. I.e.
```
pip install numpy==2.0.0
```
If version is not specified, the latest version available will be installed.

### Install jupyter tools
In a terminal, with your conda environment active, typ
```
pip install jupyterlab ipykernel ipython
```
to install jupyter tools

Start jupyter lab either by typing
```
jupyter lab
```
or from menu. Notice that your environment is NOT available as kernel :(

Exit jupyter lab.

## Making a conda environment available as kernel for jupyter

With your desired conda environment active, execute the following in a terminal:
```
python -m ipykernel install --user --name=cool_kernel
```
**or**
```
ipython kernel install --user --name=cool_kernel
```

Start jupyter lab again and check if something has changed!


## Sharing and reusing environments
Conda allows you to export your environment to share it with others as well as allowing yout to install environments that are shared with you.
To export one of your environments, activate the environment and type:
```
conda env export > your_environment.yml
```
This will store the needed data in the file ```your_environment.yml```

In order to create an environment from a file you type, in a terminal:
```
conda env create -f environment.yml
``` 
This will create an environment as specified in the file ```environment.yml```.

Download this environment file to your computer and try to recreate the environment:
[environment.yml](https://raw.githubusercontent.com/CCI-GU-Sweden/eRImote-python-BIAS-Gtb/refs/heads/main/create_kernel/environment.yml) (by right clicking on the link -> "save link as..." using ```wget``` )

* What is the name of the environment?
* What version of python does it contain?
* Find a few other packages that are installed in the environment
* Export the new environment to be used as a kernel i jupyter lab
* Deactivate all conda environments

Use some of the commands in the list below to answer the questions.

## Useful conda commands
* List environments: ```conda env list```

* Show installed packages in environment: ```conda list``` Combine it with ```|``` and ```grep``` to find a specific package: ```conda list | grep dask``` will list information about the package ```dask``` (if it is installed.

* Deactivate environment (go back to base environment): ```conda deactivate``` 

## Removing a kernel from jupyter (lab)
In order to remove a kernel from jupyter you can use the ```jupyter kernelspec``` command like this:
```
jupyter kernelspec remove --name=name_of_kernel
```
efter this command 'name_of_kernel' will no longer be available in jupyter lab.

To see available kernels use the command
```
jupyter kernelspec list
```

## Removing environments

When you want to remove a conda environment you can use:
```
conda env remove -n name_of_environment
```
just make sure you have deactivated the environment or have another environment activated.

CAVEATS: removing an environment does not remove it as a kernel from jupyter!

* Remove all **_kernels_** you created from jupyter (NOT the original named python3)
* Remove any conda **_environments_** you created


## More information / Documentation
Documentation for conda/Miniforge can be found here:
https://conda-forge.org/docs/user/


## Return to main course page
https://github.com/CCI-GU-Sweden/eRImote-python-BIAS-Gtb

