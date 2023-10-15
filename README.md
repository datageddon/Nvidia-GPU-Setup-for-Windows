# Nvidia-GPU-Setup-for-Windows-and-WSL2.0
Step-by-step instructions on setting up the Nvidia GPU for Deep Learning tasks in [Windows 11](https://www.microsoft.com/software-download/windows11) and [WSL2.0](https://learn.microsoft.com/en-us/windows/wsl/install)

> ⚠️**Caution**: TensorFlow 2.10 was the last TensorFlow release that supported GPU on native-Windows. Starting with TensorFlow 2.11, you will need to install TensorFlow in WSL2, or install tensorflow-cpu and, optionally, try the TensorFlow-DirectML-Plugin

- [ ] Install Windows 11 Home.
    > **_Note:_** You can install any version of Windows 11.
- [ ] Goto [WSL2 Install](https://learn.microsoft.com/en-us/windows/wsl/install) and install WSL2 - Windows Subsystem for Linux 2.
- [ ] Make sure your computer has a CPU with an AVX instruction set having a CPU flag of AVX2 or AVX512, and a GPU in the list of [Nvidia Compute Compatibility](https://developer.nvidia.com/cuda-gpus). Here you can see in `Advanced Technologies >> Instruction Set Extensions`. 
    > **_Windows:_** Google your CPU model, example: [ci7 11700](https://ark.intel.com/content/www/us/en/ark/products/212279/intel-core-i711700-processor-16m-cache-up-to-4-90-ghz.html)

    > **_Linux|WSL2.0:_** Run command `lscpu | grep avx` in the terminal. If there's any **avx** text found then your CPU has **AVX Instructionset**.
- [ ] Goto [Tensorflow Installation](https://www.tensorflow.org/install) and checkout the prerequisites. Everything to install is given there.
    > **_Note:_** It gives you the option to build from source, use a docker dontainer or a PIP installation.

    > **_Note:_** I use [PIP installation](https://www.tensorflow.org/install/pip).

- [ ] Install [windows C++ Redistributable](https://learn.microsoft.com/en-US/cpp/windows/latest-supported-vc-redist?view=msvc-170).
- [ ] [PIP for Windows WSL2.0](https://www.tensorflow.org/install/pip#windows-wsl2_1)