# VASP build instructions for Roihu at CSC

Short instructions:

1.  Create a CSC computing project in [MyCSC service](https://my.sc.fi),
    which members all must have a valid VASP license, if you do not already have
    a suitable project.

2.  Go to the project's projappl directory `/projappl/<project>`, and clone repository

    ```console
    git clone https://github.com/jlento/vasp-env.git
    ```

    This repository contains spack environment definition file, and an updated
    package file that supports vasp version 6.6.0 and gcc version 15.2.0.

3.  Get the the vasp 6.6.0 source and pseudopotential tarballs from
    [VASP Portal](https://vasp.at) (only Primary contact person or the License
    signatory can do this?), and place them in into `vasp-env` directory.

4. Install vasp with

    ```console
    export SPACK_USER_CACHE_PATH=$TMPDIR/spack
    export SPACK_DISABLE_LOCAL_CONFIG=true
    source /appl/soft/spack/v2026_03/spack/share/spack/setup-env.sh

    cd spack-env
    spack -e . install
    ```

The VASP executables can be used directly in the batch scripts, with for example

```console
srun /projappl/<project>/vasp-env/view/bin/vasp_std
```
