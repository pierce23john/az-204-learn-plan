# az-204-learn-plan
ChatGPT Learning plan for AZ-204 focusing on hands on



📘 AZ-204 Hands-On Lesson Plan (Continuous Project Build)
🗓 Week 0 — Environment Setup + Base To-Do App
🎯 Goal

Create the foundation project you will extend throughout the following weeks.

📌 Activities

Create your Azure subscription.

Install tools: VS Code, .NET/Node/Python runtime, Azure CLI, Git.

Initialize a simple To-Do API using your preferred language.

Implement CRUD locally using in-memory storage or SQLite.

Push project to GitHub.

📦 Output
/todo-app-api
  /src
  /tests
  README.md

🗓 Week 1 — Azure Functions: Serverless API
🎯 Goal

Turn the existing To-Do API into a serverless backend.

📌 Activities

Create an Azure Function App (HTTP trigger).

Migrate Create / Read / Delete endpoints into Functions.

Keep business logic in a shared library for reuse in later weeks.

Deploy the Function App to Azure (via CLI or GitHub Actions).

Update README with deployed API URL.

📦 Output
/api/functions


Serverless To-Do API live in Azure.

🗓 Week 2 — Azure App Service + Blob Storage Integration
🎯 Goal

Add a frontend and enable file attachments using Blob Storage.

📌 Activities

Create a frontend (React/Angular/Plain HTML+JS).

Deploy to Azure App Service.

Create Blob Storage container: todo-attachments.

From the UI, allow uploading attachments linked to To-Do items.

API stores attachment URLs and returns them to the frontend.

📦 Output
/todo-app-ui
/storage/blob-attachments

🗓 Week 3 — Cosmos DB Integration
🎯 Goal

Replace local or in-memory storage with a scalable NoSQL store.

📌 Activities

Create a Cosmos DB for NoSQL database + container.

Update serverless API to persist:

To-Do items

Attachment URLs

Metadata (created, updated)

Implement partition key strategy (e.g., userId).

Test CRUD against Cosmos DB via SDK.

📦 Output
/database/cosmos


API fully persistent in Cosmos DB.

🗓 Week 4 — Security: Key Vault + Managed Identity + Authentication
🎯 Goal

Secure your application like a real production environment.

📌 Activities

Create Azure Key Vault.

Move all secrets (Cosmos keys, storage keys) into Key Vault.

Enable Managed Identity for:

Azure Functions

App Service

Remove sensitive values from app settings.

Add authentication to the frontend:

Azure Active Directory (Microsoft Entra ID)

Protect your API endpoints with auth tokens.

📦 Output

Zero secrets in code or config files

Authenticated UI and secure API

Managed Identity integrated

🗓 Week 5 — Azure Service Bus + Event-Driven Processing
🎯 Goal

Add asynchronous processing to your To-Do system.

📝 Example Scenario

To-Do Reminder System

📌 Activities

Create a Service Bus Queue.

API sends a message each time a user sets a reminder.

Add a Queue-triggered Function that:

Fetches To-Do from Cosmos DB

Sends email (via SendGrid or Logic Apps)

Updates reminder status

📦 Output
/functions/queue-processor
/messaging/service-bus


Event-driven architecture implemented.

🗓 Week 6 — Application Insights + Observability
🎯 Goal

Make the entire system observable and exam-ready.

📌 Activities

Add Application Insights to:

Function Apps

App Service frontend

Implement:

Custom logs

Custom metrics

Failure alerts

Performance review:

Cosmos throughput

Function cold-start mitigation

Final exam review + take practice test.

📦 Output

A fully production-style Azure app using:

Azure Functions

Azure App Service

Blob Storage

Cosmos DB

Key Vault

Managed Identity

Azure AD Authentication

Service Bus

Application Insights

🏗 Final Architecture Diagram (ASCII)
Frontend (App Service + AAD)
         |
         v
Serverless API (Azure Functions - HTTP Trigger)
         |
         +--> Cosmos DB (To-Do Data)
         |
         +--> Blob Storage (Attachments)
         |
         +--> Key Vault (via Managed Identity)
         |
         +--> SendReminder → Service Bus Queue
                    |
                    v
        Queue Processor Function
                    |
                    +--> Send Email via SendGrid/Logic App
                    |
                    +--> Update Cosmos DB
