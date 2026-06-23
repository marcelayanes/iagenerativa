# Pipelines de IA Generativa — LangChain y CrewAI

Colección de notebooks ejecutados en Google Colab (GPU T4) que implementan
pipelines de IA sin necesidad de API keys externas.

## Notebooks

| # | Notebook | Framework | Descripción |
|---|----------|-----------|-------------|
| 01 | `01_crewai_multiagente_colab_t4.ipynb` | CrewAI | Pipeline multiagente: Investigador + Redactor coordinados |
| 02 | `02_langchain_rag_soporte_colab_t4.ipynb` | LangChain + RAG | RAG para soporte al cliente con FAISS y embeddings reales |
| 03 | `03_langchain_rag_citas_colab_t4.ipynb` | LangChain + RAG | RAG con citas de fuentes (DOC-01, DOC-02...) |
| 04 | `04_crewai_analisis_producto_colab_t4.ipynb` | CrewAI | 3 agentes: Analista, Riesgos, Coordinador ejecutivo |
| 05 | `05_crewai_revision_codigo_colab_t4.ipynb` | CrewAI | Revisión de código con agentes especializados |

## Stack técnico
- **CrewAI** — orquestación de agentes con roles, tareas y flujo secuencial
- **LangChain** — cadenas RAG con retriever, vectorstore y prompt templates
- **FAISS** — indexación y búsqueda por similitud semántica
- **Hugging Face Transformers** — modelos locales sin API keys
- **Google Colab T4** — entorno de ejecución reproducible
