# 简易安装
DeePMD-kit有很多简单的的安装方式，你可以按需选择。如果你希望独立编译，可以跳转到下一部分。

完成了安装流程后，文件中会自带两个已经编译好的程序：DeePMD-kit(`dp`)和LAMMPS(`lmp`)，你可以尝试输入`dp -h`和`lmp -h`来获取帮助信息，考虑到你会选择并行地训练模型和运行LAMMPS，`mpirun`同样已编译好并可供使用。

## 安装离线软件包

CPU和GPU版本的离线软件包都在可以[the Releases page](https://github.com/deepmodeling/deepmd-kit/releases)中找到

由于Github对文件大小的限制，一些安装包被拆分成两个文件，我们可以将拆分文件都下载下来再进行合并。

    cat deepmd-kit-2.0.0-cuda11.3_gpu-Linux-x86_64.sh.0 deepmd-kit-2.0.0-cuda11.3_gpu-Linux-x86_64.sh.1 > 
    deepmd-kit-2.0.0-cuda11.3_gpu-Linux-x86_64.sh

## 利用Conda安装
DeePMD-kit可以利用[Conda](https://github.com/conda/conda)安装，不过首先需要安装好[Anaconda](https://www.anaconda.com/products/individual#download-section)或者[Miniconda](https://docs.conda.io/en/latest/miniconda.html)	

安装好Anaconda或Miniconda之后，我们可以创建一个包含CPU版本的DeePMD-kit和LAMMPS的虚拟环境

    conda create -n deepmd deepmd-kit=*=*cpu libdeepmd=*=*cpu lammps-dp -c https://conda.deepmodeling.org

同理，也可以创建包含GPU版本的虚拟环境

    conda create -n deepmd deepmd-kit=*=*gpu libdeepmd=*=*gpu lammps-dp cudatoolkit=11.3 horovod -c https://conda.deepmodeling.org
CUDA Toolkit版本可以按需从10.1或11.3中选择

如果你想安装指定版本的DeePMD-kit，例如2.0.0：

    conda create -n deepmd deepmd-kit=2.0.0=*cpu libdeepmd=2.0.0=*cpu lammps-dp=2.0.0 horovod -c https://conda.deepmodeling.org
创建虚拟环境后，每次使用前需要激活环境：

    conda activate deepmd


## 利用docker安装

DeePMD-kit同样可以通过docker安装

获取CPU版本：

    docker pull ghcr.io/deepmodeling/deepmd-kit:2.0.0_cpu

获取GPU版本：

    docker pull ghcr.io/deepmodeling/deepmd-kit:2.0.0_cuda10.1_gpu
获取ROCm版本：

    docker pull deepmodeling/dpmdkit-rocm:dp2.0.3-rocm4.5.2-tf2.6-lmp29Sep2021

如果你想从源码开始安装DeePMD-kit，请点[此处](https://docs.deepmodeling.org/projects/deepmd/en/master/install/install-from-source.html)
