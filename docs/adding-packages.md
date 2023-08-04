# Adding Packages

!!! warning
    This documentation site is a work in progress, and is being tested and refined internally. Do not use this documentation as a reference in its current state.

Our Python configuration is based on the [Jupyter scipy notebook](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html#jupyter-scipy-notebook) stack, which includes many of the most common packages for use in data collection and analysis in Python. In addition, instructors can request a customized environment with specific packages pre-installed for use in a course.

However, there may still be cases where you want to install additional packages in this environment. In this JupyterHub configuration, every time you start your server, a new AWS server resource is allocated to run that server using the default configuration for your course. That means that any additional modules must be configured from your persistent home directory, rather than elsewhere on the system, which is being replaced regularly.

To configure packages locally, you will need to first create a local environment in your home directory using `mamba`. Then, you will need to register that environment with ipython to use it as a kernel in your JupyterLab environment.

## Configuring a Local Environment

Configuring a local environment will require use of the terminal in JupyterLab. To configure such an environment, use the commands below. Comments have been added with additional instructions. Where you see "environmentName", you can replace it with a folder name that you prefer to use. This will be the folder that contains the environment in your home directory. You can also replace "DisplayName" with a preferred name for your environment as it appears in the JupyterLab interface. You can use the same name as your folder name, just know that the two are not necessarily related. Neither the folder name nor the display name should contain spaces.

```bash
mamba create --prefix ./environmentName
mamba init
# close and re-open the terminal
mamba activate ./environmentName
mamba install ipykernel
# install other packages with mamba install
ipython kernel install --user --name=DisplayName
```

## Using the New Kernel

Once you have run these commands successfully, you should see a new option with the same name that you used for "DisplayName" when launching a new notebook. To use the new environment in an existing notebook, open that notebook, then click on the current kernel name in the top right (the default is "Python3 (ipykernel)"). This will bring up a pop-up with a dropdown menu where you can change the kernel to match your new environment. After doing this, you should restart your notebook's kernel from the "Kernel" menu at the top of the page.

Once you have your environment configured, you can add more packages to it by activating it, then using `mamba install` to configure more packages, like so:

```bash
mamba activate ./environmentName
mamba install numpy pandas matplotlib
```
