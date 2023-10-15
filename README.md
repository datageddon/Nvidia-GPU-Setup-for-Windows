# Nvidia-GPU-Setup-for-Windows-and-WSL2.0
Step-by-step instructions on setting up the Nvidia GPU for Deep Learning tasks in [Windows 11](https://www.microsoft.com/software-download/windows11) and [WSL2.0](https://learn.microsoft.com/en-us/windows/wsl/install)


- [ ] Make sure your computer has a CPU with an AVX instruction set having a CPU flag of AVX2 or AVX512, and a GPU in the list of [Nvidia Compute Compatibility](https://developer.nvidia.com/cuda-gpus). Here you can see in `Advanced Technologies >> Instruction Set Extensions`. 
    > **_Windows:_** Google your CPU model, example: [ci7 11700](https://ark.intel.com/content/www/us/en/ark/products/212279/intel-core-i711700-processor-16m-cache-up-to-4-90-ghz.html)

    > **_Linux:_** Run command `lscpu | grep avx` in the terminal. If there's any **avx** text found then your CPU has **AVX Instructionset**.
