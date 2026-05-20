```markdown
# Système RAG (Retrieval-Augmented Generation)

Ce projet implémente un pipeline complet de **RAG** (génération augmentée par récupération) : indexation de documents, recherche vectorielle et génération de réponse basée sur un contexte pertinent, le tout orchestré avec **LangChain** et une base vectorielle **ChromaDB**.

## ✨ Fonctionnalités

- Découpage intelligent des documents en chunks (taille fixe + chevauchement)
- Génération d’embeddings via un modèle adapté (`gte-large` de HuggingFace)
- Stockage persistant des vecteurs dans ChromaDB
- Recherche sémantique par similarité
- Génération de réponse par un LLM (via Open Router)
- Support de l’API Open Router (compatible OpenAI)

## 🛠️ Stack technique

- **Langchain** – orchestration du pipeline RAG
- **ChromaDB** – base de données vectorielle
- **Open Router API** – accès aux LLM (solution gratuite, remplace OpenAI)
- **PyPDF** – extraction de texte depuis PDF
- **python-dotenv** – gestion des variables d’environnement

## 📋 Prérequis

- Python 3.13
- `uv` (installeur rapide) ou `pip`
- Une clé API Open Router ([openrouter.ai](https://openrouter.ai/))

## 🔧 Installation

Clonez le dépôt et installez les dépendances avec `uv` :

```bash
git clone https://github.com/indexkboss/RAG_Fundamentales.git
cd RAG_Fundamentales
uv sync
```

> 💡 **Remarque** : l’utilisation de `uv` est recommandée pour une gestion plus rapide et fiable des dépendances.

## 🔑 Configuration

Créez un fichier `.env` à la racine avec votre clé API Open Router :

```env
OPEN_ROUTER_API_KEY=votre-clé-ici
```

> L’API Open Router est compatible avec le format OpenAI, vous pouvez donc utiliser `langchain-openai` en redirigeant la base URL.

## 📂 Structure du projet

```
RAG_Fundamentales/
├── pyproject.toml          # Dépendances officielles
├── RAGV2.ipynb             # Notebook principal contenant le pipeline
├── README.md               # Ce fichier
└── .env                    # Variables sensibles (ignoré par Git)
```

## 🚀 Utilisation

1. Lancez Jupyter :

```bash
uv run jupyter notebook RAGV2.ipynb
```

2. Suivez les étapes du notebook :
   - **Indexation** : chargez votre document (PDF, texte), découpez-le en chunks, générez les embeddings, stockez dans ChromaDB.
   - **Recherche** : entrez une question, elle est transformée en vecteur et comparée aux chunks.
   - **Génération** : le contexte récupéré + la question sont envoyés à l’API Open Router via LangChain pour obtenir une réponse.

## 🎛️ Personnalisation

- **Modèle d’embedding** : vous pouvez changer le modèle dans le notebook (actuellement `thenlper/gte-large`).
- **Taille des chunks** : ajustez `chunk_size` et `chunk_overlap` selon vos besoins.
- **Base vectorielle** : par défaut ChromaDB persiste les données localement.

## 📦 Dépendances principales (extrait de `pyproject.toml`)

```toml
dependencies = [
    "chromadb>=1.5.9",
    "ipykernel>=7.2.0",
    "langchain>=1.3.1",
    "langchain-community>=0.4.1",
    "langchain-openai>=1.2.1",   # utilisée avec Open Router
    "langchain-text-splitters>=1.1.2",
    "pypdf>=6.11.0",
    "python-dotenv>=1.2.2",
]
```

## 🤝 Contribution

Les suggestions et pull requests sont les bienvenues. Pour signaler un bug, ouvrez une **issue**.

---

Développé avec ❤️ pour le cours **RAG_fundamentals**.
```
