# MOOSE安装 — Multiphysics Object-Oriented Simulation Environment

MOOSE一款开元的、支持并行计算的有限元框架。

<img src=".\figs\moose_logo.png" style="zoom:50%;" />

官网地址https://mooseframework.inl.gov/

## Ubuntu下安装DAMASK

Windows用户可以使用虚拟机进行安装，这里采用Ubuntu 20.04.2.0 LTS版本。

Ubuntu官网：https://ubuntu.com/download/desktop

### 1.Ubuntu准备工作

```bash
sudo apt install curl
sudo apt install make
sudo apt install git
sudu apt install gcc
curl -L -O https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
```

注意，需要手动安装包含libquadmath库的gcc，否则可能导致动态链接库的错误。

### 2.安装Conda环境及依赖包

```bash
bash Miniconda3-latest-Linux-x86_64.sh -b -p ~/miniconda3
export PATH=$HOME/miniconda3/bin:$PATH
conda config --add channels conda-forge
conda config --add channels idaholab
conda create --name moose moose-libmesh moose-tools
conda activate moose
```

### 3.从GitHub上下载MOOSE软件包

```bash
mkdir ~/projects
cd ~/projects
git clone https://github.com/idaholab/moose.git
cd moose
git checkout master
```

### 4.编译并测试MOOSE环境

```bash
cd ~/projects/moose/test
make -j 4
./run_tests -j 4
```

### 5.Uninstall Conda MOOSE Environment

```bash
conda deactivate
conda remove --name moose --all
```

### 6.Conda环境迁移

通过Conda命令可以将当前环境下的所有依赖存储在`env.yaml`中。

```bash
conda env export > moose.yaml
conda env create -f moose.yaml
```

打包本地Conda环境并迁移至目标PC。

```bash
pip install conda-pack
conda pack -n moose
mkdir ~/miniconda3/envs/moose
tar -xzf moose.tar.gz -C ~/miniconda3/envs/moose
```

