# Getting Started with Tenstorrent Grayskull e150 Accelerator

Welcome to the world of Tenstorrent Grayskull™ e150 Accelerator! Let's kickstart your journey with these simple steps:

### 1. Download and Install CADPass
Begin by downloading [CADPass](https://www.cmc.ca/cadpass/) from the provided link. Install it on your system to proceed.

### 2. Login to CADPass
Use your CMC Microsystems credentials to log in to CADPass. Once logged in, you'll be greeted with the CADPass interface.
![Image Alt Text](https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/0.png)

### 3. Obtain AI Jupyter Tenstorrent Shortcut Details
Right-click on AI Jupyter Tenstorrent and select "Shortcut details" to obtain essential details for accessing the accelerator.

![Image Alt Text](https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/12.png)

### 4. Find the Server IP Address
Locate the server's IP address in the shortcut details window. Note down the IP address provided, such as 172.16.60.18.

![Image Alt Text](https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/3.png)

### 5. SSH to the Server
SSH into the server using the obtained IP address. Execute the following command:
```
ssh username@172.16.60.18
```


### 6. Check Available Accelerators
Once connected, check available accelerator cards by executing:

```
lspci | grep accelerator
```

This command will display available accelerator cards in the system.

```
yassine@tenstorrent:~$ lspci | grep accelerator
b1:00.0 Processing accelerators: Device 1e52:faca
ca:00.0 Processing accelerators: Device 1e52:faca
```

### 7. Activate the Virtual Environment
Activate the virtual environment using PyBuda™, a compute framework for ML workloads on Tenstorrent hardware. Visit this link for more details about PyBuda.

bash
Copy code
source /CMC/tt/bin/activate
### 8. Run TT-SMI
Now, run TT-SMI to manage accelerator settings efficiently.

### 9. Copy Examples to Your Home Directory
Copy demo examples to your home directory for convenient access. You can either copy them directly or clone the repository using Git.

### 10. Run ResNet Model
Navigate to the directory containing the ResNet model demo. Analyze the file and execute the following command to run the demo:

bash
Copy code
python pytorch_resnet.py
First 5 Things To-Do
For a simpler starting guide, explore the "first_5_steps" directory, containing guides on installation, running NLP and CV models, working with batched inputs, and serving models with FastAPI.

### 11. Jupyter Notebook Setup
Head to the "first_5_steps" directory and install the Jupyter kernel for Tenstorrent.

bash
Copy code
python -m ipykernel install --user --name=tt
### 12. Run Jupyter Notebook
Launch Jupyter Notebook on the server using:

bash
Copy code
jupyter notebook --no-browser --port=8888
Image Alt Text

### 13. Access Jupyter Notebook Locally
To access Jupyter Notebook from your local machine, utilize SSH tunneling.

bash
Copy code
ssh -N -f -L localhost:8888:localhost:8888 username@IPaddress -p 22
### 14. Open Jupyter Notebook in Browser
Open the following link in your browser to access Jupyter Notebook: http://localhost:8888/

### 15. Paste Token
Paste the token from the displayed image into the password or token field in the Jupyter Notebook interface.

### 16. Verify Jupyter Notebook Setup
Ensure successful Jupyter Notebook launch on the server for seamless operation.

### 17. Open CV Models Notebook
Navigate to the "3_running_cv_models.ipynb" notebook and ensure the "tt" environment is enabled.

Additional Resources
### - TT-Buda
### - Budabackend
### - TT-Metalium
### - Tutorials and Demos
### - Benchmarking Scripts (now public!): https://github.com/tenstorrent/benchmarking
Let's embark on an exciting journey with Tenstorrent Grayskull e150 Accelerator!
