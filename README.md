# Nvidia-GPU-Setup-for-Windows-and-WSL2.0
Step-by-step instructions on setting up the Nvidia GPU for Deep Learning tasks in [Windows 11](https://www.microsoft.com/software-download/windows11) and [WSL2.0](https://learn.microsoft.com/en-us/windows/wsl/install)

> ⚠️**Caution**: TensorFlow 2.10 was the last TensorFlow release that supported GPU on native-Windows. Starting with TensorFlow 2.11, you will need to install TensorFlow in WSL2, or install tensorflow-cpu and, optionally, try the TensorFlow-DirectML-Plugin. I use: `python -m pip install tensowflow==2.9.0`

- [ ] Install Windows 11 Home.
    > **_Note:_** You can install any version of Windows 11.
- [ ] Goto [WSL2 Install](https://learn.microsoft.com/en-us/windows/wsl/install) and install WSL2 - Windows Subsystem for Linux 2. 
- [ ] New Linux installations, installed using the `wsl --install` powershell command, will be set to WSL 2 by default.
- [ ] Run the command `wsl –install -d Ubuntu-22.04` in Powershell with administrator mode.
- [ ] Restart the computer. After restarting, `ubuntu` command on PowerShell will take you to the Linux terminal. You will be prompted to enter a new **username** and **password** for unix. And start the linux on WSL2.
- [ ] In WSL Run `python3 -V` and you will see that the Python version is **3.10.6**
    > **_Note:_** Your Python version might be different as long as it is `>= 3.9 < 3.12`
- [ ] Make sure your computer has a CPU with an AVX instruction set having a CPU flag of AVX2 or AVX512, and a GPU in the list of [Nvidia Compute Compatibility](https://developer.nvidia.com/cuda-gpus). 
    > **_Windows:_** Google your CPU model, example: [ci7 11700](https://ark.intel.com/content/www/us/en/ark/products/212279/intel-core-i711700-processor-16m-cache-up-to-4-90-ghz.html). [Here](https://ark.intel.com/content/www/us/en/ark/products/212279/intel-core-i711700-processor-16m-cache-up-to-4-90-ghz.html) you can see in `Advanced Technologies >> Instruction Set Extensions`.

    > **_Linux|WSL2.0:_** Run command `lscpu | grep avx` in the terminal. If there's any **avx** text found then your CPU has **AVX Instructionset**.
- [ ] Goto [Tensorflow Installation](https://www.tensorflow.org/install) and checkout the prerequisites. Everything to install is given there.
    > **_Note:_** It gives you the option to build from source, use a docker dontainer or a PIP installation.

    > **_Note:_** I use [PIP installation](https://www.tensorflow.org/install/pip).

- [ ] Install [windows C++ Redistributable](https://learn.microsoft.com/en-US/cpp/windows/latest-supported-vc-redist?view=msvc-170). I normally install [Microsoft Visual Studio](https://visualstudio.microsoft.com/).
- [ ] Goto [PIP for Windows WSL2.0](https://www.tensorflow.org/install/pip#windows-wsl2_1) for more instructions.
- [ ] Now you need to install the following: **[HELP](https://docs.nvidia.com/cuda/wsl-user-guide/index.html)**
  - [ ] [Nvidia Windows Driver x86](https://www.nvidia.com/Download/index.aspx) Install the nvidia driver for _**windows**_, launch it and login on it for which you will need to authenticate via email.
    > **_Note:_** The **CUDA** driver installed on Windows host will be stubbed inside the WSL 2 as <span style="color: green;">libcuda.so</span>, therefore <span style="color: red;">**users must not install any NVIDIA GPU Linux driver within WSL 2**</span>
  - [ ] You can also just add the following at the end of a **`~/.bashrc`** file
    ```bash
    export PATH=/usr/local/cuda-11.8/bin${PATH:+:${PATH}}
    export LD_LIBRARY_PATH=/usr/local/cuda-11.8/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
    export PATH=$PATH:/home/<YOUR_USERNAME>/.local/bin
    export arch=x86_64
    export distro=ubuntu2204
    ```
    > **_Note:_** The above script is for x86_64 architecture and ubuntu 22.04 distribution. You can change that according to your system.
- [ ] Docker Support
- [ ] TensorRT
- [ ] CUDA Toolkit and Cuda Developer Tools
- [ ] RAPIDS
- [ ] NCCL
