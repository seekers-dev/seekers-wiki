---
layout: page
title: Setup
permalink: /setup/
nav_order: 3
---

# Seekers Python

## Requirements

You need at least Python 3.10 to run this project.

## Download

Download the latest release [here](https://github.com/seekers-dev/seekers-py/releases/tag/v0.1.0).

## Install dependencies

Setup a virtual environment:

```sh
python -m venv venv
```

Install dependencies with:

```
pip install -r requirements
```

## Get stubs

Check if the stubs are installed. The stubs are located at `seekers/grpc`.

If they are missing, you can install them from our release page or compile them on your own.
You can check out the stub release [here](https://github.com/seekers-dev/seekers-py/releases/download/v0.1.0/stubs.zip). Extract the files and drop the stubs folder in the location described above.

If you want to compile them on your own, you must first install the `requirements-dev.txt` and then run `compile_protos.sh`.

# Seekers Java

## Requirements

You need at least Java 11 to run this project.

## Download

Download the latest snapshot [here](https://github.com/seekers-dev/seekers-javahttps://github.com/seekers-dev/seekers-java).

## Compile project

You can use docker or maven to compile the project.

### Docker

You can use docker to build the project

### Maven

```sh
./mvnw install
```