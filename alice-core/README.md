# Alice Core - Smart Home API Server

<p align="center">
  <img src="https://img.shields.io/badge/Bun-1.0+-black?style=for-the-badge&logo=bun">
  <img src="https://img.shields.io/badge/TypeScript-5.0+-3178C6?style=for-the-badge&logo=typescript">
  <img src="https://img.shields.io/badge/Hono-Web-blue?style=for-the-badge">
</p>

The central API server for Alice Smart Home. Built with Bun + Hono + SQLite.

## 🔗 Related Repos

- **Docs**: https://github.com/PinkyCodeMaster/alice
- **Voice AI**: https://github.com/PinkyCodeMaster/alice-ai
- **Firmware**: https://github.com/PinkyCodeMaster/alice-firmware
- **OS**: https://github.com/PinkyCodeMaster/alice-os-distro

## 🚀 Quick Start

```bash
# Install dependencies
bun install

# Run development server
bun run src/index.ts
```

Server runs at http://localhost:8080

## 📡 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/health` | Health check |
| GET | `/api/devices` | List all devices |
| POST | `/api/devices` | Add new device |
| GET | `/api/devices/:id` | Get device |
| PUT | `/api/devices/:id` | Update device |
| DELETE | `/api/devices/:id` | Remove device |
| GET | `/api/states` | Get all states |
| POST | `/api/devices/:id/state` | Update state |
| GET | `/api/automations` | List automations |
| POST | `/api/automations` | Create automation |

## 🏗️ Architecture

```
                    ┌─────────────────┐
                    │   Alice Core    │
                    │  (Bun + Hono)   │
                    └────────┬────────┘
                             │
           ┌─────────────────┼─────────────────┐
           │                 │                 │
           ▼                 ▼                 ▼
    ┌────────────┐    ┌────────────┐    ┌────────────┐
    │  Devices   │    │  Voice AI  │    │  Dashboard │
    │  (MQTT)    │    │  (Python)  │    │  (React)   │
    └────────────┘    └────────────┘    └────────────┘
```

## 🐳 Docker

```bash
# Pull and run
docker pull ghcr.io/pinkycodemaster/alice-core:latest
docker run -p 8080:8080 -v alice-data:/data ghcr.io/pinkycodemaster/alice-core:latest
```

Or use docker-compose:

```bash
cd alice-os-distro/docker
docker compose up -d
```

## 🛠️ Tech Stack

| Component | Technology |
|-----------|------------|
| Runtime | Bun |
| Framework | Hono |
| Database | SQLite (sql.js) |
| Validation | Zod |
| WebSocket | ws |
| MQTT | paho-mqtt |

## 📁 Project Structure

```
alice-core/
├── src/
│   ├── index.ts       # Entry point
│   ├── routes/        # API routes
│   ├── devices/       # Device management
│   ├── automations/  # Automation engine
│   └── mqtt/         # MQTT client
├── Dockerfile
└── package.json
```

## 🤝 Contributing

1. Fork the repo
2. Create a feature branch
3. Make your changes
4. Submit a PR

## 📄 License

MIT

---

**Built by Alice Systems** 🏠
