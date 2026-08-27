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
    package file that supports vasp version 6.6.1 and gcc version 15.2.0.

3.  Get the the vasp 6.6.1 source and pseudopotential tarballs from
    [VASP Portal](https://vasp.at). and place them in into `vasp-env` directory.
    
    - Only Primary contact person or the License signatory can download the
      sources. If you do not have access to the sources ask your license owner
      or primary contact person to download the sources for you.
    - If you need to build older version of VASP, check which versions are
      supported by the Spack recipe from the file
      `spack-env/spack_repo/my_repo/packages/vasp/package.py` download
      best suitable version, and edit the vasp version number in file
      `vasp-env/spack.yaml`.
       
5. Install vasp with

    ```console
    export SPACK_USER_CACHE_PATH=$TMPDIR/spack
    export SPACK_DISABLE_LOCAL_CONFIG=true
    source /appl/soft/spack/v2026_03/spack/share/spack/setup-env.sh

    cd spack-env
    spack -e . install
    ```

    If Spack complains about mismatching checksum, you can add option `--no-checksum`
    to the above `spack -e .install` command, if you are sure the vasp source is from
    trusted source [VASP Portal](https://vasp.at) .

The VASP executables can be used by referring to them with full pathname in the batch scripts,
with for example

```console
srun /projappl/<project>/vasp-env/view/bin/vasp_std
```
