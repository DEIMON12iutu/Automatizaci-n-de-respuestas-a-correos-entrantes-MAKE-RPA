# Automatizacion-de-respuestas-a-correos-entrantes-MAKE-RPA
Este proyecto presenta una solución de automatización de procesos robóticos (RPA) utilizando como plataforma MAKE.com.

# Automatización de Respuestas a Correos con Make.com (RPA)
![Make.com Logo]![image](https://github.com/user-attachments/assets/8223e1ed-963d-4d1a-94dc-ad8b79c15909)


Este proyecto implementa un flujo de automatización (RPA) en **Make.com** para:
- **Clasificar** correos entrantes mediante **filtros nativos** (palabra clave "urgente","facturacion,"ayuda")
- **Responder automáticamente** usando plantillas predefinidas
- **Registrar datos** en Google Sheets
- **Gestionar prioridades** con etiquetas de Gmail
![image](https://github.com/user-attachments/assets/57d8d844-1d16-487e-9173-a1a7572f6d9f)

## Descripción

Este flujo en Make.com monitorea una cuenta de Gmail empresarial mediante conexión IMAP/API, utilizando filtros programables en nodos Router para clasificar automáticamente los correos en categorías ("urgente", "facturación", "consulta", "general"). Para cada categoría ejecuta acciones específicas: envía respuestas automáticas mediante plantillas SMTP preconfiguradas, registra los detalles del correo (remitente, asunto, categoría y fecha/hora) en Google Sheets.

Desarrollado como solución RPA nativa en Make, el sistema optimiza la gestión de correos corporativos reduciendo tiempos de respuesta de horas a minutos, manteniendo trazabilidad completa mediante integración con Google Sheets. La implementación utiliza exclusivamente funcionalidades nativas de la paltoaforma sin dependencia de APIs externas de IA, garantizando estabilidad y seguridad en entornos empresariales.


![Vídeo-sin-título-‐-Hecho-con-Clipchamp](https://github.com/user-attachments/assets/75de1878-6861-484f-bba4-c2302cf18041)


##  Beneficios Clave
| Característica | Ventaja |
|----------------|---------------|
| **Filtros nativos** | Sin dependencia de APIs de IA (bajo costo) |
| **Plantillas personalizables** | Respuestas consistentes según categoría |
| **Integración directa** | Conexión nativa con Google Workspace |
| **Escalable** | Añade más reglas sin modificar la estructura |


##  Requisitos Técnicos

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
   - Gmail API  
   - Google Sheets API
   
2. Descargar archivo JSON de credenciales.

### 3. **Recursos Adicionales**  
- **Plantilla de Google Sheets**:  
  - Columnas mínimas requeridas:  
    ```plaintext
    Fecha | Remitente | Asunto | Categoría | Respondido  
    ```

# Configuración del Flujo en Make.com

##  Importar el Flujo
1. **Exporta tu flujo actual**:
   - En Make.com, ve a tu escenario > Haz clic en el menú de tres puntos (⋮) > Selecciona **"Export"**.
   - Guarda el archivo `GmailAutomation.json` en tu computadora.

2. **Importar en otro entorno**:
   ```plaintext
   • Crea un nuevo escenario en Make.com
   • Haz clic en "Import" > Sube el archivo JSON
   • Revisa que todos los módulos estén conectados

## Flujo de trabajo  
**Gmail Trigger (IMAP/API):** Monitorea correos entrantes en la cuenta configurada. **Router:** Filtra y clasifica los correos usando condiciones programables (palabra clave "urgente"). **Send Email:** Envía respuestas automáticas mediante plantillas SMTP predefinidas. **Google Sheets:** Registra los detalles del correo (remitente, asunto, categoría y fecha) en la hoja de cálculo. **Etiquetado Gmail:** Marca automáticamente los correos urgentes con una etiqueta específica para seguimiento interno.

![image](https://github.com/user-attachments/assets/c117d12f-be94-4dae-aeb4-3d028e5f8077)

##  Estructura del Proyecto
blueprint.json: Definición del flujo de trabajo en formato JSON. README.md: Este archivo.


## Uso del JSON

1. **Importar el flujo**:
   - Descarga `blueprint.json`
   - En Make.com: *Create Scenario* → *Import* → Sube el archivo

2. **Pruebas**:
   ```plaintext
   1. Envía un correo de prueba a la cuenta monitoreada
   2. Verifica:
      
##  Autores
**David Sosa**  Y
**Alejandro Ramírez**  
---

## Contribuciones 

### ¡Las contribuciones son bienvenidas! Por favor, abre un issue o un pull request en este repositorio.
