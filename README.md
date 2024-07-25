# Gresino

Gresino is a patch-scheduling algorithm for automated program repair (APR) that aims to improve the efficiency of APR tools.
The patch space is large and it takes long to build and test each patched program.
Gresino detects more valid patches by using grey-box algorithm.

## Environments & Setup

### Environment
- Python >= 3.8
- JDK 1.8
- [Defects4j](https://github.com/rjust/defects4j) 1.2.0
- Maven

### Preparing the patch space

Gresino takes as input the patch space to explore and the patch-scheduling algorithm to use. Regarding the patch space, Gresino currently provides an option to use the patch space of one of the following 8 program repair tools:

1. ```Tbar```
2. ```Avatar```
3. ```kPar```
4. ```Fixminer```
5. ```AlphaRepair```
6. ```Recoder```
7. ```SRepair```
8. ```SelfAPR```

To construct the patch space provided by one of the above tools, see the README file for the tool. For example, the README file of ```Tbar``` is available at [TBar/README.md](TBar/README.md). We also provide a Python script that automates patch-space preparation. See [experiments](./experiments/).


### Setting up Gresino
Gresino is implemented in Python3. Gresino is in the [Gresino](./Gresino/) directory. To set up Gresino, do the following:
```
$ cd Gresino
$ python3 -m pip install -r requirements.txt
```

## How to reproduce our experiment
All reproduction scripts and their descriptions are available in the [experiments](./experiments/) directory.



## Running Gresino
The implementation of Gresino is available in the [Gresino](./Gresino) directory. To run Gresino, do the following:
```
$ cd Gresino
$ python3 gresino.py [options] -- {test_command}
```
More details are available in [Gresino](./Gresino/README.md).

### Running Gresino via Docker
To run Gresino via Docker, install 
- [docker](https://www.docker.com/)

Plus, you should install the following to utilize GPU for learning-based tools.
- [NVIDIA driver](https://www.nvidia.com/download/index.aspx)
- [nvidia-docker](https://github.com/NVIDIA/nvidia-docker)

Then, build the docker image with the Dockerfile.
```
$ docker build -t gresino .
```

## How to add a new APR tool
To add a new APR tool, it should store two kind of files: patch candidates and meta-information about them.
