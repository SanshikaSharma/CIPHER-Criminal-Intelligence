# CIPHER — Criminal Intelligence & Pattern Heuristic Engine

## Local Windows

Use only:

- `Start_Cipher.bat` — start the complete application
- `Stop_Cipher.bat` — stop the complete application

### Start

Double-click `Start_Cipher.bat` and wait for **CIPHER IS READY**. It opens `http://127.0.0.1:8000/` automatically.

Then:

**Login → GIS → OSIRIS 3D**

Do not open `127.0.0.1:3001` manually. OSIRIS runs privately behind CIPHER's `/osiris/` same-origin route.

### First start

The first start can take several minutes because Python dependencies and OSIRIS Node dependencies may need to be installed and the OSIRIS production build may need to be created.

### If OSIRIS does not start

`Start_Cipher.bat` now waits for OSIRIS `/api/health` before starting CIPHER. If it cannot start, the launcher prints the OSIRIS log and stops instead of leaving a misleading CIPHER-only startup with `/osiris` returning HTTP 503.

## Deployment

For Docker/Render, use the root `Dockerfile` and `render.yaml`. OSIRIS is built into the same container and remains private on loopback; only CIPHER's public HTTP port is exposed.
