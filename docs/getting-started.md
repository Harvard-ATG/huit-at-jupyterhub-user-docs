# Getting Started

Once JupyterHub has been added to your Canvas site, students and teaching staff in the course will see a "JupyterHub" link in the left hand navigation of their Canvas page.

Clicking that link will give access to the JupyterHub dashboard, where a blue "Start My Server" button can be found. Clicking that link will start the process of allocating resources where the JupyterLab instance will run. This process will take a few minutes, but once the server is created, it can be used for as long as you like.

## File Storage

Each JupyterLab instance has a persistent home directory for storing files related to your work. Anything you save there will be available until you remove it, or until the JupyterHub platform is cleaned up after the end of each semester.

However, files stored outside of the home directory will not persist between working sessions, so do not save any data that you wish to keep outside of your home directory. JupyterLab will default to saving files here, but if you try to install new Python packages, they will not persist unless you set up an environment inside your home directory. More information about this process can be found in the [documentation on adding packages](adding-packages.md)

Since the JupyterLab environment is running in a remote server, you will need to upload any files you want to work with in JupyterLab, and download any files you wish to save to your computer or submit for grading. For an overview of uploading and downloading files, see the [JupyterLab documentation on uploads and downloads](https://jupyterlab.readthedocs.io/en/latest/user/files.html#uploading-and-downloading)

## Packages Available

The environment that we provide is based on the [scipy-notebook](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html#jupyter-scipy-notebook) Docker image, so all of the packages configured in that image are available in our instance of JupyterHub. This includes many of the most common data analysis libraries, such as `numpy`, `pandas`, `matplotlib`, `scipy`, `scikit-learn`, and `seaborn`.

To get a full list of packages available, [start a terminal](https://jupyterlab.readthedocs.io/en/latest/user/terminal.html) and run `mamba list`. After a short delay, you will see a list of every package available in the environment.

If you need to use a package other than the ones available, refer to our [documentation on adding packages](adding-packages.md).
