# MacOS Setup Instructions

If your personal computer is running MacOS and you plan to use it
for this class, you're in the right place!

## Part 1: Installing Miniconda

1. Install miniconda with Python 3.8. Download the Python 3.8 miniconda installer from here:
   https://docs.conda.io/en/latest/miniconda.html. 
   
    Scroll down to the MacOSX
   installers section and select the file under Python 3.8 ending in "pkg" (either Intel or M1 depending on the chip you have. Generally speaking we
   recommend using this pkg installer as it is easier, but if you are comfortable
   with the command line and strongly prefer using a shell script installer,
   feel free to download the bash version. 
   
    Once it's downloaded, run the installer through to completion. Note that this installer may take some time to run.
       
    It will also prompt you to review a license agreement and agree to it, as well as
       ask "Do you wish the installer to initialize Miniconda3 by running conda init?". You should
       respond "yes" to everything.
    

2. Open a terminal and run 
   
        conda -V

    You should see 
   
        conda 4.9.2

    If so, your installation of miniconda was successful!

## Part 2: Cloning the Assignment with git

The next thing you need to do is download the assignment. This assignment,
and all of the future ones, will be distributed as a git repository. 

If you're reading this, presumably you're already on the Github repository
page, but if not, you can find it here: https://github.com/cs124/pa0-python-jupyter-tutorial.

You will need to clone this repository to get access to the assignment:


1. Find a suitable folder to clone the assignment repo and go there with cd:

        cd /folder/to/put/cs124/assignments/


2. From there, clone the assignment with 
   
        git clone https://github.com/cs124/pa0-python-jupyter-tutorial.git

      This will create a folder `pa0-python-jupyter-tutorial` in the directory.


3. Move to that directory

        cd pa0-python-jupyter-tutorial

This is the extent of the git knowledge you'll need to have for this course.
All submission will be done by uploading files to Gradescope, so you don't
need to worry about committing or pushing.

P.S. If you're unfamiliar with git (i.e. haven't taken CS 107 or CS110 yet) 
and would like to learn more, you can check out the guide
[here](https://guides.github.com/introduction/git-handbook/).
   
## Part 3: Creating a Conda environment
   
1. Create a conda environment with all the dependencies you'll need. You should
   run this in the directory containing `environment.yml` (the directory 
   `pa0-python-jupyter-tutorial`, you should already be there after part 2): 
   
        conda env create -f environment.yml

   This will create a new Python environment (you can think of it as a
   separate, clean installation of Python that we can install packages in 
   without messing with any existing Python setup you may have),
   look up all of the packages in environment.yml, go to the internet
   and download them, and then install them in the environment. If those 
   packages require any other packages for them to work, it will also install 
   those.
   
    Note that this downloading and installation process may take a few minutes,
    that's entirely normal.
   

2. Activate the newly created environment:
        
        conda activate cs124
   
    You should now see `(cs124)` in front of your shell prompt. 
   You'll need to run `conda activate cs124` every time you open a new terminal 
   and re-start your notebook server.

## Part 4: Starting the Jupyter notebook server and opening the notebook

1. Start up your jupyter notebook server

        jupyter notebook


2. A window should open automatically in your default browser. If it didn't,
    the terminal output should contain a URL you can use to open the
    notebook in a browser of your choice.
   

3. From the Jupyter notebook file explorer window that opens, click on the
pa0.ipynb file to open it.

   
