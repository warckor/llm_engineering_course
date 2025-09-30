# 🤖 Curso de Inteligencia Artificial Generativa

Este repositorio contiene los proyectos prácticos desarrollados durante el curso de introducción a la inteligencia artificial generativa. Cada proyecto explora diferentes aspectos de la IA moderna, desde el web scraping con modelos de lenguaje hasta sistemas RAG avanzados.

## 📚 Contenido del Curso

### Módulos Desarrollados

1. **[01-web-summarizer](./01-web-summarizer/)** - Sistema de resumen automático de contenido web
2. **[02-genai-first-steps](./02-genai-first-steps/)** - Primeros pasos con modelos de lenguaje generativo
3. **[03-rag](./03-rag/)** - Sistema de Retrieval Augmented Generation para documentos

## 🎯 Objetivos de Aprendizaje

Este curso práctico aborda:

- **Integración con APIs de IA**: Google Gemini, OpenAI, Cohere
- **Modelos locales**: LMStudio, Ollama, Hugging Face Transformers
- **Técnicas de procesamiento**: Web scraping, tokenización, embeddings
- **Arquitecturas modernas**: RAG, chat conversacional, análisis de documentos
- **Optimización**: Cuantización, gestión de memoria, control de costos

## 🚀 Proyectos Implementados

### 1. 📰 Web Summarizer - Resumen Automático de Noticias

**Ubicación**: `01-web-summarizer/`

Sistema completo de web scraping y resumen automático de noticias DevOps utilizando múltiples modelos de IA.

#### Características Principales

- **Web Scraping Inteligente**: Clase `Scrapper` para extracción limpia de contenido
- **Múltiples Modelos**: Implementaciones con Gemini, LMStudio y Ollama
- **Procesamiento Robusto**: Limpieza automática de HTML y manejo de errores
- **Formato Optimizado**: Salida en Markdown para mejor legibilidad

#### Tecnologías Clave

```bash
- Beautiful Soup 4 (web scraping)
- Google Generative AI (Gemini 2.5 Flash)
- OpenAI API (LMStudio)
- Ollama Python Client
- Requests + python-dotenv
```

#### Casos de Uso

- Monitoreo automatizado de blogs DevOps
- Generación de boletines informativos
- Análisis comparativo de modelos de IA
- Investigación de tendencias tecnológicas

### 2. 🤖 Primeros Pasos con IA Generativa

**Ubicación**: `02-genai-first-steps/`

Exploración práctica de conceptos fundamentales en inteligencia artificial generativa, incluyendo tokenización y chat con modelos locales.

#### Experimentos Realizados

##### Chat Casual con LLMs Locales

- **Modelos explorados**: Microsoft Phi-3, Qwen2.5-7B, Falcon3-7B
- **Optimización de memoria**: Cuantización 4-bit con BitsAndBytesConfig
- **Streaming**: Generación de respuestas en tiempo real
- **Templates específicos**: Formatos optimizados por modelo

##### Análisis de Tokenización

- **Tipos de tokenización**: BPE, WordPiece, SentencePiece
- **Comparación de vocabularios**: Entre diferentes arquitecturas
- **Optimización de contexto**: Técnicas para reducir tokens
- **Análisis multilingüe**: Eficiencia español vs inglés

#### Stack Tecnológico

```bash
- Transformers (Hugging Face)
- PyTorch + BitsAndBytes
- Tiktoken (tokenización OpenAI)
- Google Colab (entorno de desarrollo)
```

#### Aprendizajes Clave

- Gestión eficiente de memoria GPU
- Técnicas de cuantización para democratizar IA
- Prompt engineering básico
- Evaluación cualitativa de modelos

### 3. 📚 RAG - Retrieval Augmented Generation

**Ubicación**: `03-rag/`

Sistema completo de consulta inteligente de documentos PDF utilizando técnicas de RAG (Retrieval Augmented Generation).

#### Pipeline RAG Completo

