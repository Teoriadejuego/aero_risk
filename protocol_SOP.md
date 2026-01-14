# Protocolo de Operaciones Estándar (SOP) - Proyecto AERO-RISK

**Versión:** 1.0.0
**Fecha de Vigencia:** Enero 2026
**Investigadores Principales:** Antonio Alfonso & Pablo Brañas
**Prerregistro:** [Enlace a AsPredicted](https://aspredicted.org/nq554j.pdf)

---

## 1. Introducción y Objetivo
Este documento define el procedimiento estandarizado para la recolección de datos del proyecto AERO-RISK. El objetivo es medir la aversión al riesgo en función de la incertidumbre sobre la habilidad propia.
* **Diseño:** Entre-sujetos (Between-subjects).
* **Variable Independiente:** Práctica previa (0 lanzamientos vs. 3 lanzamientos).
* **Variable Dependiente:** Distancia apostada (riesgo asumido).

---

## 2. Infraestructura y Materiales

### 2.1. Material Físico
* **Avión:** Papel DIN A4 estándar (80g). *Nota: Se debe usar el mismo modelo de plegado para todos los participantes (Modelo "Dardo" estándar).*
* **Medición:** Cinta métrica de al menos 10 metros, fijada al suelo.
* **Espacio:** Pasillo o sala despejada de al menos 15 metros de largo, sin corrientes de aire.
* **Incentivos:** Monedas de 1€ y 2€ para pago inmediato en efectivo (o sistema de vales equivalentes).

### 2.2. Ecosistema Digital (Trazabilidad)
* **Dispositivo de Captura:** Tablet con conexión a internet estable.
* **Software:** LimeSurvey (versión web).
* **Protección de Datos:** No se utilizará papel y lápiz para evitar errores de transcripción y asegurar la digitalización nativa.

---

## 3. Configuración del Espacio
1.  **Línea de Base:** Marcar una línea de lanzamiento clara en el suelo con cinta adhesiva de color visible.
2.  **Eje de Medición:** Desplegar la cinta métrica perpendicularmente a la línea de lanzamiento, fijando los extremos para evitar movimientos.
3.  **Zona de Espera:** Habilitar una silla para el participante fuera del campo visual directo de la cinta métrica hasta el momento del lanzamiento.

---

## 4. Procedimiento Paso a Paso

### FASE A: Recepción y Consentimiento (Ética Operacionalizada)
1.  **Bienvenida:** Recibir al participante (ID generado secuencialmente, ej. P001).
2.  **Consentimiento Informado:** Entregar la tablet. El participante lee y firma digitalmente el consentimiento en la primera pantalla de LimeSurvey.
    * *Check de seguridad:* Si no acepta, la encuesta termina automáticamente.
3.  **Instrucciones Generales:** Explicar verbalmente: *"Tendrás que lanzar un avión de papel. Ganarás 1€ por cada metro que el avión recorra, pero tú eliges la distancia meta. Si fallas, ganas 0€."*

### FASE B: Asignación Aleatoria (Algorítmica)
**IMPORTANTE:** El investigador NO decide el grupo. La tablet realiza la asignación ciega.
1.  El sistema ejecuta el script interno: `if(rand(1, 2) == 1, "Control", "Tratamiento")`.
2.  La pantalla de la tablet indicará al investigador la instrucción a seguir (oculta al participante hasta este momento).

### FASE C: Manipulación Experimental (Según Grupo)

#### 👉 Si la Tablet indica: GRUPO CONTROL
* **Acción:** El participante **NO** toca el avión todavía.
* **Instrucción:** Pasa directamente a la Fase D (Decisión).

#### 👉 Si la Tablet indica: GRUPO TRATAMIENTO
* **Acción:** Se permite al participante realizar **3 lanzamientos de práctica**.
* **Objetivo:** Reducir la incertidumbre sobre su propia habilidad motora.
* **Registro:** Estos lanzamientos NO se pagan y NO se miden oficialmente.
* **Instrucción:** *"Puedes lanzar el avión 3 veces para probar tu puntería. Luego haremos el lanzamiento real."*

### FASE D: La Decisión (Variable Dependiente)
1.  **Pregunta Crítica:** En la tablet, se le pide al participante: *"¿A qué distancia (en metros completos) apuestas que llegará tu avión?"*.
2.  **Registro:** El participante selecciona el valor (0 a 10 metros) en la interfaz digital.
    * *Nota:* Esta decisión es irrevocable una vez pulsado "Siguiente".

### FASE E: Ejecución y Pago
1.  **Lanzamiento Crítico:** El participante se coloca tras la línea y lanza el avión una única vez.
2.  **Medición:** El investigador observa el punto de primer impacto (no donde se detiene tras deslizarse).
3.  **Registro de Resultado:** El investigador introduce la distancia real (en cm) en la tablet.
4.  **Cálculo Automático:** LimeSurvey calcula el pago:
    * Si *Distancia Real* >= *Distancia Apostada* → **Paga: Distancia Apostada × 1€**.
    * Si *Distancia Real* < *Distancia Apostada* → **Paga: 0€**.
5.  **Cierre:** Se entrega el incentivo (si corresponde) y se agradece la participación.

---

## 5. Gestión de Datos y Seguridad

### 5.1. Almacenamiento
* Los datos se sincronizan en tiempo real con el servidor de LimeSurvey.
* **Formato de salida:** Los datos crudos se exportarán exclusivamente en `.csv` (formato abierto) siguiendo el Plan de Gestión de Datos (DMP).

### 5.2. Anonimización
* No se recogen nombres ni IPs en la base de datos principal.
* Los participantes se identifican únicamente por su código `id_participante` (P001... P128).

### 5.3. Control de Calidad
* Revisar al final de cada sesión (bloque de 10 participantes) que los datos se han subido correctamente a la nube.
* Si falla la conexión, los datos quedan en caché local de la tablet: **NO BORRAR NAVEGADOR**.

---

## 6. Registro de Desviaciones (Bitácora)
Cualquier evento no contemplado en este protocolo (ej. el avión choca con una persona, fallo de internet, el participante no entiende la instrucción) debe registrarse en el campo de texto abierto "Observaciones" al final de la encuesta en LimeSurvey, indicando el ID del participante afectado.

> *Este documento forma parte de la infraestructura de reproducibilidad del proyecto AERO-RISK.*
