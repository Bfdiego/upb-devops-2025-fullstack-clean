**🚀 Proyecto DevOps – Fullstack con CI/CD y Observabilidad**
=============================================================

**📘 Información General**
--------------------------

Este repositorio contiene la implementación completa de un **proyecto DevOps end-to-end**, donde se despliega una aplicación **Fullstack** en una instancia **EC2 de AWS**, utilizando **Docker, Docker Compose, GitHub Actions y un stack de observabilidad basado en Grafana**.

El proyecto fue desarrollado con el objetivo de **demostrar la aplicación práctica de los principios DevOps**, cubriendo automatización, despliegue continuo, monitoreo, logging y documentación.

**🎯 Objetivos del Proyecto**
-----------------------------

*   Contenerizar una aplicación Fullstack
    
*   Automatizar el build y deploy usando CI/CD
    
*   Desplegar en infraestructura real (AWS EC2)
    
*   *   Métricas
        
    *   Logs
        
*   Visualizar el estado del sistema en tiempo real
    
*   Detectar errores desde logs
    
*   Documentar todo el proceso
    

**🧱 Arquitectura del Sistema**
-------------------------------

### **🧩 Componentes Principales**

**Componente**

**Tecnología**

Frontend

Docker

Backend

API REST (Docker)

Base de Datos

PostgreSQL

Orquestación

Docker Compose

CI/CD

GitHub Actions

Infraestructura

AWS EC2

Métricas

Prometheus + cAdvisor

Logs

Loki + Promtail

Visualización

Grafana

Alertas

Discord Webhook

### **🔁 Flujo General**

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   Usuario    ↓  Frontend (Docker)    ↓  Backend (Docker)    ↓  PostgreSQL   `

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   Contenedores    ├─ Métricas → Prometheus → Grafana    └─ Logs → Promtail → Loki → Grafana   `

**🐳 Dockerización**
--------------------

Toda la aplicación está completamente dockerizada.

### **Servicios incluidos en Docker Compose**

*   frontend
    
*   backend
    
*   db (PostgreSQL)
    
*   prometheus
    
*   cadvisor
    
*   loki
    
*   promtail
    
*   grafana
    

### **Persistencia**

Se utilizan volúmenes Docker para:

*   PostgreSQL → datos persistentes
    
*   Grafana → dashboards y configuraciones
    

Esto garantiza que la información no se pierda al reiniciar los contenedores.

**📂 Estructura del Repositorio**
---------------------------------

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   .  ├── backend/  ├── frontend/  ├── docker-compose.yml  ├── observability/  │   ├── grafana/  │   │   ├── dashboards/  │   │   │   ├── docker_host.json  │   │   │   ├── backend_health.json  │   │   │   └── loki_logs_overview.json  │   │   └── provisioning/  │   │       ├── dashboards/  │   │       │   └── dashboards.yml  │   │       └── datasources/  │   │           └── datasources.yml  │   ├── prometheus/  │   │   └── prometheus.yml  │   ├── loki/  │   │   └── loki-config.yml  │   └── promtail/  │       └── promtail-config.yml  ├── .github/  │   └── workflows/  │       └── deploy.yml  └── README.md   `

**🔭 Observabilidad**
---------------------

### **📊 Métricas – Prometheus & cAdvisor**

Prometheus recolecta métricas cada **15 segundos** desde los contenedores.

#### **Métricas utilizadas**

Estado del backend:

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   up{job="backend"}   `

Contenedores activos:

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   count(container_last_seen)   `

Uso de CPU:

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   rate(container_cpu_usage_seconds_total[1m])   `

Uso de memoria:

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   container_memory_usage_bytes   `

Estas métricas se visualizan en dashboards automáticos en Grafana.

### **📜 Logs – Loki & Promtail**

Promtail recolecta logs directamente desde Docker:

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   /var/lib/docker/containers/*/*.log   `

Loki centraliza los logs y Grafana permite consultas **LogQL**.

#### **Consulta funcional principal**

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   sum by (container) (    count_over_time({job="docker"}[1m])  )   `

Esto permite ver la cantidad de logs generados por contenedor en tiempo real.

**🧪 Simulación de Errores**
----------------------------

Para demostrar observabilidad real, se agregó un **error simulado en el backend**.

Log generado:

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   ERROR_SIMULADO_BACKEND   `

Consulta LogQL para detección:

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   {job="docker"} |= "ERROR_SIMULADO_BACKEND"   `

Esto permite:

*   Identificar errores desde Grafana
    
*   Validar el pipeline de logs
    
*   Simular debugging en producción
    

**📈 Dashboards de Grafana**
----------------------------

Grafana utiliza **provisioning**, por lo que los dashboards se cargan automáticamente al iniciar el contenedor.

### **Dashboards incluidos**

1.  *   CPU
        
    *   Memoria
        
    *   Red
        
    *   Contenedores activos
        
2.  *   Estado del backend
        
    *   CPU
        
    *   Memoria
        
3.  *   Logs por contenedor
        
    *   Volumen de logs
        
    *   Errores simulados
        

Todos los dashboards están definidos en archivos .json.

**🔁 CI/CD – GitHub Actions**
-----------------------------

El proyecto cuenta con un pipeline automático que se ejecuta en cada push.

### **Pasos del pipeline**

1.  Build de imágenes Docker
    
2.  Push a Docker Hub
    
3.  Conexión SSH a EC2
    
4.  Pull de nuevas imágenes
    
5.  Deploy con Docker Compose
    
6.  Notificación a Discord
    

📄 Workflow:

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   .github/workflows/deploy.yml   `

**🔔 Notificaciones a Discord**
-------------------------------

Cada deploy exitoso envía una notificación automática a Discord con información del despliegue.

Esto permite:

*   Confirmar despliegues
    
*   Auditoría de cambios
    
*   Feedback inmediato
    

**🔐 Gestión de Secretos**
--------------------------

Todos los secretos se manejan mediante **GitHub Secrets**:

*   EC2\_HOST
    
*   EC2\_USER
    
*   EC2\_SSH\_KEY
    
*   DOCKERHUB\_USERNAME
    
*   DOCKERHUB\_TOKEN
    
*   DISCORD\_WEBHOOK\_URL
    

No se exponen credenciales en el repositorio.

**☁️ Infraestructura AWS**
--------------------------

*   Instancia EC2 activa
    
*   Servicios desplegados vía Docker
    
*   *   80 → Frontend
        
    *   8000 → Backend
        
    *   3000 → Grafana
        
    *   9090 → Prometheus
        

**✅ Cumplimiento de Rúbricas**
------------------------------

**Requisito**

**Cumple**

Dockerización

✅

CI/CD

✅

AWS

✅

Observabilidad

✅

Métricas

✅

Logs

✅

Alertas

✅

Documentación

✅

**🏁 Conclusión**
-----------------

Este proyecto demuestra una **implementación DevOps completa y funcional**, integrando automatización, despliegue continuo y observabilidad real sobre infraestructura en la nube.

El sistema es:

*   Reproducible
    
*   Escalable
    
*   Monitorizable
    
*   Listo para producción
