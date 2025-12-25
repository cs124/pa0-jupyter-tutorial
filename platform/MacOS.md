# MacOS Setup Instructions

If your personal computer is running MacOS and you plan to use it
for this class, you're in the right place!

## Part 0: Setup for Apple Silicon Chips (M1, M2, M3, M4, M5)

If you have an M1, M2, M3, M4, or M5 Chip, you might need to do a bit of additional setup first. If you do not fall into this category (i.e. you have an Intel Chip), please skip this part and go to Part 1. 

We will first check if Rosetta 2 is installed. Rosetta is a translation layer that lets you run applications for Intel on your newer Mac.

    /usr/bin/pgrep -q oahd && echo Yes || echo No 

This command checks if any processes are running with the Rosetta translation layer (internally known as 'oahd'). If none are, you can (re)install Rosetta to verify that it is on your mac with this command:

    softwareupdate --install-rosetta --agree-to-license

## Part 1: Installing Miniconda

If you already have a Conda installation, it should be compatible, so skip to part 2. Make sure to read all of part 3 as well.

1. Download the latest miniconda installer by clicking one of these links:

   1. Graphical Installer for Apple Silicon conda:
           https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.pkg

   2. Graphical Installer for Intel conda:
           https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.pkg
      
   3. Documentation for other install methods: [https://docs.anaconda.com/miniconda/install/](https://docs.anaconda.com/miniconda/install/)
    
    Once it's downloaded, run the installer through to completion. Note that this installer may take some time to run.
       
    It will also prompt you to review a license agreement and agree to it, as well as
       ask "Do you wish to update your shell profile to automatically initialize conda?". You should
       respond "yes" and/or "allow" to everything.
    
    **Note for Intel Mac users:** While new package builds for Intel Macs ended in August 2025, all existing packages remain available and fully functional. You'll have access to all the packages needed for this course.

2. Open a terminal and verify that conda is installed by running:
   
       conda -V

    If you see something like `conda 25.11.1`, you are good to go!

    If you get an error like:

   `zsh: command not found: conda`
   
   or
   
   `__conda_exe:1: no such file or directory: /Users/yourname/miniconda3/bin/conda`
    
    First, try again in a new terminal window. If conda is still not working, the installer may have configured conda incorrectly. Recent versions install to `/opt/miniconda3` by default, so run:

       /opt/miniconda3/condabin/conda init zsh

    If that command fails with "no such file or directory", then conda may be installed elsewhere. You can search for it with:

       find /opt /Users -name "conda" -type f 2>/dev/null | grep -E "(bin/conda|condabin/conda)"

    Once you find the correct path, run conda init with that path:

       /ACTUAL/PATH/TO/miniconda3/condabin/conda init zsh

   After running conda init, reload your shell:

       source ~/.zshrc

   Then verify conda is working:

       conda -V

   If this still doesn't work, make a post on Ed so we can help!

## Part 2: Cloning the Assignment with git

The next thing you need to do is download the assignment. This assignment,
and all of the future ones, will be distributed as a git repository. 

If you're reading this, presumably you're already on the Github repository
page, but if not, you can find it here: https://github.com/cs124/pa0-python-jupyter-tutorial.

You will need to clone this repository to get access to the assignment:


1. Find/create a suitable folder to clone the assignment repo and go there with cd:

       cd /folder/to/put/cs124/assignments/

   for example, a good place might be on your Desktop or in your ~/Documents folder:

       mkdir ~/Desktop/cs124
       cd ~/Desktop/cs124


2. From there, clone the assignment with 
   
       git clone https://github.com/cs124/pa0-python-jupyter-tutorial.git

      This will create a folder `pa0-python-jupyter-tutorial` in the directory.


3. Move to that directory

       cd pa0-python-jupyter-tutorial

This is the extent of the git knowledge you'll need to have for the first few PAs of the course.
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

    - You may get an error that says "not all packages could be found upstream". 
      This happens because the package versions we use in this class do not have
      native binaries for Apple Silicon Macs. To fix this issue, we will tell Conda
      to use osx64 (Intel) versions of these packages.

          CONDA_SUBDIR=osx-64 conda env create -f environment.yml 
          conda activate cs124 
          conda config --env --set subdir osx-64 
   

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
      1. You may be prompted to select a kernel for this Jupyter notebook. Check to see if
      the environment `cs124` is in the list of available kernels. If not, stop your notebook via control-c in the terminal and run this command:
      `python -m ipykernel install --user --name cs124 --display-name "cs124"`.
      Then, restart your notebook, click the "Kernal" button, select "Change kernel," and choose `cs124` as your kernel.

4. If you see the error "500 : Internal Server Error", then go to the terminal and first stop your jupyter notebook via control-c.

      1. Above in the terminal, there should be a red error line stating a lack of permissions to a conf.json file. The file path should be displayed as "/SOME/FOLDER/PATH/conf.json". Take the folder of this conf.json file (i.e. "/SOME/FOLDER/PATH/"). For example, the folder is likely to be "/usr/local/share/jupyter/nbconvert/templates/" or "/usr/share/jupyter/nbconvert/templates/".
      
      2. Finally, take this folder path and enter the following command in the terminal. Enter your computer user's password when prompted.
           
       sudo chmod -R 777 /SOME/FOLDER/PATH/
      
      3. Finally, try starting again from Step 1 of Part 4.