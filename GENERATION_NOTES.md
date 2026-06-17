# Generation Notes

            Mode: ai

            Model: groq / llama-3.1-8b-instant

            Fallback reason: OpenAI limit reached. Automatically switched to Groq.

            Architecture: Research Team Assistant

            Template path: templates/multi-agent-ai/research-team-assistant

            Short description:

            A multi-agent AI system for research and review collaboration

            Architecture notes:

            - Use a message broker (e.g., RabbitMQ) for inter-agent communication
- Implement a knowledge graph using a graph database (e.g., Neo4j)
- Use a containerization platform (e.g., Docker) for deployment

            Project planner agent workflow:

            - Architecture Agent: Define app boundaries, data flow, runtime stack, and integration points. Outputs: Use a message broker (e.g., RabbitMQ) for inter-agent communication; Implement a knowledge graph using a graph database (e.g., Neo4j); Use a containerization platform (e.g., Docker) for deployment
- Backend Agent: Design FastAPI modules, service contracts, validation, and error handling. Outputs: {'name': 'research_api', 'description': 'Provides APIs for research-related operations'}; {'name': 'review_api', 'description': 'Provides APIs for review-related operations'}; {'name': 'knowledge_graph_api', 'description': 'Provides APIs for knowledge graph-related operations'}
- Frontend Agent: Design React screens, state flow, controls, and user feedback states. Outputs: {'name': 'research_portal', 'description': 'A web interface for researchers to manage projects and collaborate with reviewers'}; {'name': 'review_portal', 'description': 'A web interface for reviewers to manage reviews and provide feedback to researchers'}
- Database Agent: Design persistence models, sample data, indexes, and audit records. Outputs: Run history; Source document metadata; Generated workflow audit records
- Testing Agent: Define contract tests, smoke tests, and generated project validation. Outputs: Unit testing, integration testing, and end-to-end testing using a testing framework (e.g., Pytest)
- DevOps Agent: Define environment variables, Docker workflow, and repository packaging. Outputs: Docker-ready project; Environment sample file; GitHub repository upload
- Reviewer Agent: Review the generated plan for completeness, security, and portfolio quality. Outputs: {'name': 'Research Initiation', 'description': 'Researcher initiates a new project and defines research goals'}; {'name': 'Reviewer Assignment', 'description': 'System assigns reviewers to the project based on expertise and availability'}; {'name': 'Review and Feedback', 'description': 'Reviewer provides feedback and ratings to the researcher'}
