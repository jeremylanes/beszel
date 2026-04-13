# Beszel Monitoring Stack

This stack deploys **Beszel** (a lightweight monitoring hub) and its **Agent**, both running via **Docker Compose** and managed behind a **Traefik** reverse proxy.

## 🛠 Prerequisites

Before running this stack, make sure you have:

- **Docker Compose** installed on your machine.
- The **Traefik** proxy deployed and actively running on the `traefik_proxy` network. 
  Required repository link: [https://github.com/jeremylanes/traefik](https://github.com/jeremylanes/traefik)

## ⚙️ Configuration

Define the domain name via an environment variable. 
Simply create an `.env` file at the root of this folder and add the following variable:

```env
DOMAIN_NAME=beszel.local
```

## 🚀 Quick Start

Managing your containers is simplified using the wrapper scripts provided in the `bin/` directory.

- **To start everything** (Main server + System agents):
  ```bash
  bin/up
  ```

- **To view the main logs** (continuous log stream):
  ```bash
  bin/logs
  ```
  *(You can also watch a specific container, e.g.: `bin/logs beszel`)*

- **To stop everything cleanly**:
  ```bash
  bin/down
  ```

## 🏗 Directory Structure
- `docker-compose.yml`: Launches the main Beszel web service protected by Traefik.
- `systems/docker-compose.yml`: Contains the monitoring Agent that collects technical system data.
- `bin/`: Automated management scripts (`up`, `down`, `logs`).
