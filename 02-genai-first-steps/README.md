# 🤖 Primeros Pasos con IA Generativa

Este proyecto contiene experimentos iniciales con modelos de lenguaje de gran escala (LLMs) y tecnologías de inteligencia artificial generativa. Se enfoca en el aprendizaje práctico de conceptos fundamentales como tokenización, inferencia local de modelos y chat casual con diferentes arquitecturas de IA.

## 🎯 Objetivo

Explorar los fundamentos de la inteligencia artificial generativa mediante:

- **Comprensión de tokenización**: Cómo los modelos procesan texto
- **Inferencia local de modelos**: Ejecución de LLMs sin APIs externas
- **Comparación de arquitecturas**: Evaluación de diferentes familias de modelos
- **Optimización de recursos**: Técnicas de cuantización y gestión de memoria

## 🛠️ Tecnologías Utilizadas

- **Python 3.13+**
- **Transformers (Hugging Face)** - Para carga y ejecución de modelos
- **PyTorch** - Framework de deep learning
- **BitsAndBytesConfig** - Para cuantización de modelos
- **Tiktoken** - Tokenizador de OpenAI
- **Google Colab** - Entorno de desarrollo (opcional)

## 📁 Estructura del Proyecto

```text
02-genai-first-steps/
├── .python-version               # Versión de Python requerida
├── pyproject.toml               # Configuración del proyecto
├── README.md                    # Este archivo
├── chatcasual_localllm.ipynb    # Chat con modelos locales
└── Tokenizers.ipynb             # Exploración de tokenización
```

## 🚀 Experimentos Realizados

### 1. Chat Casual con LLMs Locales (chatcasual_localllm.ipynb)

Este notebook implementa un sistema de chat utilizando modelos de lenguaje ejecutados localmente en Google Colab.

#### Modelos Explorados

- **Microsoft Phi-3-mini-128k-instruct**: Modelo compacto y eficiente
- **Qwen2.5-7B-Instruct-1M**: Modelo de 7B parámetros con contexto extendido
- **Falcon3-7B-Base**: Arquitectura Falcon para generación de texto

#### Características Técnicas

- **Cuantización inteligente**: Uso de BitsAndBytesConfig para optimizar memoria
- **Streaming de respuestas**: Generación de texto en tiempo real
- **Gestión de memoria GPU**: Configuración automática según recursos disponibles
- **Templates de conversación**: Formatos específicos para cada modelo

#### Configuraciones de Cuantización

```python
# Cuantización 4-bit para optimizar memoria
quantization_config = BitsAndBytesConfig(
    load_in_4bit=True,
    bnb_4bit_compute_dtype=torch.float16,
    bnb_4bit_quant_type="nf4"
)
```

### 2. Exploración de Tokenización (Tokenizers.ipynb)

Análisis profundo del proceso de tokenización y su impacto en el rendimiento de los modelos.

#### Conceptos Explorados

- **Tipos de tokenización**: Byte-pair encoding (BPE), WordPiece, SentencePiece
- **Vocabularios de modelos**: Comparación entre diferentes arquitecturas
- **Longitud de contexto**: Límites y optimizaciones
- **Encoding/Decoding**: Conversión bidireccional texto-tokens

#### Experimentos Prácticos

- **Análisis comparativo**: Tokenización del mismo texto con diferentes modelos
- **Cálculo de tokens**: Estimación de costos y límites de contexto
- **Visualización**: Representación gráfica del proceso de tokenización
- **Optimización**: Técnicas para reducir el número de tokens

## ⚙️ Configuración

### 1. Requisitos del Sistema

```bash
# Memoria RAM recomendada: 16GB+
# GPU: CUDA compatible (opcional pero recomendado)
# Espacio en disco: 20GB+ para modelos
```

### 2. Instalación de Dependencias

```bash
# Instalación automática en notebooks
!pip install -q requests torch bitsandbytes transformers sentencepiece accelerate

# O usando el entorno local
pip install transformers torch bitsandbytes accelerate
```

### 3. Configuración de Hugging Face

