
# SPIRV Codegen in a JIT engine

This example creates a simple function to add +1 to an array and store the resullt in a new array, generates its LLVM IR and converts it into SPIRV IR, and submits it to the Unified Runtime.

## Requirements

Intel GPUs are the best to work with, for other GPUs extra drivers and plugins are required.

Apart from system requirements, installing Anaconda or Miniconda is recommended.

## Understanding the file structure
```bash
codegen.cpp - connects to the drivers and the runtime and calls the function to generate SPIRV, also contains code for the array and adding +1 to it

helpers.cpp - contains the function generate_plus_one_spv() that generates LLVM IR and converts it to SPIRV

helpers.h - header file of helpers.cpp
```

## 1) Anaconda Installation

Run the following commands on you terminal
```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
export PATH="<path_to_miniconda_binaries>:$PATH"
source ~/.bashrc
```

## 2) Clone the Unified Runtime repo
```bash
git clone https://github.com/oneapi-src/unified-runtime
```

## 3) Build the examples

#### Using Conda
```bash
conda env create -f third_party/deps.yml
conda activate examples
mkdir build && cd build
cmake .. -DUR_BUILD_ADAPTER_L0=ON -DUR_BUILD_EXAMPLE_CODEGEN=ON
make
./bin/codegen
```

#### Without using Conda
```bash
mkdir build && cd build
cmake .. -DUR_BUILD_ADAPTER_L0=ON -DUR_BUILD_EXAMPLE_CODEGEN=ON -DLLVM_DIR=/usr/lib/llvm-13/cmake
make
./bin/codegen
```
