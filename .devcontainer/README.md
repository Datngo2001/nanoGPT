# nanoGPT Development Container Setup

## Quick Start

1. **Install Requirements:**
   - VS Code
   - [Remote - Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
   - Docker Desktop

2. **Open Project in Container:**
   - Open the nanoGPT folder in VS Code
   - Click the Remote Window icon (bottom-left corner)
   - Select "Reopen in Container"
   - Wait for the container to build and initialize

3. **Verify Setup:**
   ```bash
   python --version
   pip list
   ```

## Features

- **Python 3.11** with all required ML/DL libraries
- **PyTorch** with CUDA support (or CPU-only if preferred)
- **Jupyter** for interactive notebooks
- **Git & GitHub CLI** pre-installed
- **Development Tools:** Black formatter, Pylint linter, Pytest
- **VS Code Extensions:**
  - Python language support
  - Pylance type checking
  - Jupyter notebooks
  - Ruff linter

## File Structure

```
.devcontainer/
├── devcontainer.json      # Main configuration
├── Dockerfile             # Container image definition
└── requirements.txt       # Python dependencies
```

## Customization

### To use CPU-only PyTorch:
Edit `.devcontainer/Dockerfile` and change the PyTorch installation:
```dockerfile
RUN pip install --no-cache-dir torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
```

### To add more Python packages:
Add them to `.devcontainer/requirements.txt` and rebuild the container.

### To expose ports:
Edit the `"forwardPorts"` array in `devcontainer.json` (e.g., `[8888]` for Jupyter).

## Common Commands

- **Rebuild container:** Click Remote Window icon → "Rebuild Container"
- **View logs:** View → Command Palette → "Remote Containers: Show Log"
- **Install additional package:** Open terminal in container and run `pip install <package>`

## Troubleshooting

- **Container won't start:** Check Docker Desktop is running
- **GPU not detected:** Verify Docker has GPU support and NVIDIA Container Toolkit is installed
- **Module import errors:** Run `pip install -r .devcontainer/requirements.txt` in the container terminal
