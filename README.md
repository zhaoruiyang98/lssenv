# lssenv
lss analysis environment manged by [uv](https://docs.astral.sh/uv/concepts/projects/workspaces/).

## Installation
Git clone this repo (including all submodules)
```bash
git clone https://github.com/zhaoruiyang98/lssenv.git
```
initialize submodules
```bash
cd lssenv
git submodule update --depth 1 --init packages/
```
and then build and install packages (gcc and open-mpi are required)
```bash
uv sync
```
Then you can run `source ./venv/bin/activate` to activate a virtual python environment with all packages installed.

### Mac user
If you are a mac user, you can install gcc and open-mpi from [homebrew](https://brew.sh/) using the following commands
```bash
brew install gcc@15
HOMEBREW_CC=gcc-15 HOMEBREW_CXX=g++-15 brew install open-mpi --build-from-source
```
Note that, open-mpi has to be built from source with environment variable `HOMEBREW_CC` set to `gcc-15` or higher version. This is because by default homebrew installs a pre-compiled open-mpi library built with Apple Clang, but Apple clang cannot build the pfft-python library.