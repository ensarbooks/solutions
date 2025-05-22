## 🔧 Functional Requirements

### 1. **SQL Generation from Natural Language**

- Convert user-provided natural language queries into SQL statements.
- Utilize a LangChain pipeline with an LLM (e.g., `deepseek-r1`, `llama3`, or `mistral`) to generate SQL.

### 2. **Schema Introspection**

- Dynamically extract table names and column metadata from a connected MySQL database.
- Use this schema to guide the LLM in SQL generation.

### 3. **SQL Execution**

- Accept raw SQL queries via API and execute them on the connected MySQL database.
- Return query results in JSON format.

### 4. **REST API Endpoints**

- `POST /generate-sql`: Accepts natural language query, returns generated SQL.
- `POST /run-sql`: Accepts SQL query string, executes it, and returns the result.

### 5. **CORS Configuration**

- Allow cross-origin requests (e.g., for frontend integration) with full method and header access.

---

## 🛠️ Technical Requirements

### 1. **Database Configuration**

- Support for MySQL with configurable credentials and connection URL.
- ORM interface powered by SQLAlchemy.

### 2. **Language Model Integration**

- Integration with LangChain’s `ChatPromptTemplate`.
- Use of Ollama-hosted LLM for SQL generation.

### 3. **Prompt Engineering**

- Prompt template enforces structured LLM output: SQL only, no additional explanation.

### 4. **Security & Validation**

- Basic exception handling for invalid SQL or schema errors.
- Potential enhancement: Add SQL injection detection or execution guardrails.

---

## 🚀 Deployment & Environment Requirements

### 1. **Runtime Environment**

- Requires Python environment with `FastAPI`, `SQLAlchemy`, `LangChain`, `Ollama`, and `pymysql` packages.

### 2. **Ollama Model Hosting**

- Assumes the LLM model is available and properly loaded via Ollama server.

### 3. **MySQL Server**

- Requires a running MySQL instance with schema pre-configured (e.g., `sales` DB).

---

## 📈 Future Enhancements (Optional/Stretch Goals)

- **User Authentication**: Protect endpoints from unauthorized access.
- **Rate Limiting**: Prevent abuse of the LLM and SQL execution endpoints.
- **Frontend Dashboard**: UI for entering queries, viewing SQL, and exploring results.
- **Natural Language → Visual Query Builder**: Optional graphical query interface.
- **SQL Output Validation**: Check SQL safety before execution (e.g., prevent `DROP`, `TRUNCATE`).
