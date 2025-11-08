# chat-bot-final
# 🤖 Chatbot con IA - Asistente Inteligente + Noticias

## 📝 Descripción del Proyecto

Este proyecto es una aplicación web completa que combina un **chatbot inteligente** con capacidades de IA (usando Google Gemini) y un **sistema de noticias en tiempo real** consumiendo NewsAPI. 

La aplicación permite:
- 💬 Interactuar con un chatbot que puede asumir diferentes roles especializados (Asistente, Profesor, Traductor, Programador, Redactor, Coach de Carrera)
- � Ver noticias del mundo organizadas por país y categoría
- 🔄 Integración con APIs externas (Google Gemini y NewsAPI)
- 💾 Mantener el historial de conversaciones usando localStorage

---

## 👥 Roles y Contribuciones

**Desarrollador:** Yamila Anahí Martínez
- **Rol:** Full Stack Developer
- **Tareas Realizadas:**
  - ✅ Implementación del backend con Flask
  - ✅ Desarrollo de la API REST `/api/chat` para el chatbot
  - ✅ Integración con Google Gemini API para procesamiento de lenguaje natural
  - ✅ Sistema de gestión de memoria y contexto de conversación
  - ✅ Implementación de 6 roles especializados para el chatbot
  - ✅ Desarrollo del frontend con HTML, CSS (Bootstrap) y JavaScript vanilla
  - ✅ Integración con NewsAPI para noticias en tiempo real
  - ✅ Sistema de manejo de errores y validaciones
  - ✅ Diseño responsive de la interfaz de usuario
  - ✅ Implementación de procesamiento de Markdown en las respuestas

---

## 🛠️ Tecnologías Utilizadas

### Backend
- **Python 3.x** - Lenguaje de programación principal
- **Flask 3.0+** - Framework web para el backend
- **Flask-CORS** - Manejo de políticas CORS
- **Google Generative AI (Gemini)** - Modelo de IA para el chatbot
- **Requests** - Cliente HTTP para consumir APIs externas
- **Python-dotenv** - Gestión de variables de entorno
- **Pydantic** - Validación de datos

### Frontend
- **HTML5** - Estructura de las páginas
- **CSS3** - Estilos personalizados
- **Bootstrap 5.3** - Framework CSS para diseño responsive
- **JavaScript (ES6+)** - Lógica del cliente
- **LocalStorage API** - Persistencia de datos en el navegador

### APIs Externas
- **Google Gemini API** - Procesamiento de lenguaje natural
- **NewsAPI** - Noticias en tiempo real de múltiples fuentes

---

## 📁 Estructura del Proyecto

```
chat-bot-final/
├── app_unified.py          # ⭐ Aplicación Flask principal
├── chat_service.py         # Servicio de lógica del chatbot
├── llm_client.py           # Cliente para comunicarse con Gemini
├── config.py               # Configuración y variables de entorno
├── roles.py                # Definición de 6 roles del chatbot
├── prompts.py              # Generación de prompts del sistema
├── memory.py               # Gestión de memoria/historial de chat
├── requirements.txt        # Dependencias de Python
├── .env                    # Variables de entorno (NO subir a Git)
├── .env.example            # Ejemplo de variables de entorno
├── .gitignore              # Archivos ignorados por Git
├── README.md               # Este archivo
│
└── webapp/                 # Frontend de la aplicación
    ├── __init__.py
    ├── static/
    │   ├── css/
    │   │   └── app.css     # Estilos personalizados
    │   └── js/
    │       └── app.js      # Lógica del frontend del chat
    └── templates/          # Plantillas HTML
        ├── base.html       # Template base con navbar
        ├── chat.html       # Interfaz del chatbot
        └── noticias.html   # Página de noticias
```

---

## 🚀 Guía de Instalación y Ejecución

### Prerrequisitos

- Python 3.8 o superior instalado
- Una API Key de Google Gemini 
- Git instalado (para clonar el repositorio)

