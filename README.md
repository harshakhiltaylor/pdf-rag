#  PDF-RAG — AI-Powered Document Q&A Platform

An intelligent document retrieval and question-answering platform built with **Retrieval-Augmented Generation (RAG)**. Upload any PDF, ask questions in natural language, and get contextually accurate answers powered by OpenAI embeddings and LangChain — all behind a secure, authenticated interface.

---

## ✨ Features

- **PDF Upload & Ingestion** — Upload PDF documents that are parsed, chunked, and embedded for semantic search
- **RAG-Powered Q&A** — Ask natural language questions and get accurate, context-grounded answers sourced from your documents
- **OpenAI Embeddings via LangChain** — Documents are vectorized using OpenAI's embedding models, enabling high-quality semantic retrieval
- **User Authentication** — Secure sign-up/login and session management powered by [Clerk](https://clerk.dev)
- **Dockerized Setup** — Spin up the full stack (client + server) with a single `docker-compose` command

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Next.js, TypeScript, CSS |
| Backend | Node.js, Express |
| AI / RAG | LangChain, OpenAI API |
| Auth | Clerk |
| Containerization | Docker, Docker Compose |

---

## 📁 Project Structure

```
pdf-rag/
├── client/             # Next.js frontend application
├── server/             # Node.js backend API + RAG logic
└── docker-compose.yml  # Orchestrates client and server containers
```

---

##  Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) v18+
- [Docker](https://www.docker.com/) & Docker Compose
- An [OpenAI API key](https://platform.openai.com/api-keys)
- A [Clerk](https://clerk.dev) account (for auth keys)

---

### Option 1 — Docker (Recommended)

```bash
# 1. Clone the repository
git clone https://github.com/harshakhiltaylor/pdf-rag.git
cd pdf-rag

# 2. Set up environment variables (see below)

# 3. Start the full stack
docker-compose up --build
```

The client will be available at `http://localhost:3000` and the server at `http://localhost:5000` (or as configured).

---

### Option 2 — Local Development

**Server**

```bash
cd server
npm install
npm run dev
```

**Client**

```bash
cd client
npm install
npm run dev
```

---

## Environment Variables

### Server (`server/.env`)

```env
OPENAI_API_KEY=your_openai_api_key
PORT=5000
```

### Client (`client/.env.local`)

```env
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
CLERK_SECRET_KEY=your_clerk_secret_key
NEXT_PUBLIC_API_URL=http://localhost:5000
```

> Never commit `.env` files to version control.

---

## How It Works

```
User uploads PDF
      │
      ▼
Text Extraction & Chunking
      │
      ▼
OpenAI Embeddings (via LangChain)
      │
      ▼
Stored in Vector Store
      │
      ▼
User asks a question
      │
      ▼
Semantic similarity search → retrieve relevant chunks
      │
      ▼
LLM generates answer grounded in retrieved context
      │
      ▼
Answer returned to user
```

---

## Authentication

Authentication is handled by **Clerk**, providing:

- Email/password and social OAuth sign-in
- Secure session management
- Per-user document isolation

---

## Scripts

### Server

| Command | Description |
|---|---|
| `npm run dev` | Start development server |
| `npm run build` | Build for production |
| `npm start` | Run production build |

### Client

| Command | Description |
|---|---|
| `npm run dev` | Start Next.js dev server |
| `npm run build` | Build for production |
| `npm start` | Run production build |

---

## Contributing

Contributions are welcome! Please open an issue or submit a pull request.

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m 'Add your feature'`
4. Push to the branch: `git push origin feature/your-feature`
5. Open a Pull Request

---

## License

This project is open source. See [LICENSE](LICENSE) for details.

---

## Author

**Harsh Akhil taylor**
[GitHub](https://github.com/harshakhiltaylor)
