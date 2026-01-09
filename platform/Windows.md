# Windows Setup Instructions

If your personal computer is running Windows and you plan to use it
for this class, you're in the right place!

__NOTE:__ If you have access to a Windows machine as well as a Linux or MacOS
machine and don't have a clear reason to use Windows, we would encourage using
one of the other options, as generally it should be a bit easier. Otherwise,
please proceed.

## Preface: A Note about Windows

For this class, we strongly encourage working
in a UNIX-like operating system, as part of the class
will require working with UNIX command line tools. 
Having a UNIX-like environment set up will also make it easier for us to 
help you set up other parts of the course (like running your Jupyter notebooks 
and setting up your Python environment and dependencies).

In addition, most of the future courses you'll take in the CS department, 
irrespective of specialization, will work in UNIX-like environments and expect 
that you're familiar with them, so it's a very useful skill set to learn.

With that said, if your personal computer runs Windows and you don't currently
have access to a Linux or macOS alternative, __don't worry__. There are good
options available for Windows, and instructions for how to get things set
up are provided below.

## Part 1: Setting up WSL (Windows Subsystem for Linux)

Windows Subsystem for Linux (WSL) allows you to run a Linux environment directly on Windows without the need for a virtual machine or dual-boot setup.

### Prerequisites

You need one of the following Windows versions:
- Windows 11 (any version)
- Windows 10 version 2004 or higher (Build 19041 or higher)

### Installation Steps

1. Open PowerShell on your machine. You can find it by looking up "PowerShell" in any search bar.

2. Run this command to install WSL first:
        wsl --install

3. Run this single command to install Ubuntu:
   
       wsl --install -d Ubuntu

   This process may take several minutes depending on your internet connection. You may be asked to reboot your computer and/or create a Linux username and password.

4. Once setup is complete, you should see a terminal prompt that looks something like:
   
       username@computername:~$
   
   Close the shell and start a new one. Run the command `wsl -l -v`. You should see something like

         NAME        STATE    VERSION
       * Ubuntu      Stopped     2

   If you see this, congratulations! You have a working Linux environment.

P.S. If you would like more details on setting up WSL and Ubuntu, see [here](https://documentation.ubuntu.com/wsl/stable/howto/install-ubuntu-wsl2/).

## Part 2: Installing Miniconda

Now that you have Ubuntu running on your Windows machine, you'll install Miniconda to manage Python and packages for the class.

1. Launch Ubuntu from the Start menu (or type `wsl` in PowerShell). You should do this every time before you open a directory for this class.

2. Download and install Miniconda. Run these commands in your Ubuntu terminal:
   
       wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
       bash Miniconda3-latest-Linux-x86_64.sh

   Note: The download and installation may take a few minutes.

3. Follow the installation prompts. When asked "Do you wish to update your shell profile to automatically initialize conda?", type `yes`.

4. Close your Ubuntu terminal and open a new one. You should now see `(base)` at the beginning of your command prompt, indicating that conda is active.

5. Verify conda installation
   
   Run:
   
       conda -V

   You should see something like:
   
       conda 25.11.1

   The exact version number may vary, but as long as you see a conda version, your installation was successful!

### Troubleshooting

If you get `conda: command not found` after reopening your terminal:

1. Check if conda was installed:
   
       ls ~/miniconda3/bin/conda

2. If the file exists, manually initialize conda:
   
       ~/miniconda3/bin/conda init bash

3. Close and reopen your terminal, then try `conda -V` again

If this still doesn't work, make a post on Ed so we can help!

## Part 3: Cloning the Assignment with git

The next thing you need to do is download the assignment. This assignment,
and all of the future ones, will be distributed as a git repository.

If you're reading this, presumably you're already on the Github repository
page, but if not, you can find it here: https://github.com/cs124/pa0-python-jupyter-tutorial.

You will need to clone this repository to get access to the assignment:


1. Find a suitable folder to clone the assignment repo and go there with cd:

        mkdir ~/cs124
        cd ~/cs124

   Note: The `~` represents your home directory in Ubuntu, which is separate from your Windows home directory.

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

## Part 4: Creating a Conda environment

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

2. Activate the newly created environment with this command:
        
       conda activate cs124
   
   You should now see `(cs124)` in front of your shell prompt. 
   You'll need to run `conda activate cs124` every time you open a new terminal 
   and re-start your notebook server.

## Part 5: Starting the Jupyter notebook server and opening the notebook

1. Start up your jupyter notebook server

        jupyter notebook --no-browser

2. The terminal output should contain a URL to access the notebook. Copy and 
paste it into the browser of your choice and navigate to it.

3. From the Jupyter notebook file explorer window that opens, click on the
pa0.ipynb file to open it.
      1. You may be prompted to select a kernel for this Jupyter notebook. Check to see if
      the environment `cs124` is in the list of available kernels. If not, stop your notebook via control-c in the terminal and run this command:
      `python -m ipykernel install --user --name cs124 --display-name "cs124"`.
      Then, restart your notebook, click the "Kernal" button, select "Change kernel," and choose `cs124` as your kernel.

## Part 6: Submitting the Notebook

After you have created `submission.zip` in WSL, run the following command to transfer that zip file over from WSL to your local computer:

        cp ~/cs124/pa0-jupyter-tutorial/submission.zip /mnt/c/Users/YOUR_USER_NAME/OneDrive/Desktop/

Note that you may want to replace `OneDrive/Desktop/` with another destination folder based on your preferences.

You can then upload `submission.zip` to Gradescope. You are all done!