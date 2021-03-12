# Neper安装 — Polycrystal Generation and Meshing

官网地址https://neper.info/

Github地址https://github.com/rquey/neper

## Ubuntu下安装Neper

Windows用户可以使用虚拟机进行安装，这里采用Ubuntu 20.04.2.0 LTS版本。

Ubuntu官网：https://ubuntu.com/download/desktop

### 1.Ubuntu准备工作

```bash
sudo apt install cmake
sudo apt install g++
sudo apt install gcc
sudo apt-get install libnlopt.dev
sudo apt-get install povray
sudo apt-get install libgmsh-dev
sudo apt-get install imagemagick
```

- Dependencies: [GSL](http://www.gnu.org/software/gsl/), [muParser](http://beltoforion.de/article.php?a=muparser) (included in Neper), [nanoflann](https://github.com/jlblancoc/nanoflann) (included in Neper), [Gmsh](http://gmsh.info/), [libScotch](http://www.labri.fr/perso/pelegrin/scotch), [POV-Ray](http://www.povray.org/)

### 2.安装GSL

```bash
curl -L -O http://mirrors.ustc.edu.cn/gnu/gsl/gsl-2.6.tar.gz
tar -xzf gsl-2.6.tar.gz -C ~/gsl-2.6
cd ~/gsl-2.6
sudo ./configure
sudo make
sudo make install
```

### 3.从GitHub上下载Neper软件包

```bash
git clone https://github.com/rquey/neper.git
```

### 4.编译并测试Neper环境

```bash
sudo apt-get install mpich
cd ~/neper/src
mkdir build
cd build
cmake ..
make
sudo make install
make test
```

此时neper环境配置成功，使用方法可以查看文档https://neper.info/docs/neper.pdf。