# Data Science Anaconda-Ubuntu Dev Container

## Intro

This repo is used to setup an Anaconda working environment, with VSCode Dev Containers, for the Johns Hopkins University Data Science course (en685648).

Created during the Fall 2025 semester.

### POCs

- Author: Dominick Dimpfel
- Professor: Andrew Stewart

## Benefits to using

- It runs on any machine as an Ubuntu Linux OS with UNIX commands.
- All dependencies are handled by the dev container, so any results you create should be runnable by anyone else with the container.

## Setup

1. Install [VSCode](https://code.visualstudio.com/download)
2. Locally install the Dev Containers VSCode extension.

   - In VSCode, on the left toolbar, click the extensions icon (the 3 boxes and 1 diamond icon).
   - It is authored by Microsoft, click install.

3. Pull this repository to your local development folder for this course.

   - Open a shell/command prompt then run the following commands

   ```sh
   cd /path/to/your/workspace

   git clone https://github.com/ddimpfel/data-science-anaconda-ubuntu-dev-container.git
   ```

4. Open the VSCode command pallette:

   - Ctrl/Cmd+Shift+P or click on the top bar in VSCode and type '>'

5. Run the 'Dev Containers: Reopen in Container' command.

   - This will take up to 5 minutes to build the image at first.
   - You can open the logs (bottom right popup) to see what stage it is on or to debug any errors.

   <span style='color: yellow;'>NOTE:</span> You should only build the image one time, make sure to use the 'Reopen in Container' command to avoid rebuilding the image.

6. Confirm your Conda environment is setup:

   - Run the test.ipynb file to confirm the dependency versions.
   - Run 'conda env list' to check you are using the correct Conda environment:
     1. Open a new terminal in the container's VSCode window by going to Terminal > New Terminal in the titlebar (this should open bash).
     2. You should see an '\*' next to the en685648 environment.

## Using the Container

You should now have a built container for all course development. When you'd like to reopen the dev container, simply open your local workspace in VSCode and rerun the 'Dev Containers: Reopen in Container' command.

To stop the container, you can simply close VSCode or run 'Dev Containers: Close Remote Connection'.

<span style='color: green;'>Recommended:</span> Install [Docker Desktop](https://www.docker.com/products/docker-desktop/) to view and manage the container.

- https://www.youtube.com/watch?v=hwoWBdNilVI

### TODO

- make workspace environment name variable (en685648)
- setup vscode extensions file and install script for container
