### Installing Anaconda

1. Download the Anaconda installer from [anaconda.com/download](https://www.anaconda.com/download):

   ```bash
   wget https://repo.anaconda.com/archive/Anaconda3-2025.12-2-Linux-x86_64.sh
   ```

2. Install Anaconda on Ubuntu:

   ```bash
   bash Anaconda3-2025.12-2-Linux-x86_64.sh
   ```

3. Apply the changes:

   ```bash
   source ~/.bashrc
   ```

4. Verify the installation:

   ```bash
   conda --version
   ```

5. If you get `conda: command not found`:

   5.1. Initialize conda manually:

   ```bash
   ~/anaconda3/bin/conda init bash
   ```

   5.2. Apply the changes again:

   ```bash
   source ~/.bashrc
   ```

   5.3. Verify once more:

   ```bash
   conda --version
   ```

### Running Jupyter

1. Start Jupyter from the Ubuntu (WSL) terminal:

   For Jupyter Notebook:

   ```bash
   jupyter notebook --no-browser --port=8888
   ```

   For JupyterLab:

   ```bash
   jupyter lab --no-browser --port=8888
   ```

2. Copy the URL from the terminal output and open it in a web browser on Windows:

   ```
   http://localhost:8888/?token=abc123def456...
   ```

3. If everything works, you can set up aliases to avoid typing the full command every time (optional):

   3.1. Open `~/.bashrc` in a text editor:

   ```bash
   nano ~/.bashrc
   ```

   Add the following lines:

   ```bash
   alias jn='jupyter notebook --no-browser --port=8888'
   alias jl='jupyter lab --no-browser --port=8888'
   ```

   3.2. Apply the changes:

   ```bash
   source ~/.bashrc
   ```

   3.3. Now you can start Jupyter by simply typing `jn` for Notebook or `jl` for JupyterLab.

4. To configure Jupyter Notebook to start automatically when WSL launches (optional):

   4.1. Add the following snippet to `~/.bashrc` (logs will be written to `~/jupyter.log`):

   ```bash
   # Auto-start Jupyter if not already running
   if ! pgrep -f "jupyter-notebook" > /dev/null 2>&1; then
       nohup jupyter notebook --no-browser --port=8888 > ~/jupyter.log 2>&1 &
   fi
   ```

   4.2. Restart WSL to apply the changes:

   ```bash
   wsl --shutdown
   ```

   4.3. Verify that the Jupyter service is running:

   ```bash
   jupyter notebook list
   ```
