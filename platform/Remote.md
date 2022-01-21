# Rice/Myth Setup Instructions

### [WARNING! PLEASE READ]

Generally speaking, we have found that things go much smoother
if you are able to run and work on the assignments on your local
computer, without having to connect to the Myth/Farmshare machines remotely
and deal with any potential issues that may arise.

So if you do have a local machine that can be used for these assignments, we
__STRONGLY__ encourage using it and following one of the other sets of 
instructions.

If you have concerns or believe your computer may not be suitable for the class,
please reach out to the teaching staff in OH or on Piazza before proceeding with
these instructions. We'll try to check if there are any workable alternatives
before proceeding.

If you have spoken to the teaching staff and this still appears to be the best
option, you can continue to the instructions below.

## What are Rice/Myth?

Rice is the name of a group of machines made available for student use
by Stanford. Myth machines are similar, but specifically maintained by and
for the computer science department. For our purposes, they are interchangeable
so you shoul feel free to use whichever one you prefer.

## Part 1: Initial steps __[WINDOWS ONLY]__

 If you are using Windows, you will need to set up a method
for using SSH, as that is the protocol we need to use to connect to rice/myth.
If you are not using Windows, you can skip this part.

You have two options:

1. Go to the Windows_Setup.md and follow the instructions in Part 1 to 
   install Ubuntu for Windows. You can then use the Ubuntu command line for
   all future steps. 
   
2. If this is not an option, you can instead download and install
PuTTY [here](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
to use as an SSH client. Install and run it. 
   
If you chose option 1, in the instructions below, follow the steps labeled
__[MacOS/Linux/Ubuntu for Windows]__. If you chose option 2, follow the steps labeled
__[PuTTY]__ instead.


3. SSH into Rice/Myth.
   - __[MacOS/Linux/Ubuntu for Windows]__: Open a terminal window (i.e. for
     Windows, run Ubuntu). Then, in that terminal, run:

            ssh [Your SUNet]@rice.stanford.edu
            # OR
            ssh [Your SUNet]@myth.stanford.edu

   - __[PuTTY]__ Run PuTTY and when prompted, enter `rice.stanford.edu` or
    `myth.stanford.edu` in the box labeled Host Name. Do not change any of the
     other settings. Click open to open a connection, which will cause a 
     terminal window to pop up. You will then be prompted to log in.

    You'll be prompted for your Stanford SUNet account password. 
   You will also likely be asked to authenticate using 
   2-factor authentication.
   
## Part 2: Installing Miniconda

1. Once you've SSH'd into Rice or Myth, install miniconda by running the following 
   commands and following through the installer instructions:
   
        wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
        bash Miniconda3-latest-Linux-x86_64.sh

   Note that this installer may take some time to run.
   
   It will also prompt you to review a license agreement and agree to it, as well as
   ask "Do you wish the installer to initialize Miniconda3 by running conda init?". You should
   respond "yes" to everything.
   
2. Once it has finished, copy and run the following command in your terminal 
   to allow you to use conda from the command line:
       
        printf '\n# add path to conda\nexport PATH="$HOME/miniconda3/bin:$PATH"\n' >> ~/.bashrc
        source ~/.bashrc

3. Run 
   
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

1. Start up your jupyter notebook server without a browser.

        jupyter notebook --no-browser --port=[pick a number from 1025 to 65535]

    You will need to
pick a port number between 1025 and 65535 when starting the server. Any number
   will do, but on the small chance that you run into issues, it could be because
   you are on the same machine as another student and on the same port number
   as well. If that happens, just pick a different port number and restart the
   server (run the above command again).

2. You now need to set up port forwarding from Rice/Myth to your local machine:

   - __[MacOS/Linux/Ubuntu for Windows]__ Open a new, separate terminal on your
     local machine (NOTE: don't close the one that you used to SSH into 
     rice/myth, that one needs to stay open) and enter the following command:

            ssh -NL [local port you'd like to use]:localhost:[port number you picked on rice/myth] [SUNet]@[rice/myth].stanford.edu

    You can pick any local port number you want between 1025 and 65535. It does
    not have to be the same one you used earlier for the jupyter
    server, but it would be a good idea to pick only one, as then you only need
     to remember a single number. 

    If it worked correctly, seemingly nothing will happen and your terminal will 
    appear  to hang (the command will keep running and not return). This is fine
   and  exactly what we expect. Keep this window open as well! If you close it, it
    will stop the port forwarding.

   - __[PuTTY]__ Go back to your PuTTY window. In the left-side navigation
    window and select Connection->SSH->Tunnels. In the right-hand side window,
     there will be a section labeled "Add new forwarded port". 
     
    Under Source port, type the local port you'd like to forward to. 
    Destination, type:

        [rice/myth].stanford.edu:[port your Jupyter notebook server is running on]
     
    Then, click "Add".


3. Finally, try opening a browser of your choice (i.e. Chrome, Firefox, Safari)
    on your local machine and opening the URL:
    
        localhost:[local port number you chose]

    If everything worked correctly, you'll see the Jupyter file
    explorer. It may prompt you for an authentication token. If it does,
    go back to the terminal window that is running the Jupyter notebook server
    (the one you used to SSH/connect to rice/myth). In that window, you should 
    see some URLs with a portion that  looks like "token=...". Copy the token 
    from there and paste it into your browser where requested. This should
    let you proceed to the Jupyter file explorer.
    

4. From the Jupyter notebook file explorer window that opens, click on the
pa0.ipynb file to open it.