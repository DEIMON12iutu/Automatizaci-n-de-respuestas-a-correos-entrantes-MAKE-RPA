# Automatizacion-de-respuestas-a-correos-entrantes-MAKE-RPA
Este proyecto presenta una solución de automatización de procesos robóticos (RPA) utilizando como plataforma MAKE.com.

# Automatización de Respuestas a Correos con Make.com (RPA)
![Make.com Logo](https://www.make.com/images/logo.svg)

Este proyecto implementa un flujo de automatización (RPA) en **Make.com** para:
- **Clasificar** correos entrantes mediante **filtros nativos** (palabra clave "urgente","facturacion,"ayuda")
- **Responder automáticamente** usando plantillas predefinidas
- **Registrar datos** en Google Sheets
- **Gestionar prioridades** con etiquetas de Gmail
![image](https://github.com/user-attachments/assets/57d8d844-1d16-487e-9173-a1a7572f6d9f)

# Descripción

##  Flujo de Automatización en Make.com
Este proyecto implementa un sistema RPA para gestión de correos empresariales mediante **Make.com**, utilizando filtros programables y conexiones nativas con Gmail y Google Sheets. El flujo:

1. **Monitoreo en tiempo real**:  
   - Escucha correos entrantes vía **IMAP** (Gmail empresarial) con intervalos configurables (ej: cada 15 minutos).

2. **Clasificación Automática**:  
   - Filtra correos mediante **condiciones nativas** en nodos Router:  
     ```plaintext
     • Palabra clave "urgente" (asunto/cuerpo, case-insensitive)  
     • Reglas personalizables (AND/OR) para otras categorías  
     ```

3. **Gestión de Respuestas**:  
   - Envía respuestas automáticas mediante **plantillas SMTP** predefinidas.  
   - Opción de respuestas multidioma (configurable en nodos "Set variable").

4. **Registro y Trazabilidad**:  
   - Almacena en **Google Sheets**:  
     ```plaintext
     • Remitente • Asunto • Categoría ("urgente"/"facturacion")  
     • Fecha/hora • Estado de respuesta
     ```

![Vídeo-sin-título-‐-Hecho-con-Clipchamp](https://github.com/user-attachments/assets/75de1878-6861-484f-bba4-c2302cf18041)


##  Beneficios Clave
| Característica | Ventaja |
|----------------|---------------|
| **Filtros nativos** | Sin dependencia de APIs de IA (bajo costo) |
| **Plantillas personalizables** | Respuestas consistentes según categoría |
| **Integración directa** | Conexión nativa con Google Workspace |
| **Escalable** | Añade más reglas sin modificar la estructura |

![image](https://github.com/user-attachments/assets/c4923b99-5bbe-4f74-97fc-03982efae12e)
![image](https://github.com/user-attachments/assets/4846370b-e4c3-42cd-87c5-16ccbc645290)
![image](https://github.com/user-attachments/assets/5e232308-e012-48ce-be85-6e3d26857890) 

+ Configuración típica en Make.com:
- Trigger: Gmail > Watch Emails
- Router: 2 condiciones OR (asunto/cuerpo contiene "urgente")
- Acciones: Etiquetar en Gmail + Registrar en Sheets.


## ⚙️ Requisitos Técnicos

### 1. **Cuentas Obligatorias**
- **Make.com**  
  - Cuenta gratuita o de pago (según volumen de operaciones necesarias).  
  - *Nota: El plan gratis tiene límite de 1,000 operaciones/mes*.

- **Google Workspace**  
  - Credenciales para:  
    - **Gmail API** (o acceso IMAP habilitado).  
    - **Google Sheets API** (con permisos de edición).  

### 2. **Configuraciones Previas**  
#### En Google Cloud:  
1. Activar APIs:  
   - Gmail API  
   - Google Sheets API
   
2. Descargar archivo JSON de credenciales.

#### En Make.com:  
1. Añadir conexiones:  
   - Gmail (usando el JSON descargado).  
   - Google Sheets (mismo método).  

### 3. **Recursos Adicionales**  
- **Plantilla de Google Sheets**:  
  - Columnas mínimas requeridas:  
    ```plaintext
    Fecha | Remitente | Asunto | Categoría | Respondido  
    ```

# Configuración del Flujo en Make.com

## 📥 Importar el Flujo
1. **Exporta tu flujo actual**:
   - En Make.com, ve a tu escenario > Haz clic en el menú de tres puntos (⋮) > Selecciona **"Export"**.
   - Guarda el archivo `GmailAutomation.json` en tu computadora.

2. **Importar en otro entorno**:
   ```plaintext
   • Crea un nuevo escenario en Make.com
   • Haz clic en "Import" > Sube el archivo JSON
   • Revisa que todos los módulos estén conectados

# Flujo de Automatización de Correos con Make.com

## 📨 Proceso de Automatización

Este proyecto implementa un sistema RPA en **Make.com** que gestiona automáticamente los correos entrantes de una cuenta empresarial de Gmail. El flujo funciona de la siguiente manera:

1. **Detección de Correos**:  
   El módulo `Gmail > Watch Emails` monitorea la bandeja de entrada cada 15 minutos, detectando nuevos mensajes mediante conexión IMAP o API.

2. **Clasificación Automática**:  
   Un nodo `Router` filtra los correos usando condiciones no sensibles a mayúsculas:
   - Si el asunto **o** cuerpo contiene "urgente", el mensaje sigue la ruta de prioridad alta
   - Los correos normales siguen la ruta estándar

3. **Procesamiento Diferenciado**:
   - **Para urgentes**:
     - Aplica etiqueta "URGENTE" en Gmail
     - Registra en Google Sheets con estado "Pendiente"
   - **Para correos con otras etiquetas**:
     - Envía respuesta automática vía SMTP (Dependidendo su etiqueta dada).
     - Registra en Sheets como "Respondido"

4. **Registro Centralizado**:  
   Todos los correos se almacenan en Google Sheets con:
   ```plaintext
   Fecha | Remitente | Asunto | Categoría | Estado
![image](https://github.com/user-attachments/assets/c117d12f-be94-4dae-aeb4-3d028e5f8077)

## 📂 Estructura del Proyecto
blueprint.json: Definición del flujo de trabajo en formato JSON. README.md: Este archivo.


## Uso del JSON

1. **Importar el flujo**:
   - Descarga `Make_Flow.json`
   - En Make.com: *Create Scenario* → *Import* → Sube el archivo
   - Reconfigura las conexiones (Gmail, Google Sheets, SMTP)

2. **Pruebas**:
   ```plaintext
   1. Envía un correo de prueba a la cuenta monitoreada
   2. Verifica:
      - Respuesta automática recibida
      - Registro en Google Sheets
      - Etiquetado en Gmail (si es urgente)

## 👥 Autores

**David Sosa**   
**Alejandro Ramírez**  
---

## COntribuciones 

### ¡Las contribuciones son bienvenidas! Por favor, abre un issue o un pull request en este repositorio.
