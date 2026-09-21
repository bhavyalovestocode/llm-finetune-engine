# LLM Fine-Tune Engine

An open-source foundation for preparing datasets, fine-tuning language models, and serving inference APIs.

## Architecture

- `data/`: Training, validation, and evaluation datasets. Large or private artifacts should remain outside Git.
- `notebooks/`: Exploratory data analysis, experimentation, and evaluation notebooks.
- `src/engine/`: Core training, checkpoint, configuration, and inference orchestration logic.
- `src/api/`: FastAPI application and request/response models for model-serving endpoints.
- `models/`: Local model artifacts and checkpoints. Large binary files are ignored by Git.
- `tests/`: Unit and integration tests for the engine and API layers.

The intended flow is: datasets are prepared in `data/`, experiments are developed in `notebooks/`, reusable training and inference logic lives in `src/engine/`, and `src/api/` exposes that logic through a production HTTP service.

## Setup

```bash
python -m venv .venv
# Windows PowerShell
.venv\Scripts\Activate.ps1
# macOS/Linux
# source .venv/bin/activate

pip install -r requirements.txt
```

## Development

Run the test suite with:

```bash
pytest
```

Once the API application is added under `src/api/`, start it with Uvicorn using the module path defined by that application.
