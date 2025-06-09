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

We are now ready to do chemistry!
