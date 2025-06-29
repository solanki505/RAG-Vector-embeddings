# 🧠 PDF Q&A System with LangChain, ChromaDB, and Sentence Transformers

This project allows you to load a PDF file, split it into manageable chunks, create embeddings using Sentence Transformers, store them in ChromaDB, and ask questions based on the content.

---

## 🛠️ Technologies Used

- Python 🐍
- `langchain`
- `langchain-chroma`
- `sentence-transformers`
- `chroma`
- `transformers==4.52.4`
- `formers==4.1.0`
- `torch==2.7.1`

---

## 📦 Installation

Clone the repository:

```bash
git clone https://github.com/solanki505/RAG-Vector-embeddings.git
cd RAG-Vector-embeddings
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Or manually:

```bash
pip install langchain langchain-chroma sentence-transformers chromadb transformers==4.52.4 torch==2.7.1 formers==4.1.0
```

---

## 📄 How It Works

### 1. **Import Libraries**

```python
from langchain_chroma import Chroma
from langchain_community.document_loaders import PyPDFLoader
from langchain_community.embeddings.sentence_transformer import SentenceTransformerEmbeddings
from langchain_text_splitters import RecursiveCharacterTextSplitter
```

### 2. **Load the PDF**

```python
loader = PyPDFLoader("paul-graham-ideas.pdf")
documents = loader.load()
```

### 3. **Split into Chunks**

```python
text_splitter = RecursiveCharacterTextSplitter(chunk_size=100, chunk_overlap=30)
docs = text_splitter.split_documents(documents)
```

### 4. **Create Embeddings**

```python
embedding_function = SentenceTransformerEmbeddings(model_name="all-MiniLM-L6-v2")
```

### 5. **Load into ChromaDB**

```python
db = Chroma.from_documents(docs, embedding_function)
```

### 6. **Ask a Question**

```python
query = "This essay is derived from where?"
docs = db.similarity_search(query)
print(docs[0].page_content)
```

---

## 🎯 Use Cases

- Query academic or research PDFs
- Build educational or legal Q&A bots
- Extract insights from any long document

---

## 📁 Project Structure

```
RAG-Vector-embeddings/
│
├── paul-graham-ideas.pdf
├── main.py
├── requirements.txt
└── README.md
```

---

## 🧠 License

This project is open-source under the MIT License.

---

## ✨ Author

Made with ❤️ by **[Solanki Sarkar](https://github.com/solanki505)**
