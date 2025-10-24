# LibreChat Setup Guide

## Prerequisites

Before deploying LibreChat, ensure that the following prerequisites are met.

---

### 1. Configuration Files

You must create and populate the following configuration files:

#### `/vars/main.yml`

Contains key variables required for the deployment process, such as passwords, database URLs, and other environment-specific values.

**Example:**

```yaml
mongodb_password: mongo_pass
meili_master_key: master_key
openai_api_key: open_api_key
librechat_domain: librechat-domain.com
ragdb_password: pgvector_pass
```

---

#### `/templates/config/librechat.yaml`

Contains the main LibreChat configuration (backend and frontend settings).  
Fill out the file according to your environment.

Reference: `https://www.librechat.ai/docs/configuration/librechat_yaml`

---

#### `/templates/config/env`

Contains environment variables for the LibreChat container.  
Ensure this file includes all required environment variables for proper startup.

Reference: `https://www.librechat.ai/docs/configuration/dotenv`

---

### 2. MongoDB Setup

- MongoDB must be **available** and accessible from the LibreChat container.
- It must contain a **LibreChat** database.
- Create a `user` with the same credentials defined in your `main.yml` file. (you can use mongo-express)

---

### 3. Vector Database Setup

LibreChat requires a Vector Database (VectorDB) for semantic search and embeddings.

- VectorDB must be **available** and accessible.
- It must contain a `user "raguser"` with the corresponding password defined in `vars/main.yml`.
- The user must have `superuser` permissions or, at minimum, permissions to `create extensions`.

---

### 4. Deployment Notes

- Ensure all configuration files are mounted or copied to their correct locations inside the container.
- Environment variables defined in **env_file** are automatically loaded into the LibreChat container.
- Ensure MongoDB and VectorDB are ready before starting LibreChat.

---
