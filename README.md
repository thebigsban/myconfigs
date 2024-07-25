# My Settings

Configs and files for general development. 

## bashrc
```bash 
################# 
# TERMINAL HISTORY
################
alias mkdir="mkdir -pv"
PROMPT_COMMAND='history -a'
HISTTIMEFORMAT="%F %T "


################
# GENERAL 
###############
alias ll="ls -la"
alias tree='find . -print | sed -e "s;[^/]*/;|____;g;s;____|; |;g"'

#################
# CONDA (Windows)
################
. C:/Users/banst/anaconda3/etc/profile.d/conda.sh
. /c/Users/banst/anaconda3/etc/profile.d/conda.sh

#####################
# DOCKER RELATED
####################
alias de="docker exec -it"
alias dec="docker exec -it container"
alias dstopall='docker stop $(docker ps -a -q)'
alias drmall='docker rm $(docker ps -a -q)'
dbuild(){
    docker build -t "$1" .
}

drun(){
    docker run --name "$1" -it -d --gpus all "$1"
}

dbash() {
    docker exec -it "$1" //bin/bash
}

dcpall(){
    docker cp . "$1"://usr/local/"$2"
}
```

## Dockerfiles

Dockerfiles and their use cases. Sporadically updated. 

## `cuda-pytorch`
From the [Nvidia container catalog. ](https://catalog.ngc.nvidia.com/orgs/nvidia/containers/pytorch). Comes with PyTorch and Nvidia related toolkits (CUDA, cuDNN, nvcc, etc.) on Ubuntu. Good for building/running/testing CUDA kernels to be imported and used in PyTorch. Takes a while to build for the first time (>10min). 

## `ubuntu-cpp`
Unminimized Ubuntu container with C++ and basic networking (`socket`) capabilities. Used for developing applications in C++ that require some form of networking (for example, a database). 

## `pytorch-vanilla`
Just PyTorch with some minimal Nvidia related stuff (CUDA, cuDNN, not nvcc). Some other Python tools installed as well but nothing special. 




