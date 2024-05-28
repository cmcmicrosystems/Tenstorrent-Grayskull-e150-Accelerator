# Getting Started with Tenstorrent Grayskull e150 Accelerator
This getting started guide outlines a comprehensive series of steps for accessing and running inference on the Grayskull e150 Accelerator. Beginning with the download and installation of CMC Microsystems CADPass, users are guided through authentication, acquisition of necessary details, and setup of necessary tools for interaction with the e150. Emphasizing practicality, the guide includes instructions for SSH access, identification of available accelerator cards, and activation of virtual environments. Users are also introduced to key tools like TT-SMI and offered guidance on copying demo examples for further exploration. Notably, the guide introduces various options to interact with the e150, including Python script execution and Jupyter Notebook usage, empowering users with practical approaches for model execution and experimentation. Lastly, it directs users to valuable open-source repositories for continued exploration and development.

The e150 DevKit is an introductory inference-only hardware kit coupled with two distinct software approaches: TT-Buda (top-down approach) and TT-Metalium (bottom-up approach). This combination provides a foundational platform for AI experimentation and development.

<p align="center">
  <img src="https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/20.png" alt="Image Alt Text">
</p>

For more details about Grayskull e150 Accelerator and the availabale ressources, visit [https://www.cmc.ca/tenstorrent-grayskull-e150-accelerator/](https://www.cmc.ca/tenstorrent-grayskull-e150-accelerator/)

To start using the Tenstorrent Grayskull™ e150 Accelerator, follow these steps:

## 1. Download and Install CADPass:
Download [CADPass](https://www.cmc.ca/cadpass/) from the provided link and install it on your system.
   
## 2. Login to CADPass:
Use your CMC microsystems credentials to log in to CADPass. After logging in, you will see the following window:
<p align="center">
  <img src="https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/0.png" alt="Image Alt Text">
</p>
   
## 3. Obtain AI Jupyter Tenstorrent Shortcut Details:
To access the shortcut details for AI Jupyter Tenstorrent, right-click on the application and choose "Shortcut details", as demonstrated in the following illustration:
<p align="center">
  <img src="https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/12.png" alt="Image Alt Text" style="width: 500px; height: 400px;">
</p>
  
## 4. Find the Server IP Address:
Within the shortcut details window, locate the server's IP address. In this instance, the IP address of the server is identified as 172.16.60.18.
<p align="center">
    <img src="https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/3.png" alt="Image Alt Text" style="width: 250px; height: 400px;">
</p>
  
## 5. SSH to the Server:
Use the acquired IP address to SSH into the server:
   ```
   ssh username@172.16.60.18                     
   ```

## 6. Check Available Accelerators:
Once connected to the server, type the following command to see the available accelerator cards in the system:
   ```
   lspci | grep accelerator
   ```
The execution of this command will present the available accelerator cards, corresponding to the Tenstorrent Grayskull™ e150 Accelerator:
   ```
username@tenstorrent:~$ lspci | grep accelerator
b1:00.0 Processing accelerators: Device 1e52:faca
ca:00.0 Processing accelerators: Device 1e52:faca
   ```
## 7. Create and Activate the virtual environment:
PyBuda™ is a comprehensive compute framework tailored for developing, executing, and analyzing machine learning workloads on Tenstorrent hardware. For detailed insights into this framework, please refer to the documentation available at: https://docs.tenstorrent.com/tenstorrent/v/tt-buda.
The TT-Buda software stack is adept at compiling AI/ML models sourced from diverse frameworks such as PyTorch and TensorFlow. It empowers users to execute these models across various methodologies on Tenstorrent hardware.
### A crucial distinction in terminology exists:
TT-Buda stands as the official AI/ML compiler stack for Tenstorrent. PyBuda serves as the Python interface to TT-Buda. This interface facilitates direct access to TT-Buda's functionalities from within Python, enabling users to seamlessly import model architectures and weights from PyTorch, TensorFlow, ONNX, and TFLite.
To activate  TT-Buda, execute the following command:
``` 
python3 -m venv .venv
source .venv/bin/activate
pip3 install --upgrade pip==24.0
wget https://github.com/tenstorrent/tt-buda/releases/download/v0.12.3/pybuda-gs-v0.12.3-ubuntu-20-04-amd64-python3.8.zip
unzip pybuda-gs-v0.12.3-ubuntu-20-04-amd64-python3.8.zip
pip install pybuda-0.1.240509+dev.gs.a84d92c-cp38-cp38-linux_x86_64.whl tvm-0.14.0+dev.tt.1955a63ea-cp38-cp38-linux_x86_64.whl torchvision-0.16.0+fbb4cc5-cp38-cp38-linux_x86_64.whl
pip install ipykernel
pip install jupyter
```

## 8. TT-SMI 
The Tenstorrent System Management Interface (TT-SMI) is a command-line utility designed to facilitate interactions with all Tenstorrent devices hosted on a system.
The primary aim of TT-SMI is to furnish users with a straightforward and user-friendly interface for gathering and presenting device, telemetry, and firmware information.
Furthermore, users can utilize TT-SMI to execute resets for Tensix cores on the Grayskull board.
To run tt-smi, execute the following command:
```
tt-smi
```
<div style="text-align:center">
    <img src="https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/4.png" alt="Image Alt Text">
</div>

For more details about tt-smi, visit: https://github.com/tenstorrent/tt-smi

## 9. Copy Examples to Your Home Directory
To copy the demo examples to your home directory, execute the following command:
```
cp -rf /CMC/tt-buda-demos/ .
```
Alternatively, you can clone the repository:
```
git clone --branch v0.12.3 --single-branch https://github.com/tenstorrent/tt-buda-demos.git
cd tt-buda-demos
```

At this stage, you have various options to interact with the e150:

- **Python Script Execution**: Execute Python scripts directly from the command line, allowing for efficient model inference on the e150 accelerator, enabling rapid development and testing.
  
- **Jupyter Notebook**: Use Jupyter notebooks, facilitating an interactive and collaborative environment for experimenting with code and data, promoting iterative development and documentation of workflows.

- **Docker**: It typically provides benefits such as easy deployment, scalability, and isolation of software environments, enhancing reproducibility and management of dependencies. 

## 10. Python Script Execution
Navigate to the ResNet model demo directory by executing:
```
cd model_demos/cv_demos/resnet/pytorch_resnet.py
```
Open the pytorch_resnet.py file in your editor to analyze it. To run PyTorch ResNet on Tenstorrent Grayskull e150 Accelerator, use the following command:
```
python pytorch_resnet.py
```

## 11. Jupyter Notebook
This section demonstrates the process of running Jupyter notebook examples on the e150, aimed at familiarizing users with the fundamentals of TT-Buda. These notebooks can be found in the directory tt-buda-demos/first_5_steps.

-**running_nlp_models.ipynb**: Running your first NLP model with TT-Buda.

-**running_cv_models.ipynb**: Running your first CNN model with TT-Buda.

-**batched_inputs.ipynb**: Learning how to run with batched inputs and how to benchmark models on TT-Buda.

-**serving_tt_models.ipynb**: Using FastAPI to host a model running on Tenstorrent hardware to build custom APIs.

Navigate to the first_5_steps directory and install the Jupyter kernel for Tenstorrent with the following command:
```
cd tt-buda-demos/first_5_steps
python -m ipykernel install --user --name=tt
```

## 12. Run Jupyter Notebook
Launch Jupyter Notebook with the following command:
```
jupyter notebook --no-browser --port=8888
```
<div style="text-align:center">
    <img src="https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/5.png" alt="Image Alt Text" style=" width: 1560px; height: 400px;">
</div>

## 13. Access Jupyter Notebook Locally
To access Jupyter Notebook from your local machine, use SSH tunneling with the following command:
```
ssh -N -f -L localhost:8888:localhost:8888 username@IPaddreass -p 22
```

Then, open the following link in your browser:
http://localhost:8888/

## 14. Authentication
Copy the token obtained from (12.) into the password or token field in the Jupyter Notebook interface.
<div align="center">
  <img src="https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/6.png" alt="Image Alt Text" style="width: 600px; height: 600px;">
</div>


## 15. Verify Jupyter Notebook Setup
After successful authentication, a Jupyter notebook page is loaded, displaying the available notebooks in the current directory, as depicted in the following figure:

<div align="center">
    <img src="https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/7.png" alt="Image Alt Text" style=" width: 1200px; height: 400px;">
</div>

## 16. Run examples
Click on one of the notebooks and ensure that the "tt" environment is enabled, as demonstrated in the following figure:
<div align="center">
    <img src="https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/8.png" alt="Image Alt Text" style=" width: 800px; height: 150px;">
</div>

Read through the notebook and execute each step meticulously to ensure smooth progress and accurate results.

## 17. Benchmarking

These commands are intended to set up an environment for benchmarking Tenstorrent's BUDA framework using specific models and tasks. Initially, a repository named "benchmarking" is cloned from GitHub, focusing on version "v0.12.3". The working directory is then changed to the "benchmarking" directory. Inside this directory, a Python virtual environment is created named ".venv" and activated. The pip3 command is used to upgrade pip to version 24.0. Next, a specific version of PyBUDA, optimized for the system, is downloaded and extracted. Subsequently, several Python packages are installed using pip, including PyBUDA, TVM, and torchvision, along with their respective dependencies specified in "requirements.txt". The PYTHONPATH is then exported to include the current directory. Finally, two benchmarking scripts are executed: the first one performs text classification using the BERT model, while the second one performs image classification using the ResNet-50 model with specific configurations and saves the output for analysis.

```
git clone --branch v0.12.3 --single-branch https://github.com/tenstorrent/benchmarking.git
cd benchmarking
python3 -m venv .venv
source .venv/bin/activate
pip3 install --upgrade pip==24.0
wget https://github.com/tenstorrent/tt-buda/releases/download/v0.12.3/pybuda-gs-v0.12.3-ubuntu-20-04-amd64-python3.8.zip
unzip pybuda-gs-v0.12.3-ubuntu-20-04-amd64-python3.8.zip
pip install pybuda-0.1.240509+dev.gs.a84d92c-cp38-cp38-linux_x86_64.whl tvm-0.14.0+dev.tt.1955a63ea-cp38-cp38-linux_x86_64.whl torchvision-0.16.0+fbb4cc5-cp38-cp38-linux_x86_64.whl
pip install -r requirements.txt
export PYTHONPATH=.
python benchmark.py -d tt -m bert -c base --task text_classification --save_output
python benchmark.py -d tt -m resnet -c resnet50 --task image_classification -mb 64 --loop_count 32 -opt 4 --save_output
```

## 17. Run Docker

These commands initiate the setup of an environment for running Tenstorrent's BUDA framework and its associated demos. Initially, a Docker image named "ghcr.io/tenstorrent/tt-buda/ubuntu-20-04-amd64/gs
.12.3" is pulled. Subsequently, a Docker container is launched, configured to utilize Tenstorrent hardware resources and necessary system resources, such as hugepages, with specific settings for shared memory and access capabilities. 

Within the container, system packages are updated, Git is installed, and a repository containing BUDA demos is cloned. Finally, the script "pytorch_resnet.py" from the cloned repository is executed, which likely demonstrates a convolutional neural network model using PyTorch's ResNet architecture.

```
docker pull ghcr.io/tenstorrent/tt-buda/ubuntu-20-04-amd64/gs:v0.12.3
docker run --rm -ti \
--device /dev/tenstorrent/0:/dev/tenstorrent/0 \
-v /dev/hugepages-1G:/dev/hugepages-1G \
--shm-size=4g \
--cap-add ALL \
ghcr.io/tenstorrent/tt-buda/ubuntu-20-04-amd64/gs:v0.12.3 bash

# in container
apt-get update && apt-get install -y git
git clone --branch v0.12.3 --single-branch https://github.com/tenstorrent/tt-buda-demos.git
cd tt-buda-demos
python model_demos/cv_demos/resnet/pytorch_resnet.py
```


### GitHub Links to Open Source Software Repositories
Find below the GitHub links to Tenstorrent's open-source software repositories, which you may find valuable:

1. [TT-Buda](https://github.com/tenstorrent/tt-buda)
2. [Budabackend](https://github.com/tenstorrent/tt-budabackend)
3. [TT-Metalium](https://github.com/tenstorrent-metal/tt-metal)
4. [Tutorials and Demos](https://github.com/tenstorrent/tt-buda-demos)
5. [Benchmarking Scripts (Now Public!)](https://github.com/tenstorrent/benchmarking)

