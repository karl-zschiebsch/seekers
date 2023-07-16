[![Python Version 3.9/3.10](https://github.com/seekers-dev/seekers/actions/workflows/python-app.yml/badge.svg)](https://github.com/seekers-dev/seekers/actions/workflows/python-app.yml)

# seekers
* An artificial intelligence programming challenge targeted at students.
* AIs compete by controlling bouncy little circles ("seekers") trying to collect the most goals.
* Based on Python 3.9 and pygame.

![image](https://user-images.githubusercontent.com/37810842/226148194-e5b55d57-ed84-4e71-869b-d062b101b345.png)

## This repository contains
1. Python implementation of the Seekers Game
2. Seekers gRPC server
3. Seekers gRPC client

* Players can join the Seekers Game in two ways:
  1. <a name="join-method-new"></a>as gRPC clients (new and safe way)
  2. <a name="join-method-old"></a>as a local file whose `decide`-function is called directly from within the game (old and unsafe way)
     * This is discouraged as it allows players to access the game's internals and cheat. See [this issue](https://github.com/seekers-dev/seekers/issues/1).
     * useful for debugging/AI-developement

## How to run
* Install python 3.9 or higher
* Install the packages in [`requirements.txt`](requirements.txt).
  ```shell
  python -m pip install -r requirements.txt
  ```
  alternatively:
  ```shell
  pip install -r requirements.txt
  ```
  Depending on how you installed python, you might have to use `py` or `python3` instead of `python`.

### Using gRPC
#### Compile gRPC stubs manually
* Install packages in [`seekers/grpc/requirements-dev.txt`](seekers/grpc/requirements-dev.txt). 
* Execute [`seekers/grpc/compile_protos.sh`](seekers/grpc/compile_protos.sh).

#### Download gRPC stubs
  * Download the necessary grpc stubs from [seekers-dev/seekers-grpc](https://github.com/seekers-dev/seekers-grpc/releases) and put the folder `./stubs/` in `./seekers/grpc/`.

### Run a Python Seekers Game (and a gRPC server)
This will:
* start a Seekers Game
* run a gRPC server by default
* join the specified AIs (see [old join method](#join-method-old))
```shell
python run_seekers.py <AI files>
```

### Run a Python AI as a Seekers gRPC client
You will need a separate server running. This can be the server above, or, for example, [the Java implementation](https://github.com/seekers-dev/seekers-api).

```shell
python run_client.py <AI file>
```

## License
You can, and are invited to, use, redistribute and modify seekers under the terms
of the GNU General Public License (GPL), version 3 or (at your option) any
later version published by the Free Software Foundation.
