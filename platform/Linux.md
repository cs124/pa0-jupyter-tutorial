# Linux Setup Instructions

If your personal computer is running Linux and you plan to use it
for this class, you're in the right place!

## Part 1: Installing Miniconda

1. Install miniconda. Open a terminal/shell session and
run:
   
         wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
         bash Miniconda3-latest-Linux-x86_64.sh

    (Some people encounter an HTTP error upon installing the environment. If that is your case, try this alternative installation script:)   
   
         wget https://repo.anaconda.com/miniconda/Miniconda3-4.7.12.1-Linux-x86_64.sh 
         bash Miniconda3-4.7.12.1-Linux-x86_64.sh  [-u]
    
    (The optional -u flag is to ignore the existing installation.)

Note that this installer may take some time to run.
   
   It will also prompt you to review a license agreement and agree to it, as well as
   ask "Do you wish the installer to initialize Miniconda3 by running conda init?". You should
   respond "yes" to everything.
    

2. Open a terminal and run 
   
        conda -V

    You should see a Conda version printed (the exact number may differ; it should be in the form of 25.x.x). If so, your installation of miniconda was successful!

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

This is the extent of the git knowledge you'll need to have for the first few PAs.
All submission will be done by uploading files to Gradescope, so you don't
need to worry about committing or pushing.

P.S. If you're unfamiliar with git and would like to learn more, you can check out the guide
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
      1. You will be prompted to select a kernel for this Jupyter notebook. Check to see if
      the environment `cs124` is in the list of available kernels.
      2. If not, stop your notebook via control-c in the terminal and run this command:
      `python -m ipykernel install --user --name cs124 --display-name "cs124"`.
      Then, restart your notebook, click the "Kernal" button, select "Change kernel," and choose `cs124` as your kernel.
   
