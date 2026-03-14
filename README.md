# Palworld Server

## ✅ Overview
This repo runs a **Palworld dedicated server** using Docker Compose.

## 🔌 Required port forwarding (router/NAT)
- **8211/UDP** – game server
- **27015/UDP** – Steam query / server list
- **8212/TCP** – REST API (do **not** expose publicly unless you know what you're doing)

## 🧩 Env files used by Docker Compose
- **`.env`** – main config (includes gameplay settings, rates, etc.).
  - Includes detailed comments describing settings.
- **`.env.secrets`** – private values (passwords, server name, etc.).
  - This file is **gitignored** and should never be committed.

## 📝 Setup
1. Update **`.env`** with your desired server settings.
   - This file contains documentation and defaults for the commonly used settings.

   - For full details on every setting, see the official docs:
       - Server settings: https://palworld-server-docker.loef.dev/getting-started/configuration/server-settings
       - Game settings: https://palworld-server-docker.loef.dev/getting-started/configuration/game-settings

2. Create the secret file and keep it private (it is gitignored):

```sh
touch .env.secrets
```

3. Edit `.env.secrets` and set your real values (passwords, server name, etc.).

Example:

```sh
# Server/connection secrets
SERVER_NAME=My Palworld Server
SERVER_DESCRIPTION=Only visible to players
SERVER_PASSWORD=changeme
ADMIN_PASSWORD=changeme

# Optional: override public/forwarded endpoints
PUBLIC_IP=
PUBLIC_PORT=
```

## 🔁 Start / Restart / Stop

- Start

```sh
docker compose up -d
```

- Restart:

```sh
docker compose restart palworld
```

- Stop:

```sh
docker compose down
```
