---
tags:
  - reference/CLI
date created: Thu, Apr 4th 2024, 3:49 am
date modified: Sun, Nov 3rd 2024, 1:36 am
---

# conda

**Install Miniconda/Anaconda with Python**
```powershell

# Specify the Miniconda/Anaconda version to install
MINICONDA_VERSION="Miniconda3-latest-Linux-x86_64.sh"

# Download and install Miniconda/Anaconda using the specified version
curl -O https://repo.anaconda.com/miniconda/$MINICONDA_VERSION
bash $MINICONDA_VERSION

# Update conda to the latest version in the base environment
conda update -n base conda

# Create a new environment named 'myenv'
conda create --yes --name myenv

# Create a new environment named 'new_env_name' with Python version 3.12
conda create --name new_env_name python=3.12

# Activate an environment
conda activate myenv

# Deactivate the current environment
conda deactivate

# List all environments
conda env list

# Install a package in the current environment
conda install --yes packagename

# Install a specific version of a package
conda install --yes packagename=1.0.1

# Update a package in the current environment
conda update --yes packagename

# Uninstall a package from the current environment
conda remove --yes packagename

# List all packages in the current environment
conda list

# Search for a package in the Anaconda package index
conda search packagename

# Create a clone of an environment named 'myenv' called 'myclone'
conda create --yes --name myclone --clone myenv

# Delete the environment named 'myenv'
conda env remove --yes --name myenv

# Set the auto_activate_base to false
conda config --set auto_activate_base false

# Automatically activate 'myenv' upon opening a new terminal
echo "conda activate myenv" >> ~/.zshrc

# Downgrade Python to version 3.11
conda install --yes python=3.11

# Rename the environment name 'env-oldname' to 'env-newname'
conda rename -n env-oldname env-newname

# Update conda in the base environment
conda update -n base conda

# Install and set the new solver libmamba for faster dependency resolution
conda install -n base conda-libmamba-solver
conda config --set solver libmamba

# Remove env
conda remove --name ENVIRONMENT --all

``` 

# Remote server

Send local files to remote
`scp -r /Users/Jiachi/Desktop/RA_Prof.ChenNan/extracter.py zlab@nan.d2.comp.nus.edu.sg:/mnt/ssd2/home/zlab/users/Jiachi`

Check this https://storm.cis.fordham.edu/~yli/documents/CISC2200Fall21/5_TransferFilesScpMac.pdf for more reference

## Run codes in the background in server

To use `screen` to run `./race_full.py` in one session and `./race_last.py` in another, here’s how you can do it:

1. **Start a New Screen Session for `race_full.py`**:
   - Create and name the session for `race_full.py`:
     ```bash
     screen -S race_full
     ```
   - Inside this screen session, run the script:
     ```bash
     ./race_full.py
     ```
   - Detach from the session by pressing `Ctrl+A` then `D`. This will keep `race_full.py` running in the background.

2. **Start Another Screen Session for `race_last.py`**:
   - Create and name the session for `race_last.py`:
     ```bash
     screen -S race_last
     ```
   - Inside this screen session, run the script:
     ```bash
     ./race_last.py
     ```
   - Detach from this session as well using `Ctrl+A` then `D`.

3. **Check and Manage Screen Sessions**:
   - To view your active sessions, use:
     ```bash
     screen -ls
     ```
   - You should see both `race_full` and `race_last` listed, either as `(Attached)` or `(Detached)`.

4. **Reattach to a Session**:
   - If you want to reattach to a session, specify its name. For example:
     ```bash
     screen -r race_full
     ```
   - To reattach to `race_last`:
     ```bash
     screen -r race_last
     ```

This setup will keep both scripts running independently, and you can freely detach and reattach as needed to monitor their progress.

## Q&A

1. **Will the CSV Output Appear Automatically After the Scripts Finish?**
   - If each script is set up to save output directly to a `.csv` file (e.g., with `pandas.to_csv("output.csv")`), the files will be created automatically as long as the script completes successfully. You don’t need to do anything further, and the output files will be available on the server as soon as each script finishes.
   - If your scripts are instead printing output to the terminal, you won’t see that output directly in the `.csv` files. To ensure the output goes to `.csv` files, make sure each script is saving the data directly within the code.

2. **Will the Scripts Stop Running If You Lose Connection with the Server?**
   - No, if you start each script within a `screen` session and then detach the session (using `Ctrl+A D`), they will continue to run in the background, even if you disconnect from the server.
   - `screen` is designed to keep sessions alive independently of your SSH connection, so you can log out without stopping the scripts.

In short, once you set up each screen session to run and detach them, your scripts will run to completion and save their `.csv` output files without needing further intervention. You can reconnect to the server anytime to check on the files or reattach to the sessions if needed.

## kill screen

To stop all `screen` sessions that are running your scripts, you can follow these steps:

1. **List All Active Screen Sessions**:
   - First, check all active screen sessions:
     ```bash
     screen -ls
     ```

2. **Terminate Each Session**:
   - For each session you want to stop, use the following command to quit:
     ```bash
     screen -S session_name -X quit
     ```
   - Replace `session_name` with the name or ID shown in the `screen -ls` output, like `race_full` or `race_last`.
   - For example:
     ```bash
     screen -S race_full -X quit
     screen -S race_last -X quit
     ```

3. **Kill All Screen Sessions at Once (Optional)**:
   - If you want to terminate all screen sessions at once, use:
     ```bash
     screen -ls | grep Detached | cut -d. -f1 | awk '{print $1}' | xargs kill
     ```
   - This command finds all detached sessions and kills them. Be careful, as this will stop all running `screen` processes.

After running these commands, all the screen sessions running your scripts will be stopped, and the scripts will no longer be running in the background.

## copy from file from folder A to folder B

`cp example.txt ~/Documents`

# vscode/cursor can not load new conda env/kernel automatically

`cmd shift p` -> reload the window

reference: [python - VSCode Jupyter cannot update kernels automatically - Stack Overflow](https://stackoverflow.com/questions/65858621/vscode-jupyter-cannot-update-kernels-automatically)

## check cpu usage

[How to Check Linux CPU Usage or Utilization? {Easy Way}](https://phoenixnap.com/kb/check-cpu-usage-load-linux)

# Brew

First, uninstall the package:

`brew uninstall <package>`

Then, remove all the unused dependencies:

`brew autoremove`

# Remove Login Item in MAC

Uninstalling an app involves more than just deleting the app from /Applications. You need to use an "uninstaller" like the free [AppCleaner](https://freemacsoft.net/appcleaner/). I also use the paid apps "Remove-It" and "App Cleaner and Uninstaller". You can (in decreasing order of preference):

1. A few apps (e.g. those from Adobe) have uninstaller apps. Use these if you can.

2. Reinstall the app, then uninstall with AppCleaner. This will delete the app and remove associated files including background tasks.

3. Poke around in
4. ~/Library/LaunchAgents,
5. /Library/LaunchAgents,
6. /Library/LaunchDaemons
7. `~/Library/Caches/com.runningwithcrayons.Alfred/Workflow Data/com.benjamino.emoji_wine` afled caches

4. Put up with the undeleted background tasks most of which are probably not actually running (because of what you have deleted) and any others are probably not doing any harm.

https://forums.macrumors.com/threads/how-to-uninstall-login-items.2376298/

