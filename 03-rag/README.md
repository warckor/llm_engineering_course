# 📚 RAG - Retrieval Augmented Generation

Este proyecto implementa un sistema de **Retrieval Augmented Generation (RAG)** que permite consultar documentos PDF utilizando técnicas de procesamiento de lenguaje natural y embeddings. El sistema divide documentos largos en fragmentos manejables, los convierte en representaciones vectoriales y permite realizar consultas inteligentes sobre el contenido.

## 🎯 Objetivo

Desarrollar un sistema RAG completo que permita:

- **Procesamiento de documentos PDF**: Extracción y análisis de texto
- **Segmentación inteligente**: División de contenido en chunks semánticamente coherentes
- **Generación de embeddings**: Representación vectorial del contenido
- **Consultas contextuales**: Respuestas basadas en contenido específico del documento
- **Integración con LLMs**: Uso de modelos de lenguaje para respuestas naturales

## 🛠️ Tecnologías Utilizadas

- **Python 3.13+**
- **LangChain Community** - Para carga y procesamiento de documentos
- **PyPDF** - Extracción de texto de archivos PDF
- **OpenAI API** - Modelos de lenguaje y embeddings
- **Tiktoken** - Tokenización y conteo de tokens
- **RecursiveCharacterTextSplitter** - Segmentación inteligente de texto
- **python-dotenv** - Gestión de variables de entorno

## 📁 Estructura del Proyecto

```text
03-rag/
├── .env                        # Variables de entorno (API keys)
├── .python-version            # Versión de Python requerida
├── pyproject.toml             # Configuración del proyecto y dependencias
├── uv.lock                    # Lock file para reproducibilidad
├── README.md                  # Este archivo
├── split-text.ipynb           # Implementación del sistema RAG
└── docs/
    └── Resolución exámenes TLP.pdf  # Documento de prueba
```

## 🚀 Funcionalidades Principales

### 1. Carga de Documentos PDF

Utiliza **PyPDFLoader** de LangChain para:

- **Extracción automática**: Texto de todas las páginas del PDF
- **Preservación de metadatos**: Información de páginas y estructura
- **Carga asíncrona**: Procesamiento eficiente de documentos grandes
- **Gestión de errores**: Manejo robusto de archivos corruptos o protegidos

```python
# Ejemplo de carga de documento
loader = PyPDFLoader("./docs/documento.pdf")
pages = []
async for page in loader.alazy_load():
    pages.append(page)
```

### 2. Segmentación Inteligente de Texto

Implementa **RecursiveCharacterTextSplitter** para:

- **División contextual**: Mantiene coherencia semántica en los fragmentos
- **Tamaño optimizado**: Chunks de 1000 caracteres con overlap de 200
- **Preservación de estructura**: Respeta párrafos y secciones
- **Flexibilidad configurable**: Parámetros ajustables según el tipo de documento

```python
# Configuración del splitter
splitter = RecursiveCharacterTextSplitter(
    chunk_size=1000, 
    chunk_overlap=200
)
chunks = splitter.split_documents(pages)
```

### 3. Generación de Embeddings

Integración con modelos de embedding para:

- **Representación vectorial**: Conversión de texto a vectores numéricos
- **Similitud semántica**: Búsqueda por significado, no solo palabras clave
- **Modelos variados**: Soporte para diferentes proveedores (OpenAI, Cohere)
- **Optimización de costos**: Procesamiento por lotes eficiente

### 4. Sistema de Consultas Contextuales

Implementa un pipeline completo de RAG:

- **Búsqueda semántica**: Encuentra fragmentos relevantes automáticamente
- **Contexto enriquecido**: Combina múltiples chunks para respuestas completas
- **Respuestas naturales**: Genera texto fluido basado en el contenido encontrado
- **Trazabilidad**: Identifica las fuentes utilizadas en cada respuesta

## ⚙️ Configuración

### 1. Variables de Entorno

Crear un archivo `.env` en la raíz del proyecto:

