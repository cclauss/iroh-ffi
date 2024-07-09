# Iroh Python

This is the [Iroh](https://github.com/n0-computer/iroh) python api!

The api was generated using [uniffi-rs](https://github.com/mozilla/uniffi-rs).

All iroh classes, methods, functions, and enums contain docstrings.

The current best way to understand how the iroh python api can be used is to check out our [tests](https://github.com/n0-computer/iroh-ffi/tree/main/python).

We currently ship binary wheels on pypi for:
- amd64 win
- x86_64 manylinux2014
- aarch64 manylinux2014
- arm64 macosx
- x86_64 macosx

If you need another platform you will have to build from source using the repository at https://github.com/n0-computer/iroh-ffi/


## Development setup

- Install [`maturin`](https://www.maturin.rs/installation) for python development and packaging.
- Install `uniffi-bindgen` with `pip`
- `maturin build` will build a wheel in `targets/wheels`
- `maturin develop` will build the wheel and install into the current virtual env. It expects you to use `virtualenv` to manage your virtual environment.

## Building portable wheels

Invoking `maturin build` will build a wheel in `target/wheels`.  This
will likely only work on your specific platform. To build a portable
wheel for linux use:

```
docker run --rm -v $(pwd):/mnt -w /mnt quay.io/pypa/manylinux2014_x86_64 /mnt/build_wheel.sh
```

## Running the example

This repo includes a very small, but working example for using the python API, at [`python/main.py`](python/main.py).

To run it with the latest version of iroh published on pypi:

```sh
# Install iroh with pip
pip install iroh
# Run the example
python3 python/main.py --help
```

To run with a locally-built wheel:

```sh
# Create and activate a virtual env
virtualenv .
source ./bin/activate
# Install dependencies
pip install uniffi-bindgen
# Build wheel
maturin develop
# Run the example
python3 python/main.py --help

```

## Running the tests

This repo includes python tests. To run them, execute the following commands from the repo root. This will build the wheel and run all python tests.

```sh
# Create and activate a virtual env
virtualenv .
source ./bin/activate
# Install dependencies
pip install uniffi-bindgen pytest pytest-asyncio
# Build wheel
maturin develop
# Run tests
python -m pytest
```
