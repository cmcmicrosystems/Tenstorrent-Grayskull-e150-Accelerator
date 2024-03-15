# Getting Started with Tenstorrent Grayskull e150 Accelerator
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
yassine@tenstorrent:~$ lspci | grep accelerator
b1:00.0 Processing accelerators: Device 1e52:faca
ca:00.0 Processing accelerators: Device 1e52:faca
   ```
## 7. Activate the virtual environment:
PyBuda™ is a comprehensive compute framework tailored for developing, executing, and analyzing machine learning workloads on Tenstorrent hardware. For detailed insights into this framework, please refer to the documentation available at: https://docs.tenstorrent.com/tenstorrent/v/tt-buda.
The TT-Buda software stack is adept at compiling AI/ML models sourced from diverse frameworks such as PyTorch and TensorFlow. It empowers users to execute these models across various methodologies on Tenstorrent hardware.
### A crucial distinction in terminology exists:
TT-Buda stands as the official AI/ML compiler stack for Tenstorrent. PyBuda serves as the Python interface to TT-Buda. This interface facilitates direct access to TT-Buda's functionalities from within Python, enabling users to seamlessly import model architectures and weights from PyTorch, TensorFlow, ONNX, and TFLite.
To activate  TT-Buda, execute the following command:
``` 
yassine@tenstorrent:~$ source /CMC/tt/bin/activate
(tt) yassine@tenstorrent:~$
```

## 8. TT-SMI 
The Tenstorrent System Management Interface (TT-SMI) is a command-line utility designed to facilitate interactions with all Tenstorrent devices hosted on a system.
The primary aim of TT-SMI is to furnish users with a straightforward and user-friendly interface for gathering and presenting device, telemetry, and firmware information.
Furthermore, users can utilize TT-SMI to execute resets for Tensix cores on the Grayskull board.
To run tt-smi, execute the following command:
```
(tt) yassine@tenstorrent:~$ tt-smi
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
git clone https://github.com/tenstorrent/tt-buda-demos
```

At this stage, you have various options to interact with the e150:

- **Python Script Execution**: Execute Python scripts directly from the command line, allowing for efficient model inference on the e150 accelerator, enabling rapid development and testing.
  
- **Jupyter Notebook**: Use Jupyter notebooks, facilitating an interactive and collaborative environment for experimenting with code and data, promoting iterative development and documentation of workflows.

- **Docker**: It typically provides benefits such as easy deployment, scalability, and isolation of software environments, enhancing reproducibility and management of dependencies. 

## 10. Python Script Execution
Navigate to the ResNet model demo directory by executing:
```
cd /home/yassine/tt-buda-demos/model_demos/cv_demos/resnet
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

## 14. Paste Token
Paste the token obtained from (12.) into the password or token field in the Jupyter Notebook interface.
<div align="center">
  <img src="https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/6.png" alt="Image Alt Text" style="width: 600px; height: 600px;">
</div>


## 15. Verify Jupyter Notebook Setup
<div align="center">
    <img src="https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/7.png" alt="Image Alt Text" style=" width: 1200px; height: 400px;">
</div>

## 16. open 3_running_cv_models.ipynb
A new window will open with the notebook loaded. Ensure that the "tt" environment is enabled, as demonstrated in the following figure:
<div align="center">
    <img src="https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/8.png" alt="Image Alt Text" style=" width: 800px; height: 150px;">
</div>

## 17. Executing Notebook Steps
Read through the notebook and execute each step meticulously to ensure smooth progress and accurate results.

### GitHub Links to Open Source Software Repositories
Find below the GitHub links to Tenstorrent's open-source software repositories, which you may find valuable:

1. [TT-Buda](https://github.com/tenstorrent/tt-buda)
2. [Budabackend](https://github.com/tenstorrent/tt-budabackend)
3. [TT-Metalium](https://github.com/tenstorrent-metal/tt-metal)
4. [Tutorials and Demos](https://github.com/tenstorrent/tt-buda-demos)
5. [Benchmarking Scripts (Now Public!)](https://github.com/tenstorrent/benchmarking)

