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

     ![Vídeo-sin-título-‐-Hecho-con-Clipchamp](https://github.com/user-attachments/assets/3d62b659-2e76-46f0-818d-762a836461b7)



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
2. Crear credenciales OAuth 2.0 (tipo "Aplicación de escritorio").  
3. Descargar archivo JSON de credenciales.

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

