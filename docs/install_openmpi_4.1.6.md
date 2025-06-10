# Building OpenMPI 4.1.6

OpenMPI is an implementation of the Message Passing Interface (MPI) that allows
parallel processes. ORCA 6.0.1 requires OpenMPI 4.1.6 and we will now install
it.

## Setup environment

We will use the AMD Optimized Compiler (AOCC) to install OpenMPI. In order to
do that, we must load some environment modules, which are files you can load
that make certain software available to you. All you have to do is run the
commands:

```bash
source <nsp>
module load aocc
```

Now the C compiler `clang`, C++ compiler `clang++` and Fortran compiler
`flang` are available to use. You can check by running the commands:

```bash
which clang
which clang++
which flang
```

The output should be the location of the compiler executables. One last
thing to do is to create environment variables for each compiler so that
the installer knows for sure which compiler to use:

```bash
export CC=clang
export CXX=clang++
export FC=flang
```

Now we are ready to compile some programs!

## Create the necessary directory structure

We will keep things organized by creating a directory for our software
installations. It is customary for Linux to keep user-installed software in
the `/opt` directory, so we will follow that convention and create our own
`/opt` directory in our project directory.

1. Navigate to your project directory.

    ```bash
    cd /<path-to-proj-shared>/<username>/
    ```

2. Create an `opt` directory where software will be installed.

    ```bash
    mkdir opt
    ```

3. Create a directory where OpenMPI 4.1.6 will be installed.

    ```bash
    mkdir -p opt/openmpi
    ```

## Download and unpack the OpenMPI 4.1.6 source code

We will use the `wget` command to download the compressed source code in
`.tar.gz` ("tarball") format, then uncompress ("unpack") it using the
`tar` program.

1. Download the source code.

```bash
wget https://download.open-mpi.org/release/open-mpi/v4.1/openmpi-4.1.6.tar.gz
```

2. Unpack the tarball.
```bash
tar xvf openmpi-4.1.6.tar.gz
```

This will create a folder called `openmpi-4.1.6` which contains the source
code. 

## Configure the installation

Software installations in the Linux command-line interface involve first
choosing the options for the installed program - this is called 
'configuration.' We will now configure the OpenMPI 4.1.6 installation with
the following options:

1. Install the program in the `/<path-to-proj-shared>/<username>/opt/openmpi/4.1.6`
   folder by using the `--prefix` option.

2. Link the program to PMIx library using the `--with-pmix` option and its
   dependency `libevent` using the `--with-libevent` option.

3. Link the program to the UCX library using the `--with-ucx` option.

The PMIx and UCX libraries are low-level communication libraries that help MPI
run faster on supercomputing clusters. So, the commands to run is:

```bash
cd openmpi-4.1.6
./configure --prefix=/<path-to-opt>/openmpi/4.1.6 --with-pmix=/<path-to-pmix> --with-libevent=/<path-to-libevent> --with-ucx=/<path-to-ucx>
```

The configure script will output much information once this command is run.
These are all various print statements recording each action the configuration
script is taking. Now we are ready for the 'build' phase of the installation.

## Build the executables

Now we simply 'build' the program using the `make` program, using 8 parallel
processes via the `-j 8` flag.

1. Build the binaries
    ```bash
    make -j 8
    ```

2. Install the binaries
    ```bash
    make -j 8 install
    ```

We have installed OpenMPI 4.1.6!
