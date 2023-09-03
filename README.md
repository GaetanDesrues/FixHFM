# FixHFM

## Install

    git clone git@github.com:GaetanDesrues/FixHFM.git && cd FixHFM

    source <your-venv>/bin/activate
    pip install -r requirements.txt

    cd fixhfm/_/HamiltonFastMarching/Interfaces/PythonHFM
    python setup.py build_ext --inplace
    pip install -e .

    cd -
    pip install -e .

You can now use `from fixhfm import HFM_Isotropic3, HFM_Riemann3`.

*Notes below*

## From ElecModel

A modified version of HFM containing only the required modules were shipped with the ElecModel code.
See [this file](fixhfm/_/HamiltonFastMarching/Headers/Specializations/CMakeLists.txt).

I also shipped a modified version of pybind11 (see `pybind_missing_dir` in `setup.py`).

**Install HFMpy**:

    cd $ELEC_MODEL/extern/HamiltonFastMarching/Interfaces/PythonHFM
    python setup.py build_ext --inplace
    pip install -e .

**Check HFMpy installation**:

    cd $ELEC_MODEL
    python -c 'from HFMpy import HFM_Isotropic3; print(HFM_Isotropic3)'
    # <module 'HFMpy.HFM_Isotropic3' from '/.../HFMpy/HFM_Isotropic3.cpython-39-x86_64-linux-gnu.so'>

## Generate wheel

    rm -rf build dist
    python setup.py sdist bdist_wheel