```python
# Autenticación (requerida para algunos modelos)
from huggingface_hub import login
login(token="tu_huggingface_token")
```

## 📊 Experimentos y Resultados

### Comparación de Modelos

| Modelo     | Parámetros | Memoria (4-bit) | Velocidad | Calidad   |
| ---------- | ---------- | --------------- | --------- | --------- |
| Phi-3-mini | 3.8B       | ~2.5GB          | Rápido    | Buena     |
| Qwen2.5    | 7B         | ~4.5GB          | Medio     | Excelente |
| Falcon3    | 7B         | ~4.5GB          | Medio     | Muy buena |

### Análisis de Tokenización

- **Eficiencia por idioma**: Comparación español vs inglés
- **Patrones de token**: Identificación de elementos comunes
- **Optimización de prompts**: Técnicas para reducir tokens
- **Límites de contexto**: Gestión de conversaciones largas

## 🎓 Aprendizajes Clave

### Conceptos Fundamentales

1. **Tokenización es crucial**: Afecta directamente costos y rendimiento
2. **Cuantización permite democratización**: Modelos grandes en hardware limitado
3. **Cada modelo tiene personalidad**: Diferentes estilos y capacidades
4. **La optimización es esencial**: Balance entre calidad y recursos

### Técnicas Aprendidas

- **Gestión de memoria GPU**: Configuración eficiente para diferentes tamaños de modelo
- **Prompt engineering básico**: Construcción de mensajes efectivos
- **Evaluación cualitativa**: Métodos para comparar salidas de modelos
- **Debugging de modelos**: Identificación y resolución de problemas comunes

## 🔍 Casos de Uso Prácticos

1. **Asistente personal local**: Chat privado sin dependencias externas
2. **Análisis de texto**: Comprensión de estructura y contenido
3. **Prototipado rápido**: Experimentación con diferentes modelos
4. **Educación**: Comprensión práctica de conceptos de IA
5. **Investigación**: Base para proyectos más avanzados

## 🚀 Próximos Pasos

### Mejoras Sugeridas

- **Fine-tuning**: Adaptación de modelos a casos específicos
- **Benchmarking automático**: Evaluación sistemática de rendimiento
- **Interface de usuario**: Desarrollo de chat web interactivo
- **Optimización avanzada**: Técnicas de compresión y aceleración

### Experimentos Futuros

- **Modelos multimodales**: Integración de texto e imágenes
- **Agents**: Sistemas de IA con capacidad de acción
- **RAG avanzado**: Integración con bases de conocimiento
- **Deploy en producción**: Sistemas escalables y robustos

## 📚 Recursos Adicionales

### Documentación

- [Hugging Face Transformers](https://huggingface.co/docs/transformers/)
- [PyTorch Documentation](https://pytorch.org/docs/)
- [BitsAndBytes Guide](https://github.com/TimDettmers/bitsandbytes)

### Modelos Recomendados

- **Para empezar**: Microsoft Phi-3-mini
- **Calidad/Rendimiento**: Qwen2.5-7B
- **Experimentación**: Falcon3-7B
- **Producción**: Llama 2/3 (según licencia)

## ⚠️ Consideraciones Importantes

### Recursos Computacionales

- **GPU recomendada**: Para modelos de 7B+ parámetros
- **Tiempo de carga**: Los modelos pueden tardar varios minutos en cargar
- **Espacio de almacenamiento**: Los modelos ocupan varios GB

### Licencias y Uso

- **Revisar licencias**: Cada modelo tiene términos específicos
- **Uso responsable**: Evitar contenido inapropiado o dañino
- **Privacidad**: Los modelos locales protegen datos sensibles
- **Costos**: Considerar uso de GPU en plataformas cloud

## 📝 Notas del Curso

Este proyecto forma parte del módulo introductorio donde se cubren:

- **Fundamentos teóricos**: Arquitecturas transformer y attention
- **Implementación práctica**: Uso de librerías y frameworks
- **Optimización**: Técnicas para recursos limitados
- **Evaluación**: Métodos para medir calidad y rendimiento
- **Ética**: Consideraciones sobre sesgos y uso responsable
