# 📰 Web Summarizer - DevOps News

Este proyecto implementa un sistema de web scraping y resumen automático de noticias de DevOps utilizando diferentes modelos de inteligencia artificial. El sistema está diseñado para extraer contenido de sitios web especializados en DevOps y generar resúmenes concisos utilizando modelos de lenguaje avanzados.

## 🎯 Objetivo

Desarrollar una herramienta que automatice la extracción y el resumen de contenido web especializado en DevOps, comparando el rendimiento de diferentes modelos de IA:

- **Google Gemini 2.5 Flash** (API)
- **LMStudio** (servidor local)
- **Ollama** (modelo local)

## 🛠️ Tecnologías Utilizadas

- **Python 3.13+**
- **Beautiful Soup 4** - Para web scraping y parsing HTML
- **Requests** - Para realizar peticiones HTTP
- **Google Generative AI** - Para integración con Gemini
- **OpenAI API** - Para LMStudio
- **Ollama Python Client** - Para modelos locales
- **python-dotenv** - Para gestión de variables de entorno
- **IPython** - Para visualización mejorada en notebooks

## 📁 Estructura del Proyecto

```text
01-web-summarizer/
├── .env                           # Variables de entorno (API keys)
├── .python-version               # Versión de Python requerida
├── pyproject.toml               # Configuración del proyecto y dependencias
├── uv.lock                      # Lock file para reproducibilidad
├── README.md                    # Este archivo
├── devops_news_gemini.ipynb     # Implementación con Google Gemini
├── devops_news_lmstudio.ipynb   # Implementación con LMStudio
└── devops_news_ollama.ipynb     # Implementación con Ollama
```

## 🚀 Funcionalidades Principales

### Clase Scrapper

- **Extracción de contenido web**: Obtiene HTML de URLs especificadas
- **Limpieza automática**: Remueve elementos irrelevantes (scripts, estilos, navegación)
- **Parsing inteligente**: Extrae título y contenido textual limpio
- **Gestión de errores**: Manejo robusto de errores de red y parsing

### Implementaciones por Modelo

#### 1. Google Gemini (devops_news_gemini.ipynb)

- Utiliza la API de Google Generative AI
- Modelo: `gemini-2.5-flash`
- Configuración optimizada para resúmenes concisos
- Formato de salida en Markdown

#### 2. LMStudio (devops_news_lmstudio.ipynb)

- Conexión a servidor local de LMStudio
- Compatible con modelos OpenAI
- Flexibilidad para diferentes modelos locales
- Control total sobre parámetros de generación

#### 3. Ollama (devops_news_ollama.ipynb)

- Integración nativa con Ollama
- Modelos completamente locales
- Sin dependencia de APIs externas
- Ideal para privacidad y desarrollo offline

## ⚙️ Configuración

### 1. Instalación de Dependencias

```bash
# Usando uv (recomendado)
uv sync

# O usando pip tradicional
pip install -r requirements.txt
```

### 2. Variables de Entorno

Crear un archivo `.env` en la raíz del proyecto:

```env
# Para Google Gemini
GEMINI_API_KEY=tu_api_key_de_gemini

# Para LMStudio (si usas servidor local)
LMSTUDIO_BASE_URL=http://localhost:1234/v1
LMSTUDIO_API_KEY=lm-studio

# Para Ollama (si usas servidor remoto)
OLLAMA_HOST=http://localhost:11434
```

### 3. Configuración de Modelos Locales

#### LMStudio

1. Instalar LMStudio desde [https://lmstudio.ai/](https://lmstudio.ai/)
2. Descargar un modelo compatible (ej: Llama 2, Code Llama)
3. Iniciar el servidor local en puerto 1234

#### Ollama

1. Instalar Ollama desde [https://ollama.ai/](https://ollama.ai/)
2. Descargar modelos: `ollama pull llama2`
3. El servidor se ejecuta automáticamente en puerto 11434

## 📊 Uso

### Ejecución Básica

1. **Abrir el notebook deseado** en Jupyter Lab/VSCode
2. **Configurar la URL objetivo** (por defecto: DevOpsCube)
3. **Ejecutar las celdas secuencialmente**
4. **Revisar el resumen generado**

### Ejemplo de Uso

```python
# Inicializar el scrapper
scrapper = Scrapper()
content = scrapper.get_content("https://devopscube.com/blog/")

# Procesar con IA (ejemplo con Gemini)
response = client.models.generate_content(
    model=MODEL,
    contents=f"Resume el siguiente contenido: {content.body}"
)

# Mostrar resultado
display(Markdown(response.text))
```

## 🔍 Características del Scrapper

- **Filtrado inteligente**: Remueve automáticamente elementos HTML irrelevantes
- **Extracción de texto limpio**: Obtiene contenido textual sin formato
- **Gestión de títulos**: Extrae y preserva títulos de página
- **Handling de errores**: Gestión robusta de errores de red y parsing
- **Configurabilidad**: Fácil adaptación a diferentes sitios web

## 📈 Casos de Uso

1. **Monitoreo de noticias DevOps**: Resúmenes automáticos de blogs especializados
2. **Investigación de tendencias**: Análisis de contenido de múltiples fuentes
3. **Boletines informativos**: Generación automática de newsletters
4. **Análisis comparativo**: Evaluación de diferentes modelos de IA
5. **Prototipado rápido**: Base para sistemas de resumen más complejos

## 🎓 Aprendizajes del Curso

Este proyecto forma parte del módulo de introducción a la inteligencia artificial generativa, donde se exploran:

- **Integración de APIs de IA**: Trabajo con diferentes proveedores (Google, OpenAI)
- **Modelos locales vs. en la nube**: Comparación de ventajas y limitaciones
- **Web scraping responsable**: Técnicas de extracción de contenido web
- **Prompt engineering**: Optimización de prompts para resúmenes de calidad
- **Gestión de entornos**: Configuración de proyectos con múltiples dependencias

## 📝 Notas Técnicas

- **Compatibilidad**: Requiere Python 3.13 o superior
- **Dependencias**: Todas las dependencias están especificadas en `pyproject.toml`
- **Seguridad**: Las API keys deben mantenerse en `.env` y nunca commitear al repositorio
- **Rendimiento**: Los modelos locales pueden ser más lentos pero ofrecen mayor privacidad
- **Rate limiting**: Considerar límites de API al usar servicios externos