### Paso 1: Clonar el Repositorio

```bash
git clone https://github.com/YamilaMartinez1990/chat-inteligente.git
cd chat-bot-final
```

### Paso 2: Crear un Entorno Virtual

**En Windows (PowerShell):**
```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
```

**En Linux/Mac:**
```bash
python3 -m venv venv
source venv/bin/activate
```

### Paso 3: Instalar Dependencias

```bash
pip install -r requirements.txt
```

### Paso 4: Configurar Variables de Entorno

1. Copiar el archivo de ejemplo:
   ```bash
   # Windows
   copy .env.example .env
   
   # Linux/Mac
   cp .env.example .env
   ```

2. Editar el archivo `.env` y agregar API Key de Gemini:
   ```env
   GEMINI_API_KEY=tu_api_key_real_aqui
   MODEL=gemini-1.5-flash
   MAX_RETRIES=3
   TIMEOUT_SECONDS=30
   MAX_HISTORY=12
   SYSTEM_NAME=Chatbot Gemini
   ```

### Paso 5: Ejecutar la Aplicación

**Aplicación Unificada:**
```bash
python app_unified.py
```

La aplicación estará disponible en:

- 🏠 **Asistente IA:** <http://127.0.0.1:5000/>
- � **Noticias:** <http://127.0.0.1:5000/noticias>
- 🔌 **API del Chat:** POST <http://127.0.0.1:5000/api/chat>

---

## 📖 Uso de la Aplicación

### 💬 Chatbot

1. Acceder a <http://127.0.0.1:5000/>
2. En el sidebar izquierdo, seleccionar un rol para el chatbot
3. Escribir un mensaje en el campo de texto
4. Presionar "Enviar" o Enter
5. Esperar la respuesta del chatbot
6. El historial se guarda automáticamente en el navegador

**Roles disponibles:**

- **Asistente**: Ayudante general para cualquier consulta
- **Profesor**: Explica conceptos de forma didáctica
- **Traductor**: Traduce texto entre diferentes idiomas (exclusivamente traducción)
- **Programador**: Ayuda con código y problemas de programación (solo temas de programación)
- **Redactor Profesional**: Redacción y corrección de textos
- **Coach de Carrera**: Orientación profesional y desarrollo de carrera

### 📰 Noticias

1. Acceder a <http://127.0.0.1:5000/noticias>
2. Seleccionar país y categoría de interés
3. Hacer clic en "Cargar Noticias"
4. Navegar por las tarjetas de noticias
5. Hacer clic en "Leer más" para abrir la noticia completa en una nueva pestaña

---

## 🔌 API REST del Chatbot

### Endpoint: `/api/chat`

**Método:** POST

**Headers:**
```
Content-Type: application/json
```

**Body (JSON):**
```json
{
  "mensaje": "Hola, ¿cómo estás?",
  "role": "asistente",
  "reset": false
}
```

**Parámetros:**
- `mensaje` (string, requerido): El mensaje del usuario
- `role` (string, opcional): Rol del chatbot (`asistente`, `profesor`, `traductor`, `programador`)
- `reset` (boolean, opcional): Si es `true`, reinicia la conversación

**Respuesta exitosa (200):**
```json
{
  "respuesta": "¡Hola! Estoy muy bien, gracias por preguntar. ¿En qué puedo ayudarte hoy?"
}
```

**Respuesta de error (400):**
```json
{
  "error": "El mensaje no puede estar vacío"
}
```

### Ejemplo con cURL:

```bash
curl -X POST http://127.0.0.1:5000/api/chat \
  -H "Content-Type: application/json" \
  -d '{"mensaje": "Explícame qué es Python", "role": "profesor"}'
```

### Ejemplo con JavaScript (Fetch):

```javascript
fetch('http://127.0.0.1:5000/api/chat', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    mensaje: '¿Qué es Python?',
    role: 'profesor',
    reset: false
  })
})
.then(response => response.json())
.then(data => console.log(data.respuesta))
.catch(error => console.error('Error:', error));
```

