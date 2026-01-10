# Google Colab Notebook Setup Instructions

### [WARNING! PLEASE READ]

Generally speaking, we have found that things go much smoother
if you are able to run and work on the assignments on your local
computer, without having to use Google Colab notebooks.

So if you do have a local machine that can be used for these assignments, we
__STRONGLY__ encourage using it and following one of the other sets of 
instructions.

If you have concerns or believe your computer may not be suitable for the class,
please reach out to the teaching staff in OH or on Piazza before proceeding with
these instructions. We'll try to check if there are any workable alternatives
before proceeding.

If you have spoken to the teaching staff and this still appears to be the best
option, you can continue to the instructions below.

## Part 1: Google Colab Setup

1. Go to [colab.research.google.com](http://colab.research.google.com). 
   If prompted to open a notebook, hit cancel for now. You should double-check 
   that you are logged in to your Stanford Google account. If not, you can 
   switch accounts in the top right.
   
## Part 2: Opening the Notebook

1. Now go to File->Open Notebook. Go to the
   Github tab. It will ask you to log into your GitHub account (if you don't have one, you should make one). Once you've done that, copy and paste 
   the URL: 
   https://github.com/cs124/pa0-python-jupyter-tutorial into the search box and hit enter. It should show:
   
            Repository: cs124/pa0-python-jupyter-tutorial
            Branch:  Master

   Click on pa0.ipynb below to load the notebook. You may want to make a copy so that you can save the file and return to it. Make sure to hit save (Ctrl + S on Windows and Cmd + S on Mac) early and often.

2. At the top of the notebook file, add the following cells and run them one by one:

2. At the top of the notebook file, add the following cells and run them one by one:

        Cell 1:
            !pip install -q condacolab
        
        Cell 2:
            import condacolab
            condacolab.install()
        
        Cell 3:
            %%writefile environment.yml
            name: cs124
            channels:
            - defaults
            dependencies:
            - jupyter
            - jupyter_client
            - numpy=2.1.3
            - python=3.10
            - matplotlib>=3.6
            - scikit-learn>=1.2
            - spacy>=3.7
            - nltk>=3.8
            - gensim>=4.3

        Cell 4:
            !conda env create -f environment.yml
        
        Cell 5:
            import os
            import sys

            # Manually configure to use cs124 environment
            os.environ['CONDA_DEFAULT_ENV'] = 'cs124'
            os.environ['PATH'] = '/usr/local/envs/cs124/bin:' + os.environ['PATH']
            sys.path.insert(0, '/usr/local/envs/cs124/lib/python3.10/site-packages')

            print("✓ Environment configured")
    
    Note: To use Google Colab to set up future PAs, you may want to modify the Cell 3 to add in additional dependencies that the PA requires.

## Part 3: Downloading the Notebook

Click on File -> Download -> Download `.ipynb` and upload it to Gradescope. 

Note: Future assignments may require additional files and folders to be submitted together as a zip file. See the assignment descriptions for more information.
