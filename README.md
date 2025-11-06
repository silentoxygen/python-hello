 # python-hello

A minimal Flask "Hello World" application packaged with a Dockerfile. This repository demonstrates a tiny Python web app that responds with "Hello from Python!" at the root path and includes instructions for running locally and in Docker.

## Contents

- `App/main.py` - small Flask application.
- `App/requirements.txt` - Python dependencies (Flask).
- `Docker/Dockerfile` - example Dockerfile to build a container image.

## Prerequisites

- Python 3.7+ (for running locally)
- pip (to install dependencies)
- Docker (optional, for building and running the container)

> Note: The included Dockerfile uses the `python:3.7` base image. You can update this if you want a newer Python version.

## Run locally

1. Create and activate a virtual environment (recommended):

```bash
python3 -m venv .venv
source .venv/bin/activate
```

2. Install dependencies:

```bash
pip install -r App/requirements.txt
```

3. Run the app:

```bash
python App/main.py
```

4. Open your browser and visit http://localhost:5000 — you should see "Hello from Python!".

## Build and run with Docker

From the repository root you can build and run the provided Docker image.

Build the image (from project root):

```bash
docker build -t python-hello -f Docker/Dockerfile .
```

Run the container:

```bash
docker run --rm -p 5000:5000 python-hello
```

Then visit http://localhost:5000 in your browser.

Tip: The Dockerfile copies the whole repository into `/app` and runs `pip install -r requirements.txt`. If you change the location of `main.py` or `requirements.txt`, update the Dockerfile accordingly.

## Project contract

- Input: HTTP GET request to `/`.
- Output: Plain text response `Hello from Python!` with HTTP 200.
- Errors: If Flask cannot start (port in use or missing dependency), the process will exit with an error message.

## Small improvements you can make

- Pin the Flask version in `App/requirements.txt` for reproducible builds (for example `Flask==2.2.5`).
- Add a simple health-check endpoint (e.g., `/health`) for container orchestrators.
- Add a `Makefile` or `docker-compose.yml` for easier development.

## License

This repository does not include a license file. Add a `LICENSE` if you want to permit reuse (for example, MIT or Apache-2.0).

## Author

Provided as a minimal example.
