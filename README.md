# Getting Started with Tenstorrent Grayskull e150 Accelerator
To start using the Tenstorrent Grayskull™ e150 Accelerator, follow these steps:
1. **Download and Install CADPass:**
   Download [CADPass](https://www.cmc.ca/cadpass/) from the provided link and install it on your system.
   
2. **Login to CADPass:**
   Use your CMC microsystems credentials to log in to CADPass. After logging in, you will see the following window:
   ![Image Alt Text](https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/0.png)
   
3. **Obtain AI Jupyter Tenstorrent Shortcut Details:**
   Right-click on AI Jupyter Tenstorrent and select "Shortcut details" as shown in the following figure:

   ![Image Alt Text](https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/12.png)
   
4. **Find the Server IP Address:**
   In the shortcut details window, you will find the IP address of the server. In this case, the IP address of the server is 172.16.60.18

   ![Image Alt Text](https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/3.png)
   
6. **SSH to the Server:**
   Use the obtained IP address to SSH into the server using the following command:
   ```
   ssh username@172.16.60.18                     
   ```
7. **Check Available Accelerators:**
Once connected to the server, type the following command to see available accelerator cards in the system:
   ```
   lspci | grep accelerator
   ```
The output of this command will display the available accelerator cards, such as:
   ```
   yassine@tenstorrent:~$ lspci | grep accelerator
b1:00.0 Processing accelerators: Device 1e52:faca
ca:00.0 Processing accelerators: Device 1e52:faca
   ```
8. **Activate the virtual environment:**
PyBuda ™ is a compute framework used to develop, run, and analyze ML workloads on Tenstorrent hardware.
for more details about the framework, visit: https://docs.tenstorrent.com/tenstorrent/v/tt-buda
The TT-Buda software stack can compile AI/ML models from several different frameworks such as PyTorch and Tensorflow, and execute them in many different ways on Tenstorrent hardware.

Note on terminology:

TT-Buda is the official Tenstorrent AI/ML compiler stack and PyBuda is the Python interface for TT-Buda. PyBuda allows users to access and utilize TT-Buda's features directly from Python. This includes directly importing model architectures and weights from PyTorch, TensorFlow, ONNX, and TFLite.

``` 
yassine@tenstorrent:~$ source /CMC/tt/bin/activate
(tt) yassine@tenstorrent:~$
```
10. run TT-SMI
```
(tt) yassine@tenstorrent:~$ tt-smi
```

![Image Alt Text](https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/4.png)

12. copy examples to your home directory
```
cp -rf /CMC/tt-buda-demos/ .
```
Alternatively, you can clone the repo as follow:
```
git clone https://github.com/tenstorrent/tt-buda-demos
```
13. run resnet
``` 
cd /home/yassine/tt-buda-demos/model_demos/cv_demos/resnet
```
Open pytorch_resnet.py in editor and analyze the file. to run pytorch_resnet on Tenstorrent Grayskull e150 Accelerator, execute the following command:
```
python pytorch_resnet.py
```


First 5 Things To-Do
For a simple, 5-step, starting guide on learning the basics of TT-Buda please visit first_5_steps.

In that directory, you will find the following user guides:

1_install_ttbuda.md -> Installation guide for TT-Buda
2_running_nlp_models.ipynb -> Run your first NLP model with TT-Buda
3_running_cv_models.ipynb -> Run your first CNN model with TT-Buda
4_batched_inputs.ipynb -> Learn how to run with batched inputs and how to benchmark models on TT-Buda
5_serving_tt_models.ipynb -> Use FastAPI to host a model running on Tenstorrent hardware to build custom APIs



16. Jupyter notebook setup
```
cd tt-buda-demos/first_5_steps
python -m ipykernel install --user --name=tt
Installed kernelspec tt in /home/yassine/.local/share/jupyter/kernels/tt
```

17. run Jupyter notebook
```
jupyter notebook --no-browser --port=8888
```

![Image Alt Text](https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/5.png)



16. on a local machine
ssh -N -f -L localhost:8888:localhost:8888 username@IPaddreass -p 22

17. open in browser:
open jupyter notebook lin in browser:
http://localhost:8888/


17. past the token from pic5 to the password or token field as shown in the following figure:
![Image Alt Text](https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/6.png)



18. at this stage, you have successfully launched Jupyter notebook on the server:
![Image Alt Text](https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/7.png)


 
19. open 3_running_cv_models.ipynb
a new window open with the notebook loaded. make sure the environement tt is enabeled as shown the following figure:
![Image Alt Text](https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/8.png)

21. read and execute each step of the notebook 

## Additional ressources:
	1. TT-Buda: https://github.com/tenstorrent/tt-buda
	2. budabackend: https://github.com/tenstorrent/tt-budabackend
	3. TT-Metalium: https://github.com/tenstorrent-metal/tt-metal
	4. tutorials and demos: https://github.com/tenstorrent/tt-buda-demos
benchmarking scripts (now public!): https://github.com/tenstorrent/benchmarking![image](https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/assets/9284879/f0800e6b-ca13-4104-9adc-cad1d6c23152)
