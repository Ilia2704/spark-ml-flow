# spark_ml_docker

Minimal local Spark environment using **Docker Compose**.

This project starts:
- Apache Spark **Standalone cluster** (1 master + 2 workers)
- JupyterLab connected to the Spark cluster
- Shared volumes for notebooks and workspace

No Dockerfile is used — everything runs directly from `docker-compose.yml`.


- `docker/` — infrastructure (Docker Compose, Python dependencies)
- `notebooks/` — Jupyter notebooks (mounted into the container)
- `workspace/` — shared workspace accessible by Spark master and workers

---

## Requirements

- Docker
- Docker Compose (v2+)

Tested on macOS (Apple Silicon / M2).

---

## How to run

From the **project root**:

```bash
docker compose -f docker/docker-compose.yml up -d
