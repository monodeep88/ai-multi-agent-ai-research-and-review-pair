# Research And Review Pair

    ## Project Overview

    Research And Review Pair is a complete full-stack AI project for **Multi-Agent AI** at **Beginner** difficulty. It includes a FastAPI backend, a React frontend, sample documents, vector search with ChromaDB support, source citations, timeline logs, structured run storage, Docker files, and tests.

    The system aims to facilitate collaboration between researchers and reviewers in the academic community.

    Difficulty controls project complexity, architecture depth, AI model selection, and how advanced the generated codebase is.

    - Architecture depth: minimal backend, simple folder structure, easy README, low-cost/free model
    - Selected architecture: Research Team Assistant
    - Template path: templates/multi-agent-ai/research-team-assistant
    - Generated stack: FastAPI backend, React UI, local vector fallback, simple tests
    - README style: beginner-friendly setup and clear expected output

    ## Tech Stack

    - Backend: Python, FastAPI, Pydantic, SQLAlchemy
    - AI/RAG: LangChain-ready prompt layer, ChromaDB vector storage, local deterministic fallback model
    - Workflow: Agent pipeline with planner, retrieval, tool, reasoning, and final answer steps
    - Frontend: React and Vite
    - Database: SQLite by default, PostgreSQL through Docker Compose
    - Testing: pytest
    - Difficulty: Beginner

    ## Generation Method

    This project was generated with a template-based architecture engine. AI is used only for the blueprint, domain customization, sample data, prompts, and documentation. The codebase is produced from tested FastAPI/React/Docker templates rather than raw LLM source output.

    ## Folder Structure

    ```text
    ai-multi-agent-ai-research-and-review-pair/
      backend/
        app/
          main.py
          config.py
          db.py
          schemas.py
          data/sample_docs/
          services/
            text.py
            vector_store.py
            llm.py
            tools.py
            pipeline.py
        tests/
          test_project_contract.py
        requirements.txt
        Dockerfile
      frontend/
        src/
          App.jsx
          main.jsx
          styles.css
        package.json
        Dockerfile
      docker-compose.yml
      .env.example
      README.md
    ```

    ## Environment Variables

    ```env
    OPENAI_API_KEY=
    OPENAI_MODEL=gpt-4o-mini
    DATABASE_URL=sqlite:///./app.db
    ALLOWED_ORIGINS=http://localhost:5173,http://localhost:3000
    VITE_API_URL=http://localhost:8000
    ```

    The app runs without an OpenAI key by using a deterministic local answer model. Add `OPENAI_API_KEY` to use LangChain with OpenAI.

    ## Installation

    ```bash
    cd backend
    python -m venv .venv
    .venv\Scripts\activate
    pip install -r requirements.txt
    ```

    ```bash
    cd ../frontend
    npm install
    ```

    ## Run Backend

    ```bash
    cd backend
    uvicorn app.main:app --reload --port 8000
    ```

    ## Run Frontend

    ```bash
    cd frontend
    npm run dev
    ```

    ## Run With Docker

    ```bash
    docker compose up --build
    ```

    ## Example API Request

    ```bash
    curl -X POST http://localhost:8000/api/ask ^
      -H "Content-Type: application/json" ^
      -d "{\"question\": \"What is the refund policy?\"}"
    ```

    ## Example User Question

    ```text
    What should I do if a customer asks for a refund without an order id?
    ```

    ## Expected Output

    The API returns:

    - `answer`: a grounded answer generated from retrieved context
    - `sources`: cited document chunks with similarity scores
    - `steps`: planner, retriever, reasoning, tool-call, and final-answer timeline logs
    - `project_type`: `Multi-Agent AI`

    ## How The RAG/Agent Flow Works

    Researcher agent -> analyst agent -> reviewer agent -> final synthesized answer.

    ## Project Planner Agent Workflow

    User -> React Dashboard -> FastAPI -> Project Planner Agent -> Specialist Agents -> Generated Project -> Auto Testing -> GitHub Repository Creation -> Push Code -> Return GitHub URL

    - **Architecture Agent**: Define app boundaries, data flow, runtime stack, and integration points. Outputs: Use a message broker (e.g., RabbitMQ) for inter-agent communication; Implement a knowledge graph using a graph database (e.g., Neo4j); Use a containerization platform (e.g., Docker) for deployment.
- **Backend Agent**: Design FastAPI modules, service contracts, validation, and error handling. Outputs: {'name': 'research_api', 'description': 'Provides APIs for research-related operations'}; {'name': 'review_api', 'description': 'Provides APIs for review-related operations'}; {'name': 'knowledge_graph_api', 'description': 'Provides APIs for knowledge graph-related operations'}.
- **Frontend Agent**: Design React screens, state flow, controls, and user feedback states. Outputs: {'name': 'research_portal', 'description': 'A web interface for researchers to manage projects and collaborate with reviewers'}; {'name': 'review_portal', 'description': 'A web interface for reviewers to manage reviews and provide feedback to researchers'}.
- **Database Agent**: Design persistence models, sample data, indexes, and audit records. Outputs: Run history; Source document metadata; Generated workflow audit records.
- **Testing Agent**: Define contract tests, smoke tests, and generated project validation. Outputs: Unit testing, integration testing, and end-to-end testing using a testing framework (e.g., Pytest).
- **DevOps Agent**: Define environment variables, Docker workflow, and repository packaging. Outputs: Docker-ready project; Environment sample file; GitHub repository upload.
- **Reviewer Agent**: Review the generated plan for completeness, security, and portfolio quality. Outputs: {'name': 'Research Initiation', 'description': 'Researcher initiates a new project and defines research goals'}; {'name': 'Reviewer Assignment', 'description': 'System assigns reviewers to the project based on expertise and availability'}; {'name': 'Review and Feedback', 'description': 'Reviewer provides feedback and ratings to the researcher'}.

    ## AI-Customized Domain Workflow

    - {'name': 'Research Initiation', 'description': 'Researcher initiates a new project and defines research goals'}
- {'name': 'Reviewer Assignment', 'description': 'System assigns reviewers to the project based on expertise and availability'}
- {'name': 'Review and Feedback', 'description': 'Reviewer provides feedback and ratings to the researcher'}

    ## Business Rules

    - {'name': 'Reviewer Expertise', 'description': 'Reviewer must have expertise in the research area to be assigned to the project'}
- {'name': 'Researcher Reputation', 'description': 'Researcher reputation affects the likelihood of being assigned to a project'}

    1. The backend loads sample documents from `backend/app/data/sample_docs`.
    2. Documents are split into chunks.
    3. Chunks are embedded and stored in ChromaDB when available, with a local fallback for development.
    4. User questions are matched against relevant chunks.
    5. Agent-specific steps run: planner, retriever, tool call, reasoning, reviewer, or graph nodes.
    6. The final answer is returned with source citations and a timeline.

    ## Testing

    ```bash
    cd backend
    pytest
    ```

    ## Validation Gates Before GitHub Push

    The SaaS validates generated projects before creating and pushing the GitHub repository:

    - `pytest`
    - `npm install`
    - `npm run build`
    - `docker compose config`
    - `docker compose build`
