# Pipelines de IA Generativa: RAG y Sistemas Multiagente (CrewAI)

Conjunto de notebooks ejecutables en Google Colab (GPU T4) que implementan
arquitecturas de Generación Aumentada por Recuperación (RAG) con LangChain
y sistemas multiagente con CrewAI, usando un modelo real de Hugging Face
(`sshleifer/tiny-gpt2`) como motor de generación.

## Notebooks

| Notebook | Tema | Stack |
|---|---|---|
| `01_crewai_multiagente_colab_t4.ipynb` | Pipeline secuencial de 2 agentes (Investigador → Redactor) | CrewAI, Transformers |
| `02_langchain_rag_soporte_colab_t4.ipynb` | RAG para soporte al cliente: embeddings propios, FAISS, recuperación + generación | LangChain, FAISS, Transformers |
| `03_langchain_rag_citas_colab_t4.ipynb` | RAG con trazabilidad de fuentes (citas tipo `[DOC-01]`) | LangChain, FAISS, Transformers |
| `04_crewai_analisis_producto_colab_t4.ipynb` | Pipeline de 3 agentes (Analista de producto → Especialista de riesgos → Coordinador) | CrewAI, Transformers |
| `05_crewai_revision_codigo_colab_t4.ipynb` | Revisión automatizada de código con 3 agentes (Bugs → Pruebas → Reporte) | CrewAI, Transformers |

## Detalles técnicos

- **Modelo base:** `sshleifer/tiny-gpt2` (carga real desde Hugging Face Hub, sin mocks).
- **LLM personalizado para CrewAI:** clase `HuggingFaceCrewLLM` que extiende `BaseLLM` para integrar un modelo local de Transformers como backend de los agentes.
- **Embeddings propios para RAG:** clase `TransformerEmbeddings` que extrae hidden states del modelo para generar vectores, indexados en FAISS.
- **Mitigación de alucinaciones:** la función `retrieval_based_answer` ancla la respuesta exclusivamente al contexto recuperado (patrón RAG estricto), evitando que el modelo genere contenido fuera de las fuentes indexadas.
- **Entorno:** Google Colab, GPU T4, instalación reproducible vía `pip` (versiones fijadas para `crewai`, `langchain`, `transformers`).

## Cómo ejecutar

1. Abrir cualquier notebook en Google Colab.
2. Ejecutar la celda de instalación (`%%capture`).
3. Reiniciar el entorno de ejecución si es la primera vez (celda indicada).
4. Ejecutar el resto de las celdas en orden.

## Autor

[Marcela de los Ángeles Yanes Pérez] — [(https://orcid.org/0000-0003-4282-4465)]
