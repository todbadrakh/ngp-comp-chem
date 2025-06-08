# Building OpenMPI 4.1.6

OpenMPI is an implementation of the Message Passing Interface (MPI) that allows
parallel processes. ORCA 6.0.1 requires OpenMPI 4.1.6 and we will now install
it.

## Create the necessary directory structure

We will keep things organized by creating a directory for our software
installations. It is customary for Linux to keep user-installed software in
the `/opt` directory, so we will follow that convention.

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
    mkdir -p opt/openmpi/4.1.6
    ```

## Download and unpack the OpenMPI 4.1.6 source code

    ```bash
    wget https://download.open-mpi.org/release/open-mpi/v4.1/openmpi-4.1.6.tar.gz
    tar xvf openmpi-4.1.6.tar.gz
    ```
    This will create a folder called openmpi-4.1.6 which contains the source
    code. 

## Configure the installation

    Software installations in the Linux command-line interface involve first
    choosing the options for the installed program - this is called 
    'configuration.' We will now configure the OpenMPI 4.1.6 installation with
    the following options:

    a. Install the program in the `/<path-to-proj-shared>/<username>/openmpi/4.1.6`
    folder by using the `--prefix` option.

    b. Link the program to MPIx library using the `--with-mpix` option.

    c. Link the program to the UCX library using the `--with-ucx` option.







