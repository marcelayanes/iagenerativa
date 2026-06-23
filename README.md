# Pipelines de IA Generativa: RAG y Sistemas Multiagente (CrewAI)

Conjunto de notebooks ejecutables en Google Colab (GPU T4) que implementan
arquitecturas de Generación Aumentada por Recuperación (RAG) con LangChain
y sistemas multiagente con CrewAI, usando modelos reales de Hugging Face
como motor de generación.

## Notebooks

| Notebook | Tema | Stack |
|---|---|---|
| `01_crewai_multiagente_colab_t4.ipynb` | Pipeline secuencial de 2 agentes (Investigador → Redactor) | CrewAI, Transformers |
| `02_langchain_rag_soporte_colab_t4.ipynb` | RAG para soporte al cliente con capa de verificación factual desacoplada de la generación | LangChain, FAISS, Qwen2.5-0.5B-Instruct |
| `03_langchain_rag_citas_colab_t4.ipynb` | RAG con trazabilidad de fuentes (citas tipo `[DOC-01]`) | LangChain, FAISS, Qwen2.5-0.5B-Instruct |
| `04_crewai_analisis_producto_colab_t4.ipynb` | Pipeline de 3 agentes (Analista de producto → Especialista de riesgos → Coordinador) | CrewAI, Transformers |
| `05_crewai_revision_codigo_colab_t4.ipynb` | Revisión automatizada de código con 3 agentes (Bugs → Pruebas → Reporte) | CrewAI, Transformers |

## Detalles técnicos

- **Modelos base:** `Qwen/Qwen2.5-0.5B-Instruct` (RAG) y `sshleifer/tiny-gpt2` (CrewAI), cargados directamente desde Hugging Face Hub.
- **Generación con chat templates:** uso de `apply_chat_template` para formatear correctamente las instrucciones al modelo instruct.
- **Embeddings propios para RAG:** clase `TransformerEmbeddings` que extrae hidden states del modelo para generar vectores, indexados en FAISS.
- **Mitigación de alucinaciones (notebook 02):** arquitectura de verificación factual desacoplada de la generación. Una función (`evaluar_politica`) extrae del contexto recuperado los valores relevantes (días transcurridos, plazo permitido, tiempo de procesamiento) y calcula determinísticamente si la solicitud procede. El LLM solo redacta sobre ese resultado ya verificado, sin decidir ni inventar cifras — evita que el modelo "alucine" conclusiones no sustentadas por los datos.
- **Trazabilidad de fuentes (notebook 03):** uso de identificadores explícitos (`[DOC-01]`, `[DOC-02]`...) para que cada afirmación generada pueda rastrearse a su documento de origen.
- **LLM personalizado para CrewAI:** clase `HuggingFaceCrewLLM` que extiende `BaseLLM` para integrar un modelo local de Transformers como backend de los agentes.
- **Entorno:** Google Colab, GPU T4, instalación reproducible vía `pip` (versiones fijadas para `crewai`, `langchain`, `transformers`).

## Cómo ejecutar

1. Abrir cualquier notebook en Google Colab.
2. Ejecutar la celda de instalación (`%%capture`).
3. Reiniciar el entorno de ejecución si es la primera vez (celda indicada, solo en notebooks de CrewAI).
4. Ejecutar el resto de las celdas en orden.

## Autora

Marcela de los Ángeles Yanes Pérez
Doctorado en Ciencias de la Computación — UJAT
ORCID: https://orcid.org/0000-0003-4282-4465
