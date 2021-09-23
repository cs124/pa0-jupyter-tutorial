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

## Part 1: Setting up Ubuntu for Windows

1. To get a working Linux environment set up on your Windows machine, we
recommend using Ubuntu for Windows 10. It requires that you have an installation
of Windows 10 which includes [this update](https://support.microsoft.com/en-gb/help/4028685/windows-10-get-the-fall-creators-update). 


* If you have an up-to-date Windows 10 installation, you are all set. 
* If you do not have the update installed, you should go ahead and update from
Windows settings, or follow the specific instructions in the link above to 
install it.
* If you have an older version of Windows, like Windows 7 or 8, you 
will need to [upgrade to Windows 10 first](https://www.microsoft.com/en-us/software-download/windows10ISO) (it's free).
If for some reason you're not able to upgrade to Windows 10, please contact the
teaching staff on Piazza or via the staff email address as soon as possible!
   
2. Follow the instructions [here](https://ubuntu.com/tutorials/ubuntu-on-windows#1-overview)
to install Ubuntu for Windows.
   

3. Once the installation process is complete, run Ubuntu (it should 
   be located in your list of installed programs). A terminal window should 
   pop up and you should be able to type in it.


4. If so, you're all set and can continue to the next section!

#### Helpful note: If you need to access the disks under the Windows system (c:\ d:\ e:\ etc), they are located under ubuntu path /mnt/

## Part 2: Installing Miniconda

1. Install miniconda with Python 3.8. To do this, run Ubuntu to start a terminal
   (you can find Ubuntu under your list of installed programs).
   
    Then in the terminal that opens, run:
   
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
   

2. Run 
   
        conda -V

    You should see 
   
        conda 4.9.2

    If so, your installation of miniconda was successful!

## Part 3: Cloning the Assignment with git

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
   

2. Activate the newly created environment:
        
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

   

