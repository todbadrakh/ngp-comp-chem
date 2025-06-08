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


