# lssenv
lss analysis environment managed by [uv](https://docs.astral.sh/uv/concepts/projects/workspaces/).

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

### For mac users
If you are a mac user, you can install gcc (not clang) and open-mpi from [homebrew](https://brew.sh/) using the following commands
```bash
brew install gcc@15
HOMEBREW_CC=gcc-15 HOMEBREW_CXX=g++-15 brew install open-mpi --build-from-source
```
Note that, open-mpi has to be built from source with environment variable `HOMEBREW_CC` set to `gcc-15` or higher version. This is because by default homebrew installs a pre-compiled open-mpi library built with Apple Clang, but Apple clang cannot build the pfft-python library.

Then you need export the environment so that the correct compiler will be used when building libraries
```bash
export CC=/opt/homebrew/bin/gcc-15
export CXX=/opt/homebrew/bin/g++-15
```
You can put the above commands to your `~/.zshrc` file.

## Update the environment
There may be more packages added to this repo in the future. To update, please run the following commands
```bash
git pull
git submodule update --depth 1 --init packages/
uv sync
```

Note that, submodules under directory `projects` are reserved for personal/collaborative use, which may or may not be public repos.