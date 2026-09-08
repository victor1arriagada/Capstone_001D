# 🚇 Proyecto Línea 9 — Infraestructura de Telecomunicaciones Subterránea

## 📡 Descripción

Proyecto desarrollado para el **Proyecto Capstone (PTY4624)** de la carrera de **Ingeniería en Conectividad y Redes** de Duoc UC, enfocado en el diseño de una infraestructura de telecomunicaciones para la futura **Línea 9 del Metro de Santiago**.

La propuesta busca proporcionar **conectividad móvil continua 4G/5G** en los 27 km de trazado subterráneo, utilizando una arquitectura basada en:

* 📶 Cable Radiante (*Leaky Feeder*)
* 📡 Sistema de Antenas Distribuidas (DAS Activo)
* 🔌 Backbone de Fibra Óptica OS2
* 🌐 Transporte de datos de 10G/40G
* 🔐 Segmentación de redes IT/OT
* 🛡️ Controles de seguridad basados en IEC 62443

El diseño considera la continuidad de las comunicaciones durante el desplazamiento de los trenes a velocidades de hasta **80 km/h**, además del aislamiento de las redes públicas respecto de los sistemas críticos ferroviarios.

---

## 📍 Contexto y problemática

La Línea 9 contempla aproximadamente:

| Característica       |                      Valor |
| -------------------- | -------------------------: |
| Longitud             |                  **27 km** |
| Estaciones           |                     **14** |
| Entorno              | Principalmente subterráneo |
| Profundidad          |     >25 metros en sectores |
| Tecnología propuesta |       4G/5G + Fibra Óptica |

Uno de los principales desafíos corresponde a la pérdida de señal producida por la profundidad y las estructuras de hormigón presentes en los túneles.

Estas condiciones pueden generar un efecto similar a una **jaula de Faraday**, provocando niveles de atenuación estimados entre **90 y 110 dB** y, como consecuencia, pérdida de conectividad móvil.

### Impacto

La falta de conectividad podría afectar actividades como:

* 🎫 Validación de pasajes digitales y códigos QR.
* 🏦 Acceso a aplicaciones bancarias.
* 📞 Llamadas y mensajería.
* 🚨 Comunicaciones durante situaciones de emergencia.
* 🌐 Uso de datos móviles durante el trayecto.

El proyecto considera que potencialmente más de **1 millón de usuarios diarios** podrían verse afectados por esta problemática.

---

# 🎯 Objetivo general

Diseñar una arquitectura integral de telecomunicaciones subterránea para los **27 km de la Línea 9**, combinando tecnologías **5G y fibra óptica**, con el propósito de proporcionar conectividad continua durante el desplazamiento de los trenes y mantener aisladas las redes operativas críticas.

---

# 📌 Objetivos específicos

### 📶 Cobertura 4G/5G

Dimensionar una solución de **Cable Radiante** que permita entregar cobertura RF multioperador y mantener un *handover* continuo dentro de los túneles.

### 📡 DAS Activo

Diseñar un **Sistema de Antenas Distribuidas (DAS Activo)** para proporcionar conectividad inalámbrica en las estaciones.

### 🔌 Backbone de Fibra Óptica

Diseñar un backbone utilizando **fibra óptica OS2**, con velocidades de **10/40G** y una arquitectura de doble anillo redundante que conecte las 14 estaciones.

### 🔐 Ciberseguridad

Implementar mecanismos de segmentación **IT/OT**, protegiendo los sistemas asociados a:

* Tracción.
* Señalización.
* Control de trenes.
* Sistemas críticos ferroviarios.

---

# 🏗️ Arquitectura propuesta

La solución se divide en tres componentes principales:

```text
                    ┌───────────────────────┐
                    │      OPERADORES       │
                    │       4G / 5G        │
                    └───────────┬───────────┘
                                │
                         ┌──────▼──────┐
                         │  DAS ACTIVO │
                         └──────┬──────┘
                                │
                     ┌──────────▼──────────┐
                     │    CABLE RADIANTE   │
                     │    LEAKY FEEDER     │
                     └──────────┬──────────┘
                                │
                     ┌──────────▼──────────┐
                     │  TÚNELES LÍNEA 9    │
                     │      27 KM          │
                     └──────────┬──────────┘
                                │
                      ┌─────────▼─────────┐
                      │ FIBRA ÓPTICA OS2  │
                      │     10G / 40G     │
                      └─────────┬─────────┘
                                │
                    ┌───────────▼───────────┐
                    │   BACKBONE EN ANILLO  │
                    │       REDUNDANTE      │
                    └───────────┬───────────┘
                                │
              ┌─────────────────┴─────────────────┐
              │                                   │
        ┌─────▼─────┐                       ┌─────▼─────┐
        │    IT     │                       │    OT     │
        │ Red Pública│                       │ Red Crítica│
        └───────────┘                       └───────────┘
```

La arquitectura contempla radiofrecuencia confinada en túneles y transporte óptico mediante una red de alta capacidad, buscando resolver la continuidad de señal y el *handover* sin interferir con los sistemas de señalización y control ferroviario.

---

# ⚠️ Riesgos principales

| Riesgo                                                     | Nivel      | Mitigación                                                                       |
| ---------------------------------------------------------- | ---------- | -------------------------------------------------------------------------------- |
| Pérdida de potencia RF por curvaturas y longitud del túnel | 🔴 Alto    | *Link Budget*, cable radiante de bajas pérdidas y amplificadores bidireccionales |
| Interferencia con sistemas críticos del Metro              | 🔴 Crítico | Separación física de fibra, VRF/VLAN y aislamiento OT                            |

---

# 🧪 Metodología

El proyecto se divide en distintas áreas de trabajo:

### 🌐 Redes IP

* Backbone de fibra OS2.
* Switches.
* Arquitectura en anillo.
* QoS.

### 📡 RF Subterránea

* Cobertura 4G/5G.
* Análisis de atenuación.
* Presupuesto RF.
* Cable Radiante.
* DAS.


# 🔧 Etapas del proyecto

## 1. Diagnóstico

Análisis del trazado, profundidad, niveles de atenuación y demanda estimada de tráfico.

## 2. Ingeniería RF

Cálculo de ganancias y pérdidas, diseño del DAS y dimensionamiento del Cable Radiante.

## 3. Arquitectura de red

Diseño de:

* Fibra OS2.
* Presupuesto óptico.
* Red IP.
* QoS.
* Redundancia.

## 4. Seguridad e integración

Implementación del aislamiento IT/OT y mecanismos de redundancia de red.

---

# 📁 Evidencias del proyecto

Las principales evidencias comprometidas son:

* 📄 **Informe Técnico de Arquitectura**

  * Especificaciones de fibra.
  * DAS.
  * Cable Radiante.

* 🗺️ **Topología y Diagrama de Red**

  * Topología física.
  * Topología lógica.
  * Backbone en anillo.
  * Distribución en estaciones.

* 📊 **Memoria de Cálculo de Enlaces**

  * *Optical Loss Budget*.
  * Balance de enlace RF.
  * Cálculos expresados en dB.

* 🔐 **Matriz de Segmentación OT/IT**

  * VLANs.
  * VRFs.
  * Reglas de aislamiento.
  * Criterios asociados a IEC 62443.

---

# 👥 Equipo

**Proyecto Capstone — PTY4624**

* **Victor Arriagada**
* **Martin Devia**
* **Sebastian Jara**
* **Emilio Yañez**

**Carrera:** Ingeniería en Conectividad y Redes
**Institución:** Duoc UC — Sede San Joaquín
**Docente:** Claudia Gabriela Reinoso Hurtado

---
