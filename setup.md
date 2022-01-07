# Setting up
To begin, let's make sure we have the pre-requisites installed.

## 1. Install Anaconda.

SLEAP is written entirely in Python. **Anaconda** is a Python environment manager that makes it easy to install SLEAP and its necessary dependencies without affecting other Python software on your computer.

If you already have Anaconda installed, you can skip to the next step.

To install Anaconda, we recommend using the lightweight Miniconda version:

1. Go to: https://docs.conda.io/en/latest/miniconda.html#latest-miniconda-installer-links
2. Download the latest version for your OS.
3. Follow the installer instructions.

**On Windows**, just click through the installation steps. I personally prefer using the following settings:
- Install for: All Users (requires admin privileges)
- Destination folder: C:/Miniconda3
- Advanced Options: Add Miniconda3 to the system PATH environment variable
- Advanced Options: Register Miniconda3 as the system Python 3.9
These will make sure that Anaconda is easily accessible from most places on your computer.

**On Linux**, it might be easier to do this straight from the terminal (<kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>T</kbd>) with this one-liner:
```
wget -nc https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh && bash Miniconda3-latest-Linux-x86_64.sh -b && ~/miniconda3/bin/conda init bash
```
Restart the terminal after running this command.

**On Macs**, you can run the graphical installer using the pkg file, or this terminal command:
```
wget -nc https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh && bash Miniconda3-latest-MacOSX-x86_64.sh -b && ~/miniconda3/bin/conda init zsh
```
For M1 Macs, you might need to use a different version:
```
wget -nc https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh && bash Miniconda3-latest-MacOSX-arm64.sh -b && ~/miniconda3/bin/conda init zsh
```

### Check that Anaconda is installed.

When opening a terminal, you might now see a `(base)` in front of your username. This denotes that you're in the `base` conda environment and everything should be good to go.

If you don't see it, try typing `conda env list`. If you get an error about `conda` not being found, you might not have installed it or it can't be accessed.

**Windows**: Unless you use a custom terminal app like [Cmder](https://cmder.net) or [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701), the easiest terminal to use is the **Anaconda Prompt (Miniconda3)** which is installed together with conda.

## 2. Install GPU drivers (optional).
If you are running SLEAP on a laptop or workstation with an NVIDIA GPU, you'll be able to train and predict much faster using [CUDA](https://developer.nvidia.com/cuda-toolkit). **If you don't have a GPU, feel free to skip to the next step.**

**Note**: This is currently only supported on Windows and Linux. Macs can run SLEAP, but we do not (yet) support acceleration using newer Mac chips (e.g., M1).

The SLEAP installation will take care of all of the dependencies required to do this, but you will need to just make sure you have the NVIDIA GPU drivers installed. This should not affect any other software on your system that relies on the GPU.

1. Go to: https://nvidia.com/drivers
2. Select your GPU version and OS and hit "Search". The "Download Type" doesn't matter (Game Ready Drivers are usually stable.)
3. Download the release, follow the steps in the installer, and restart your computer.

## 3. Install SLEAP.

For this tutorial, we will be using the [SLEAP v1.2.0a2 pre-release](https://github.com/murthylab/sleap/releases/tag/v1.2.0a2).

To install it with conda, open up your terminal (e.g., **Anaconda Prompt (Miniconda3)**) and run:
```
conda create -y -n sleap_v1.2.0a2 -c sleap -c sleap/label/dev -c nvidia sleap=1.2.0a2
```
This will create an environment named `sleap_v1.2.0a2`. You can change this name with the `-n` argument of the command above, but we recommend using a fresh environment when trying new (and especially pre-release) versions of SLEAP. This will allow you to have multiple versions installed in case you need to make sure your code doesn't break in 6 months when you need to submit your paper revisions!

**Macs**: We do not currently provide a conda package for Macs, but you can still install SLEAP like this:
```
conda create -y -n sleap_v1.2.0a2 python=3.7 && conda activate sleap_v1.2.0a2 && pip install sleap==1.2.0a2 && conda deactivate
```

Alright, now let's activate the environment:
```
conda activate sleap_v1.2.0a2
```
(You should now see the `(base)` prefix change to `(sleap_v1.2.0a2)`).

And make sure that SLEAP works by importing it:
```
python -c "import sleap; sleap.versions(); sleap.system_summary()"
```

## 4. Download this repository

You can download the data in this repository with:
```
git clone https://github.com/talmolab/sleap-tutorial-uo
```

Or by downloading and extracting from this link: https://github.com/talmolab/sleap-tutorial-uo/archive/refs/heads/main.zip

This is not required if you have your own data, but it'll help you follow along if you don't.