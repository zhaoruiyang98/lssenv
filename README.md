# lssenv
lss analysis environment manged by [uv](https://docs.astral.sh/uv/concepts/projects/workspaces/).

## Installation
Git clone this repo (including all submodules)
```bash
git clone --recurse-submodules https://github.com/zhaoruiyang98/lssenv.git 
```
and then (gcc and open-mpi are required)
```bash
uv sync
```
Then you can run `source ./venv/bin/activate` to activate a virtual python environment with all packages installed.

If you are a mac user with Apple silicon, you can install gcc and open-mpi from [homebrew](https://brew.sh/) using the following commands
```bash
brew install gcc@15
HOMEBREW_CC=gcc-15 HOMEBREW_CXX=g++-15 brew install open-mpi --build-from-source
```
Note that, open-mpi has to be built from source with environment variable `HOMEBREW_CC` set to `gcc-15` (surely using `gcc-16`, `gcc-17`, ... released in the future should also work). This is because by default homebrew installs a pre-compiled open-mpi library built with Apple Clang, which is not able to build the pfft-python library.