- Carga automática y segmentación de documentos PDF
- Generación de embeddings con modelos OpenAI, Cohere o GitHub Models
- Almacenamiento persistente en ChromaDB
- Recuperación semántica y respuestas contextuales usando LLM
- Soporte para historial conversacional (history-aware retriever)
- Ejemplo de consultas encadenadas y memoria de chat

#### Notebooks Destacados

- **simple-rag.ipynb**: Implementa el flujo completo de RAG sobre PDF, con ejemplos de preguntas encadenadas y memoria conversacional.
- **split-text.ipynb**: Ejemplo de segmentación y análisis de texto en documentos PDF.

##### Procesamiento de Documentos

- **Carga de PDFs**: PyPDFLoader con soporte asíncrono
- **Segmentación inteligente**: RecursiveCharacterTextSplitter (chunks configurables)
- **Preservación de metadatos**: Información de páginas y estructura
- **Gestión de errores**: Manejo robusto de archivos problemáticos

##### Sistema de Consultas

- **Embeddings semánticos**: OpenAI, Cohere, GitHub Models
- **Búsqueda contextual**: Similitud por significado, no palabras clave
- **Generación de respuestas**: LLM optimizados para español
- **Trazabilidad**: Referencias exactas a fuentes utilizadas

#### Herramientas Utilizadas

```bash
- LangChain Community (procesamiento documentos)
- PyPDF (extracción texto PDF)
- OpenAI API / Cohere / GitHub Models (modelos y embeddings)
- Tiktoken (análisis de tokens)
- python-dotenv (gestión variables)
```

#### Caso de Uso Práctico

**Análisis de Exámenes TLP**: Sistema para consultar resoluciones de exámenes de Teoría de Lenguajes de Programación, permitiendo búsquedas específicas y explicaciones contextuales basadas en el contenido del documento.

## 🛠️ Stack Tecnológico Común

### Lenguajes y Frameworks

- **Python 3.13+**: Lenguaje principal del curso
- **Jupyter Notebooks**: Entorno de desarrollo interactivo
- **UV**: Gestión moderna de dependencias Python

### APIs y Servicios

- **GitHub Models**: Acceso gratuito para desarrollo
- **Google Gemini**: Modelos de última generación
- **OpenAI API**: Estándar de la industria
- **Cohere**: Especialización en modelos multilingües

### Herramientas Locales

- **LMStudio**: Servidor local de modelos
- **Ollama**: Ejecución de modelos en local
- **Hugging Face**: Ecosistema de modelos open source

## 📊 Progresión del Aprendizaje

### Nivel Básico (Proyecto 1)

- Integración básica con APIs
- Manejo de requests HTTP
- Procesamiento de texto simple
- Comparación de modelos

### Nivel Intermedio (Proyecto 2)

- Modelos locales y optimización
- Técnicas de cuantización
- Análisis profundo de tokenización
- Gestión de memoria y recursos

### Nivel Avanzado (Proyecto 3)

- Arquitecturas RAG complejas
- Procesamiento de documentos
- Embeddings y búsqueda semántica
- Integración de múltiples componentes

## 🎓 Competencias Desarrolladas

### Técnicas

- **Web Scraping**: Extracción inteligente de contenido web
- **Prompt Engineering**: Optimización de instrucciones para IA
- **Model Selection**: Criterios para elegir modelos apropiados
- **Cost Optimization**: Estrategias para controlar gastos de API
- **Performance Tuning**: Optimización de memoria y velocidad

### Conceptuales

- **RAG vs Fine-tuning**: Cuándo usar cada aproximación
- **Local vs Cloud**: Ventajas y limitaciones de cada opción
- **Tokenization Impact**: Cómo afecta a rendimiento y costos
- **Embedding Quality**: Criterios para evaluar representaciones
- **Context Management**: Gestión eficiente de límites de contexto

## 🚀 Configuración Rápida

### Requisitos Previos

```bash
# Python 3.13+
python --version

# UV para gestión de dependencias
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### Instalación por Proyecto

```bash
# Proyecto 1: Web Summarizer
cd 01-web-summarizer/
uv sync
cp .env.example .env  # Configurar API keys