```env
# Para GitHub Models (alternativa gratuita)
GITHUB_TOKEN=tu_token_de_github
GITHUB_MODEL_URL=https://models.inference.ai.azure.com

# O para OpenAI oficial
OPENAI_API_KEY=tu_api_key_de_openai
OPENAI_BASE_URL=https://api.openai.com/v1

# Configuración de modelos
MODEL=cohere/cohere-command-a
EMBEDDING_MODEL=cohere/Cohere-embed-v3-multilingual
```

### 2. Instalación de Dependencias

```bash
# Usando uv (recomendado)
uv sync

# O usando pip tradicional
pip install langchain langchain-community pypdf openai tiktoken python-dotenv
```

### 3. Preparación de Documentos

```bash
# Crear directorio de documentos
mkdir -p docs/

# Copiar archivos PDF al directorio
cp tu_documento.pdf docs/
```

## 📊 Flujo de Trabajo RAG

### Fase 1: Procesamiento del Documento

1. **Carga**: Extracción de texto del PDF página por página
2. **Análisis**: Identificación de estructura y metadatos
3. **Segmentación**: División en chunks semánticamente coherentes
4. **Validación**: Verificación de integridad y calidad de los fragmentos

### Fase 2: Generación de Embeddings

1. **Preparación**: Limpieza y normalización de texto
2. **Embedding**: Conversión a representaciones vectoriales
3. **Almacenamiento**: Persistencia de vectores y metadatos
4. **Indexación**: Preparación para búsquedas eficientes

### Fase 3: Consulta y Respuesta

1. **Query processing**: Análisis de la consulta del usuario
2. **Retrieval**: Búsqueda de fragmentos más relevantes
3. **Context building**: Construcción del contexto para el LLM
4. **Generation**: Generación de respuesta natural y coherente

## 🔍 Análisis de Rendimiento

### Métricas de Tokenización

El sistema incluye análisis detallado de tokens para:

- **Optimización de costos**: Cálculo preciso de tokens consumidos
- **Gestión de contexto**: Verificación de límites de modelos
- **Eficiencia de prompts**: Optimización de system prompts
- **Monitoreo de uso**: Seguimiento de consumo de API

```python
# Ejemplo de análisis de tokens
encoding = tiktoken.get_encoding("cl100k_base")
system_prompt_tokens = len(encoding.encode(system_prompt))
print(f"Tokens en system prompt: {system_prompt_tokens}")
```

### Configuración de Modelos

#### Modelos de Lenguaje Probados

- **Cohere Command-A**: Excelente para tareas de RAG en español
- **OpenAI GPT-4.1-mini**: Modelo compacto y eficiente
- **Alternativas locales**: Compatible con LMStudio y Ollama

#### Modelos de Embedding

- **Cohere Embed v3 Multilingual**: Optimizado para idiomas múltiples
- **OpenAI text-embedding-3-small**: Eficiente y económico
- **Alternativas locales**: Sentence Transformers

## 🎓 Casos de Uso Implementados

### 1. Análisis de Exámenes Académicos

El proyecto incluye un ejemplo práctico con:

- **Documento**: Resolución de exámenes TLP (Teoría de Lenguajes de Programación)
- **Consultas típicas**: Búsqueda de soluciones específicas
- **Respuestas contextuales**: Explicaciones detalladas basadas en el contenido
- **Trazabilidad**: Referencias exactas a páginas y secciones

### 2. Consultoría Automatizada

Potencial para:

- **Base de conocimiento**: Consultas sobre documentación técnica
- **Soporte al cliente**: Respuestas automáticas basadas en manuales
- **Investigación académica**: Análisis de papers y publicaciones
- **Análisis legal**: Consultas sobre documentos normativos

## 🚀 Características Avanzadas

### Gestión Inteligente de Contexto

- **Límites dinámicos**: Adaptación automática a límites de modelo
- **Priorización**: Selección de chunks más relevantes cuando hay límites
- **Overlap estratégico**: Preservación de coherencia entre fragmentos
- **Metadata enrichment**: Información adicional sobre ubicación y relevancia

