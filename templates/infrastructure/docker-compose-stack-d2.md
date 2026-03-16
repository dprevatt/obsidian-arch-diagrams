---
tags: [architecture, diagram, d2, infrastructure, docker]
project: <ProjectName>
created: 2026-03-16
---

# Docker Compose Stack

> [!info] Context
> A Docker Compose service topology showing containers, networks, volumes, and port mappings. Use for documenting local development environments or production container deployments.

## Diagram

```d2
direction: down

docker_host: Docker Host {
  style: {
    fill: "#111827"
    stroke: "#4b5563"
    font-color: "#9ca3af"
    bold: true
  }

  # Frontend Network
  frontend_net: frontend network {
    style: {
      fill: "#1e3a5f"
      stroke: "#4a9eff"
      font-color: "#4a9eff"
      stroke-dash: 3
    }

    nginx: nginx {
      shape: rectangle
      style: {
        fill: "#1e3a5f"
        stroke: "#4a9eff"
        font-color: "#4a9eff"
      }
    }

    webapp: web app {
      shape: rectangle
      style: {
        fill: "#1e3a5f"
        stroke: "#4a9eff"
        font-color: "#4a9eff"
      }
    }
  }

  # Backend Network
  backend_net: backend network {
    style: {
      fill: "#1a3a2a"
      stroke: "#4aff91"
      font-color: "#4aff91"
      stroke-dash: 3
    }

    api: api server {
      shape: rectangle
      style: {
        fill: "#1a3a2a"
        stroke: "#4aff91"
        font-color: "#4aff91"
      }
    }

    worker: worker {
      shape: rectangle
      style: {
        fill: "#1a3a2a"
        stroke: "#4aff91"
        font-color: "#4aff91"
      }
    }
  }

  # Shared Services (on both networks)
  redis: Redis {
    shape: cylinder
    style: {
      fill: "#2e1e1a"
      stroke: "#ff7044"
      font-color: "#ff7044"
    }
  }

  postgres: PostgreSQL {
    shape: cylinder
    style: {
      fill: "#2e1e1a"
      stroke: "#ff7044"
      font-color: "#ff7044"
    }
  }

  # Volumes
  volumes: volumes {
    style: {
      fill: "#2a1a3a"
      stroke: "#cc4aff"
      font-color: "#cc4aff"
      stroke-dash: 3
    }

    db_data: db-data {
      shape: cylinder
      style: {
        fill: "#2a1a3a"
        stroke: "#cc4aff"
        font-color: "#cc4aff"
      }
    }

    redis_data: redis-data {
      shape: cylinder
      style: {
        fill: "#2a1a3a"
        stroke: "#cc4aff"
        font-color: "#cc4aff"
      }
    }

    app_logs: app-logs {
      shape: cylinder
      style: {
        fill: "#2a1a3a"
        stroke: "#cc4aff"
        font-color: "#cc4aff"
      }
    }
  }

  # Service connections
  frontend_net.nginx -> frontend_net.webapp: proxy
  frontend_net.webapp -> backend_net.api: HTTP :8080
  backend_net.api -> backend_net.worker: enqueue
  backend_net.api -> redis: :6379
  backend_net.worker -> redis: :6379
  backend_net.api -> postgres: :5432
  backend_net.worker -> postgres: :5432

  # Volume mounts
  volumes.db_data -> postgres: mount /var/lib/postgresql/data
  volumes.redis_data -> redis: mount /data
  volumes.app_logs -> backend_net.api: mount /app/logs
}

# External port exposure
internet: Internet {
  shape: cloud
  style: {
    fill: "#2e1a1a"
    stroke: "#ff4a4a"
    font-color: "#ff4a4a"
  }
}

internet -> docker_host.frontend_net.nginx: 80:80
```

## Notes

- Requires the `d2-obsidian` plugin
- Add/remove services, networks, and volumes as needed
- Label connections with port numbers matching your `docker-compose.yml`
- Customize service names to match your actual compose file
- Dashed borders (`stroke-dash: 3`) represent Docker network boundaries
- Cylinders inside the `volumes` group represent named Docker volumes
- For TLS termination, add a port `443:443` arrow alongside the `80:80` entry
- If using Docker Swarm or Kubernetes, adapt the outer container label accordingly
