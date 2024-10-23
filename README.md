# Project Installation Guide

## Overview
This project is built upon the amazing [SPlisHSPlasH](https://github.com/InteractiveComputerGraphics/SPlisHSPlasH) library, which is an open-source solution for physically-based fluid simulation. If you're interested in the original work, it was created by [Jan Bender](https://animation.rwth-aachen.de/person/1/) and is available under the MIT license.

I've put together this guide to help you get started, based on my own experience setting everything up. While it follows the [official SPlisHSPlasH Windows documentation](https://splishsplash.readthedocs.io/en/latest/build_from_source.html#installation-instructions-windows), I've added some extra tips and explanations that I wish I had when I started.

## Prerequisites

Before we dive in, let's make sure you have all the necessary software installed

### Required Software
| Software | Version | Why do we need it? |
|----------|---------|-------------------|
| CMake | 3.31.0 | This is our build system generator - think of it as the conductor of our software orchestra! |
| Visual Studio | 15 2017 (15.9.67) | Our main development environment where we'll compile and run our code |
| g++ | 13.2.0 | The C++ compiler that will turn our code into something the computer can understand |

### Environment Setup
This part is super important, and it's where I initially got stuck! Here's what you need to do:

1. **MSBuild Configuration**
   - First, add this path to your system's PATH variable:
     ```
     C:\Program Files (x86)\Microsoft Visual Studio\2017\Community
     ```
   - Then, create a new environment variable called `VCTargetspath` with this value:
     ```
     C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\VC\VCTargets
     ```
   - **Important**: Restart your computer after making these changes !

## Installation Steps

### 1. Clone Repository
First things first, clone the repository by opening your terminal and running:
```bash
git clone https://github.com/InteractiveComputerGraphics/SPlisHSPlasH.git
```
Choose a location where you want to store your project - I recommend somewhere easy to find and without spaces in the path name.

### 2. Build Configuration
Now comes the fun part! We'll use CMake to set up our build environment:

1. Open CMake GUI (look for "cmake-gui" in your start menu)
2. **Important note for experienced users**: If you've used CMake before with newer versions of Visual Studio, you'll need to clean your cache:
   - Go to `File -> Delete Cache`
   - This ensures we use the correct Visual Studio version (2017)
3. Set up your directories:
   - For "Where is the source code": Browse to your SPlisHSPlasH folder
   - For "Where to build the binaries": Same folder but with `/build` at the end
4. Click `Configure`, then `Generate`

> **Don't panic!** You might see this message during building:
> ```
> Performing Test CMAKE_HAVE_LIBC_PTHREAD - Failed
> Looking for pthread_create in pthreads - not found
> Looking for pthread_create in pthread - not found
> ```
> I spent quite some time worrying about this, but this seems to be actually normal! pthread is a standard library that's already part of your system, so you can safely ignore these messages.

### 3. Build Process
Almost there! Now we'll build the actual project:

1. Click "Open Project" in CMake GUI
2. Visual Studio will open automatically. Here's what to do:
   - Look for the Solution Explorer on the right side
   - Right-click on "Solution 'SPlisHSPlasH' (32 projects)"
   - Select "Build Solution"
   - When it's done (after some time...), you'll find a new "bin" folder in your main project directory

### 4. Running Your First Simulation
The moment we've been waiting for! Let's run a simulation:

1. Open PowerShell
2. Navigate to your SPlisHSPlasH directory
3. Type this command:
   ```powershell
   bin/SPHSimulator_d.exe
   ```
4. You'll see a window pop up with various scene files (basically, they're .json files) - these are pre-made simulations you can try out. Pick one that looks interesting and watch the magic happen!

## Troubleshooting
Running into problems? Don't worry, it happens to everyone (it will...)! Here are some common issues and solutions:

- **Environment variables not working**: Double-check the paths and make sure you've restarted your computer
- **Build fails**: Ensure you have enough disk space and that all prerequisites are installed correctly


Good luck with your fluid simulation journey! 🚀 If this guide helped you, consider giving it a star on GitHub!