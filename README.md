# 🤖 n8n Multi-Agent Enterprise Orchestrator (Manager-Worker Architecture)

[![n8n](https://img.shields.io/badge/Orchestrator-n8n-EA4B71?style=for-the-badge&logo=n8n&logoColor=white)](https://n8n.io/)
[![LangChain](https://img.shields.io/badge/AI_Engine-LangChain_Nodes-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white)](https://js.langchain.com/)
[![Architecture](https://img.shields.io/badge/Pattern-Manager--Worker-blue?style=for-the-badge)](#)

Sistema de orquestación distribuida de inteligencia artificial implementado sobre **n8n**, diseñado para erradicar el antipatrón del *"Workflow Mono-Bloque"* mediante el desacoplamiento de microservicios agénticos bajo el patrón de diseño **Manager-Worker**.

---

## 📌 Arquitectura del Sistema

El ecosistema opera como un *backbone* de comunicación digital donde un flujo orquestador central clasifica la intención en lenguaje natural, filtra el payload y delega la ejecución de forma síncrona hacia especialistas técnicos (*sub-workflows*).

```text
                       [Webhook Inbound Trigger]
                                   │
                                   ▼
                    [AI Intent Classifier & Triaje]
                                   │
                     Taxonomía Cerrada de Decisión
                     ├── DATA_ANALYSIS
                     ├── COMMUNICATION_DRAFT
                     └── FALLBACK
                                   │
                                   ▼
                            [Switch Router]
             ┌─────────────────────┼─────────────────────┐
             │                     │                     │
             ▼                     ▼                     ▼
     [Sanitize Set 1]      [Sanitize Set 2]      [Fallback Escalate]
             │                     │                     │
             ▼                     ▼                     ▼
      (Call Worker 1)       (Call Worker 2)     (Human Intervention)
      [Data Specialist]     [Copy Specialist]            │
             │                     │                     │
             └─────────────────────┼─────────────────────┘
                                   │
                                   ▼
                        [Consolidate Audit Log]
                         (Observabilidad y Traza)
                                   │
                                   ▼
                          [Respond to Webhook]
