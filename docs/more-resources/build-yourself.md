---
layout: page
title: Build by Yourself
parent: More Resources
nav_order: 8
---

# Build by Yourself

## Seekers Python

### Requirements

You need at least Python 3.10 to run this project.

### Clone Locally

```sh
git clone https://github.com/seekers-server.git
```

### Install Dependencies

Setup a virtual environment:

```sh
python -m venv venv
```

Install dependencies with:

```
pip install -r requirements
```

### Get Stubs

Check if the stubs are installed. The stubs are located at `seekers/grpc`.

If they are missing, you can install them from our release page or compile them on your own.
You can check out the stub release [here](https://github.com/seekers-dev/seekers-py/releases/download/v0.1.0/stubs.zip). Extract the files and drop the stubs folder in the location described above.

If you want to compile them on your own, you must first install the `requirements-dev.txt` and then run `compile_protos.sh`.

### Create Binaries

If you want to create binaries on your own, you can use cx_Freeze. Please note that this step is optional.

First, if you want to setup a virtual environment and install all requirements for building the binaries with only one command, you can use:

```sh
bash freeze -i
```

Alternativly, if you already installed the dependecies like described in the step above, you can just use the command below:

```
pip install cx_Freeze
```

For building the binaries for the `run_seekers.py` file, you can use:

```sh
bash freeze -s
```

For building the binaries for the `run_client.py` file, you can use:

```sh
bash freeze -c
```

If you want to test your binaries, use the following command:

```sh
bash freeze -t
```

### Finished!

You can find your binaries at the `dist` folder or you can use `run_seekers.py` to run it.

## Seekers Server

### Clone Locally

```sh
git clone https://github.com/seekers-server.git
```

### Requirements

You need at least Java 11 to run this project.

### Compile Project

You compile the project with maven. You do not need to install maven, as it is already installed with the maven wrapper.

```sh
./mvnw install
```

### Finished!

You can find your jar file in the `target` folder.