### Optimización de Rendimiento

- **Procesamiento por lotes**: Embedding múltiples chunks simultáneamente
- **Caché inteligente**: Reutilización de embeddings previamente calculados
- **Lazy loading**: Carga de documentos bajo demanda
- **Memory management**: Gestión eficiente de memoria para documentos grandes

## 📈 Métricas y Evaluación

### Calidad de Respuestas

- **Relevancia**: ¿La respuesta aborda la pregunta específica?
- **Completitud**: ¿Se incluye información suficiente?
- **Precisión**: ¿Los datos citados son correctos?
- **Coherencia**: ¿La respuesta es lógica y bien estructurada?

### Eficiencia del Sistema

- **Tiempo de respuesta**: Latencia desde consulta hasta respuesta
- **Uso de tokens**: Optimización de costos de API
- **Calidad de retrieval**: Precisión en la selección de chunks
- **Escalabilidad**: Rendimiento con documentos de diferentes tamaños

## 🔄 Integración y Extensibilidad

### APIs y Servicios

- **GitHub Models**: Acceso gratuito a modelos de IA para desarrollo
- **OpenAI API**: Modelos premium para producción
- **Cohere**: Especialización en modelos multilingües
- **Servicios locales**: LMStudio, Ollama para despliegues privados

### Extensiones Futuras

- **Vector databases**: Chroma, Pinecone, Weaviate para escalabilidad
- **Múltiples formatos**: Word, Excel, HTML, etc.
- **Interfaces de usuario**: Streamlit, FastAPI para demos
- **Evaluación automática**: Métricas de calidad automatizadas

## 🤝 Aprendizajes del Curso

### Conceptos Fundamentales

1. **RAG vs Fine-tuning**: Cuándo usar cada aproximación
2. **Chunking strategies**: Impacto en la calidad de respuestas
3. **Embedding selection**: Criterios para elegir modelos de embedding
4. **Prompt engineering**: Optimización de system prompts para RAG
5. **Cost management**: Estrategias para controlar gastos de API

### Técnicas Avanzadas

- **Hybrid search**: Combinación de búsqueda semántica y tradicional
- **Re-ranking**: Mejora de resultados con modelos especializados
- **Query expansion**: Enriquecimiento de consultas para mejor retrieval
- **Context compression**: Optimización de contexto para límites de token

## ⚠️ Consideraciones Importantes

### Privacidad y Seguridad

- **Datos sensibles**: Cuidado con información confidencial en APIs externas
- **Compliance**: Consideraciones GDPR y regulaciones locales
- **Modelos locales**: Alternativas para máxima privacidad
- **Audit trails**: Registro de consultas y respuestas

### Limitaciones Actuales

- **Tamaño de documentos**: Documentos muy grandes pueden requerir optimización
- **Formato de archivos**: Limitado a PDF (expandible a otros formatos)
- **Idioma**: Optimizado para español, pero funciona con otros idiomas
- **Actualización**: Los documentos requieren reprocesamiento tras cambios

## 📚 Recursos Adicionales

### Documentación Técnica

- [LangChain Documentation](https://python.langchain.com/docs/)
- [OpenAI API Reference](https://platform.openai.com/docs/)
- [Cohere Documentation](https://docs.cohere.com/)

### Papers y Referencias

- "Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks"
- "Dense Passage Retrieval for Open-Domain Question Answering"
- "In-Context Retrieval-Augmented Language Models"

### Herramientas Recomendadas

- **Vector databases**: Chroma, Pinecone, Weaviate
- **Evaluation**: RAGAS, TruLens
- **Monitoring**: LangSmith, Weights & Biases
- **UI/UX**: Streamlit, Gradio, Chainlit

Este proyecto representa una implementación completa y educativa de un sistema RAG, proporcionando una base sólida para aplicaciones más avanzadas de inteligencia artificial aplicada al procesamiento de documentos.