---

## 🧪 Características Implementadas

### Backend

- ✅ Endpoint `/api/chat` para el chatbot
- ✅ Sistema de 6 roles especializados intercambiables
- ✅ Gestión de memoria/contexto de conversación
- ✅ Manejo de errores y validaciones
- ✅ Integración con Google Gemini API
- ✅ Integración con NewsAPI para noticias
- ✅ Manejo de errores HTTP (404, 500, 503)
- ✅ Procesamiento de Markdown en respuestas

### Frontend

- ✅ Interfaz de chat moderna y responsive
- ✅ Sidebar con 6 roles seleccionables
- ✅ Indicador de "escribiendo..." mientras espera respuesta
- ✅ Persistencia del historial en localStorage
- ✅ Botón para limpiar conversación
- ✅ Filtros por país y categoría para noticias
- ✅ Navegación entre Chat y Noticias
- ✅ Diseño responsive con Bootstrap
- ✅ Formato de texto con Markdown (negrita, cursiva, código)

---

## 🐛 Solución de Problemas

### Error: "No module named 'flask'"
**Solución:** Asegurarse de tener el entorno virtual activado e instalar dependencias:
```bash
pip install -r requirements.txt
```

### Error: "GEMINI_API_KEY not found"
**Solución:** Verificar que el archivo `.env` existe y contiene la API Key correcta.

### Error: "Connection refused" al acceder a la API
**Solución:** Verificar que el servidor Flask está corriendo en el puerto 5000.

### El chatbot no responde
**Solución:** 
1. Verificar la API Key de Gemini en `.env`
2. Revisar la consola del servidor para ver errores
3. Verificar conexión a internet

---

## 📦 Archivos Importantes

### `app_unified.py` ⭐

Archivo principal que ejecuta toda la aplicación. Combina el chatbot y las noticias.

### `chat_service.py`

Lógica del servicio de chat: gestiona roles, memoria e interacción con el modelo de IA.

### `config.py`

Configuración centralizada usando variables de entorno.

### `roles.py`

Define los 6 roles especializados que puede asumir el chatbot.

### `llm_client.py`

Cliente que se comunica con la API de Google Gemini.

### `memory.py`

Sistema de gestión de memoria para mantener el contexto de la conversación.

---

## 🔒 Seguridad

- ⚠️ **NUNCA** subir el archivo `.env` al repositorio
- ⚠️ Agregar `.env` al archivo `.gitignore`
- ⚠️ Agregar `.env.example` al archivo `.gitignore`
- ⚠️ Usar siempre variables de entorno para información sensible
- ⚠️ En producción, usar HTTPS y validar todas las entradas del usuario

---

## 📚 Recursos y Referencias

- [Documentación de Flask](https://flask.palletsprojects.com/)
- [Google Gemini API](https://ai.google.dev/docs)
- [Bootstrap 5](https://getbootstrap.com/docs/5.3/)
- [NewsAPI](https://newsapi.org/docs)

---

## 📝 Notas Adicionales

- NewsAPI tiene un plan gratuito con 100 requests/día
- El historial del chat se guarda en el navegador (localStorage), no en el servidor
- Para cambiar el modelo de IA, modificar la variable `MODEL` en el archivo `.env`
- Los roles especializados (Programador, Traductor, Redactor, Coach) solo responden consultas de su dominio

---

## 🎓 Créditos

Proyecto desarrollado como trabajo práctico final para Arquitectura y diseño de Interfaces.

**Desarrollado por:** Yamila Anahí Martínez  
**Fecha:** Noviembre 2025  
**Tecnologías:** Python, Flask, JavaScript, Google Gemini API, NewsAPI

---

## 📄 Licencia

Este proyecto es de uso educativo.

---

¿Preguntas o problemas? Contactar a:yamilauncuyo2024@gmail.com
