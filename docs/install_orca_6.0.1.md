# Installing ORCA 6.0.1

ORCA 6.0.1 is very easy to install. One must simply unpack the `.tar.gz`
compressed file into the appropriate directory.

## Create the necessary directory structure

1. Navigate to your `/opt` directory.

    ```bash
    cd /<path-to-proj-shared>/<username>/opt
    ```

2. Copy the orca source tarball to the `/opt` directory

    ```bash
    cp /<path-to-ngp-comp-chem-repo>/orca_6_0_1_linux_x86-64_shared_openmpi416_avx2.tar.xz .
    ```

3. Unpack the source code

    ```bash
    tar xvf orca_6_0_1_linux_x86-64_shared_openmpi416.tar.xz
    ```

4. Rename the ORCA directory

    ```bash
    mkdir orca
    mv orca_6_0_1_linux_x86-64_shared_openmpi416 orca/6.0.1
    ```


## Download and unpack the OpenMPI 4.1.6 source code

```bash
wget https://download.open-mpi.org/release/open-mpi/v4.1/openmpi-4.1.6.tar.gz
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
run faster on supercomputing clusters. So, the command to run is:

```bash
./configure --prefix=/<path-to-opt>/openmpi/4.1.6 --with-pmix=/<path-to-pmix> --with-libevent=/<path-to-libevent> --with-ucx=/<path-to-ucx>
```

The configure script will output much information once this command is run.
Now we are ready for the 'build' phase of the installation.

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