# Proyecto 2: GenAI First Steps
cd ../02-genai-first-steps/
uv sync
# Configurar tokens HuggingFace si es necesario

# Proyecto 3: RAG System
cd ../03-rag/
uv sync
cp .env.example .env  # Configurar API keys
```

### Variables de Entorno Necesarias

```env
# Para proyectos que usan APIs externas
GEMINI_API_KEY=tu_gemini_api_key
GITHUB_TOKEN=tu_github_token
GITHUB_MODEL_URL=https://models.inference.ai.azure.com
OPENAI_API_KEY=tu_openai_api_key
HF_TOKEN=tu_huggingface_token  # Opcional para modelos privados
```

## 📈 Casos de Uso Reales

### Empresariales

- **Monitoreo de competencia**: Análisis automático de contenido de la competencia
- **Soporte al cliente**: Sistemas de respuesta automática basados en documentación
- **Investigación de mercado**: Análisis de tendencias en publicaciones especializadas
- **Gestión documental**: Consulta inteligente de bases de conocimiento corporativas

### Educativos

- **Análisis de literatura**: Procesamiento de papers académicos
- **Asistentes de estudio**: Consulta de material de curso
- **Evaluación automática**: Análisis de respuestas y exámenes
- **Tutoría personalizada**: Respuestas adaptadas al contexto del estudiante

### Personales

- **Asistente de lectura**: Resúmenes de artículos largos
- **Organización de información**: Clasificación automática de contenido
- **Investigación personal**: Consulta eficiente de documentos propios
- **Aprendizaje continuo**: Exploración guiada de nuevos temas

## 🔄 Evolución del Curso

### Fase 1: Fundamentos (Proyecto 1)

- Comprensión básica de APIs de IA
- Integración simple con modelos externos
- Procesamiento básico de contenido web

### Fase 2: Profundización (Proyecto 2)

- Exploración de modelos locales
- Técnicas de optimización avanzadas
- Comprensión profunda de tokenización

### Fase 3: Aplicación Avanzada (Proyecto 3)

- Arquitecturas complejas de IA
- Integración de múltiples tecnologías
- Aplicación práctica a casos reales

## 📚 Recursos Adicionales

### Documentación Oficial

- [LangChain Documentation](https://python.langchain.com/docs/)
- [Hugging Face Transformers](https://huggingface.co/docs/transformers/)
- [OpenAI API Reference](https://platform.openai.com/docs/)
- [Google AI Studio](https://aistudio.google.com/)

### Papers de Referencia

- "Attention Is All You Need" (Transformer Architecture)
- "Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks"
- "Language Models are Few-Shot Learners" (GPT-3)
- "Training language models to follow instructions with human feedback"

### Herramientas Recomendadas

- **VS Code**: Editor con excelente soporte para Python e IA
- **Jupyter Lab**: Entorno avanzado para notebooks
- **Docker**: Para despliegues consistentes
- **Git**: Control de versiones (esencial para proyectos de IA)

## 🎖️ Logros del Curso

Al completar estos proyectos, has desarrollado competencias en:

✅ **Integración de APIs de IA modernas**  
✅ **Implementación de sistemas RAG**  
✅ **Optimización de modelos locales**  
✅ **Procesamiento inteligente de documentos**  
✅ **Web scraping para IA**  
✅ **Técnicas de tokenización avanzadas**  
✅ **Gestión eficiente de recursos computacionales**  
✅ **Evaluación y comparación de modelos**

## 📧 Soporte y Comunidad

Para dudas, sugerencias o contribuciones:

- **Issues**: Utiliza el sistema de issues de GitHub
- **Discusiones**: Participa en las discusiones del repositorio
- **Pull Requests**: Contribuye con mejoras y nuevas características

---

*Este curso representa una introducción práctica y completa al mundo de la inteligencia artificial generativa, proporcionando las bases necesarias para desarrollar aplicaciones avanzadas y comprender las tecnologías emergentes en el campo de la IA.*
