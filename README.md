# 🚀 Proyecto DevOps – Fullstack con CI/CD y Observabilidad

## 📘 Información general

Este repositorio contiene la implementación completa de un proyecto DevOps end-to-end, donde se despliega una aplicación fullstack en una instancia EC2 de AWS, utilizando Docker, Docker Compose, GitHub Actions y un stack de observabilidad basado en Grafana.

El proyecto fue desarrollado con el objetivo de demostrar la aplicación práctica de los principios DevOps, cubriendo automatización, despliegue continuo, monitoreo, logging y documentación.

## 🎯 Objetivos del proyecto

- Contenerizar una aplicación fullstack.
- Automatizar el build y deploy usando CI/CD.
- Desplegar en infraestructura real (AWS EC2).
- Visualizar el estado del sistema en tiempo real.
- Detectar errores desde logs.
- Documentar todo el proceso.

## 🧱 Arquitectura del sistema

### 🧩 Componentes principales

| Componente        | Tecnología                 |
|------------------|----------------------------|
| Frontend         | Docker                      |
| Backend          | API REST (Docker)           |
| Base de Datos    | PostgreSQL                  |
| Orquestación     | Docker Compose              |
| CI/CD            | GitHub Actions              |
| Infraestructura  | AWS EC2                     |
| Métricas         | Prometheus + cAdvisor       |
| Logs             | Loki + Promtail             |
| Visualización    | Grafana                     |
| Alertas          | Discord Webhook             |

### 🔁 Flujo general

```text
Usuario
  ↓
Frontend (Docker)
  ↓
Backend (Docker)
  ↓
PostgreSQL
```

```text
Contenedores
  ├─ Métricas → Prometheus → Grafana
  └─ Logs → Promtail → Loki → Grafana
```

## 🐳 Dockerización

Toda la aplicación está completamente dockerizada.

### Servicios incluidos en Docker Compose

- frontend
- backend
- db (PostgreSQL)
- prometheus
- cadvisor
- loki
- promtail
- grafana

### Persistencia

Se utilizan volúmenes Docker para:

- PostgreSQL → datos persistentes.
- Grafana → dashboards y configuraciones.

Esto garantiza que la información no se pierda al reiniciar los contenedores.

## 📂 Estructura del repositorio

```text
.
├── backend/
├── frontend/
├── docker-compose.yml
├── observability/
│   ├── grafana/
│   │   ├── dashboards/
│   │   │   ├── docker_host.json
│   │   │   ├── backend_health.json
│   │   │   └── loki_logs_overview.json
│   │   └── provisioning/
│   │       ├── dashboards/
│   │       │   └── dashboards.yml
│   │       └── datasources/
│   │           └── datasources.yml
│   ├── prometheus/
│   │   └── prometheus.yml
│   ├── loki/
│   │   └── loki-config.yml
│   └── promtail/
│       └── promtail-config.yml
├── .github/
│   └── workflows/
│       └── deploy.yml
└── README.md
```
