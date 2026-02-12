# 🐝 Agritech BeeSense - QA Project

## Termohygrometer Device - MiniBrain V0.1

[![Status](https://img.shields.io/badge/Status-Not%20Started-red)]()
[![Version](https://img.shields.io/badge/Version-0.1.0-blue)]()
[![Board](https://img.shields.io/badge/Board-MiniBrain%20V0.1-green)]()

---

##  Descripción del Proyecto

Este repositorio contiene el proceso de **Quality Assurance (QA)** completo para el dispositivo **BeeSense Termohygrometer**, un sensor inteligente de temperatura y humedad diseñado para aplicaciones agrícolas con las siguientes características:

-  Medición precisa de temperatura y humedad
-  Batería recargable con autonomía de 100 días
-  Conectividad WiFi y BLE
-  Almacenamiento de datos en AWS
-  Actualizaciones OTA (Over-The-Air)
-  Sistema de alertas configurable
-  Frecuencia de muestreo personalizable

---

##  Estructura del Proyecto

```
QA_Agritech_BeeSense/
│
├── QA.md                          # Documento principal de proceso de QA
├── README.md                      # Este archivo
│
└── docs/
    ├── BeeSense_user_manual.pdf   # Manual de usuario del dispositivo
    └── [Otros documentos técnicos]
```

---

##  Documentación Principal

### [QA.md](QA.md)
Documento completo del proceso de Quality Assurance que incluye:

- **Información General**: Datos del proyecto, equipo y fechas
- **Matriz de Trazabilidad de Requisitos (RTM)**: 10 requisitos funcionales priorizados
- **Criterios de Aceptación**: Umbrales de calidad para aprobación
- **Categorías de Pruebas**:
  -  Pruebas Funcionales
  -  Pruebas de Rendimiento
  -  Pruebas de Red
  -  Pruebas de Usabilidad
  -  Validación de Sensores y Datos
  -  Pruebas de Seguridad
- **Evaluación de Riesgos**
- **KPIs de QA**

### [Manual de Usuario](docs/BeeSense_user_manual.pdf)
Manual completo con instrucciones de uso, configuración y troubleshooting del dispositivo BeeSense.

---

##  Objetivos de QA

Garantizar que el dispositivo Termohidrómetro cumple con:
-  Especificaciones del datasheet del producto
-  Manual de usuario
-  Funcionalidades requeridas por el usuario
-  Operación correcta y confiable
-  Integridad de datos
-  Gestión remota
-  Fiabilidad a largo plazo

---

## 📊 Criterios de Aprobación

El dispositivo será aprobado si cumple:

1.  100% de requisitos de prioridad **High** y **Critical** aprobados
2.  Mínimo 95% de casos de prueba totales aprobados
3.  Cero bugs de severidad **Critical** o **High** sin resolver
4.  Prueba de estabilidad de 72 horas sin crashes
5.  Prueba de resistencia de 7 días sin memory leaks
6.  Precisión de sensores dentro de tolerancias definidas
7.  Cero pérdida de datos en transiciones offline/online
8.  Almacenamiento seguro de credenciales verificado

---

##  Alcance de Pruebas

###  Dentro del Alcance
- Validación de comportamiento del firmware
- Validación funcional del hardware
- Validación de precisión de sensores
- Flujos de comunicación (BLE, WiFi, AWS)
- Almacenamiento y retransmisión de datos
- Comportamiento de OTA
- Validación del sistema de alarmas
- Validación de seguridad

###  Fuera del Alcance
- Pruebas de UI de aplicación móvil
- Pruebas de rendimiento del backend en la nube
- Defectos de manufactura del hardware

---

##  Requisitos Principales (RTM)

| ID | Descripción | Prioridad | Estado |
|----|-------------|-----------|--------|
| FR-01 | Wake-up correcto por timer | High | Pending |
| FR-02 | Pulsación corta de reed trigger ciclo normal | High | Pending |
| FR-03 | Pulsación larga de reed activa modo BLE | High | Pending |
| FR-04 | Precisión temperatura ±0.5°C | High | Pending |
| FR-05 | Precisión humedad ±3% RH | High | Pending |
| FR-06 | Reconexión automática a WiFi | High | Pending |
| FR-07 | Datos offline almacenados y retransmitidos | High | Pending |
| FR-08 | OTA solo con batería segura | High | Pending |
| FR-09 | Indicadores LED reflejan estado del sistema | Medium | Pending |
| FR-10 | Almacenamiento seguro de credenciales en NVS | Critical | Pending |

---

##  Equipo

| Rol | Nombre | Email |
|-----|--------|-------|
| **Firmware Lead** | Isabella García Saenz | isa@sense-ai.co |
| **Hardware Lead** | Ana María Montañez | ana@sense-ai.co |
| **QA Lead 1** | Daniel Escobar Saltarén | daniel@sense-ai.co |
| **QA Lead 2** | Mateo Robayo | mateo@sense-ai.co |
| **QA Lead 3** | Cristian Acevedo | cristian@sense-ai.co |

---

##  Timeline

- **Fecha de Inicio**: 16/02/2026
- **Fecha de Finalización**: TBD
- **Estado Actual**: Not Started

---

##  Especificaciones Técnicas

### Hardware
- **Board**: MiniBrain V0.1
- **Sensores**: Temperatura y Humedad de alta precisión
- **Batería**: Recargable
- **Tiempo de carga**: ~2 horas
- **Autonomía**: ~100 días

### Conectividad
- **WiFi**: Transmisión de datos a AWS
- **BLE**: Configuración de dispositivo
- **OTA**: Actualizaciones remotas de firmware

### Precisión de Sensores
- **Temperatura**: ±0.5°C
- **Humedad**: ±3% RH

---

##  KPIs de QA

| KPI | Objetivo |
|-----|----------|
| Cobertura de Requisitos | 100% |
| Tasa de Ejecución de Casos de Prueba | ≥ 95% |
| Fuga de Bugs Críticos | 0 |
| Bugs de Alta Severidad Abiertos | 0 antes del release |
| Tasa de Éxito de Reconexión | ≥ 98% |
| Tasa de Éxito de OTA | ≥ 99% |
| Estabilidad (72h) | 0 crashes |
| Tasa de Pérdida de Datos | 0% |

---

##  Próximos Pasos

1. Revisar y aprobar el documento de proceso de QA
2. Definir casos de prueba detallados para cada requisito
3. Configurar entorno de pruebas
4. Iniciar ejecución de pruebas funcionales
5. Realizar pruebas de rendimiento y estabilidad
6. Documentar resultados y bugs encontrados
7. Validación final y aprobación

---

##  Control de Versiones

| Versión | Fecha | Autor | Descripción |
|---------|-------|-------|-------------|
| 0.1.0 | 16/02/2026 | QA Team | Definición inicial del proceso de QA |

---

##  Contacto

Para más información sobre este proyecto, contactar al equipo de QA o al Firmware Lead.

**Cliente**: The World  
**Repository**: Agritech_BeeSense - Alpha  
**Branch**: dev

---

<div align="center">
<b>🐝 Sense AI © 2026</b>
</div>
