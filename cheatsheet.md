# Google Vertex AI - Agent Builder

Course: HEIG-VD CLD 2024/25

Authors: Leonard Cseres, Edison Sahitaj, David Schildbock, Tristan Gerber

Date: June 9, 2025

## What is Agent Builder

Vertex AI Agent Builder is a managed service on Google Cloud that allows to create and manage conversational agents (like a chatbot or virtual assistant). It offers a no-code and code-first to design prompt-based agents and connect to external API.

**Problems solved using this tool** :

- Automatically answers frequently asked questions 24/7 to reduce human workload
- Interprets and summarises internal documents for complex access to information
- Customised tools to link the agent to databases for difficult integration

## Use cases

- Customer support using chatbot
- Analysis of documents
- Product recommendations
- R&D support

## Pricing

| Component | Description |
|-----------|-------------|
| Token processed | Price per 1000 input and output tokens |
| Used model | The cost varies depending on the model (e.g. Gemini 2.5 Pro) |
| Agent Engine | CPU/memory billing for customised use |

### Scenario

If we had a team of 5 people using gemini 2.5 pro. Each person would do an average of 50 prompts per day for 20 days :

**Prompt/month** : 5 * 50 * 20 = 5000 prompts

**Total tokens** : 5000 * 1500 = 7m5 tokens

**Cost of tokens** :
- input : 2m5 * 0.00125 = $3.13
- output : 5m * 0.01 = $50

**Total** : $53.13/month

## Advantages and disadvantages

### Pros

- Unified platform - Vertex AI brings data prep, feature store, AutoML, custom training, pipelines, deployment, and monitoring into one unified console—streamlining workflows under a single UI/API.
- Scalability - It scales effortlessly from small experiments to enterprise-grade workloads, with support for distributed training, GPUs/TPUs, and managed services.
- For beginners: AutoML - With its no-code AutoML tools for vision, text, video, and tabular data, beginners can train production-grade models with minimal coding.
- For experts: Custom Training - Experts get full control via custom training jobs—using TensorFlow, PyTorch, XGBoost, custom containers, pipelines, and hyperparameter tuning.

### Cons

- Vendor lock-In (Google Cloud) - Deep reliance on GCP services like BigQuery, Cloud Storage, and Pipelines makes migrating to other clouds overly complex and costly.
- Hard to predict cost - Pricing involves multiple dimensions—training, endpoints, storage, AutoML—leading to billing surprises even for small or educational use.
- Limited open source community - Despite supporting frameworks like TensorFlow and PyTorch, the platform has limited OSS ecosystem and documentation, especially around advanced features and custom containers.
- Steep learning curve - Beginners and even seasoned ML teams face a steep climb mastering the platform—custom jobs, pipelines, containers, workbench—and documentation is often fragmented or outdated.

## Alternatives

| Platform                             | Lock‑In | Easy to Use      | MLOps Features                | AutoML | GenAI Ready       |
|--------------------------------------|:-------:|:----------------:|:-----------------------------:|:------:|:-----------------:|
| **Google Vertex AI Agent Builder** (ours)   | High    | ☑☑☑     | ☑☑☑☑  | ☑☑☑☑ | ☑☑☑☑ |
| **AWS Bedrock Agents**               | High    | ☒☒      | ☑☑☑☑☑ | ☑☑☑  | ☑☑  |
| **Azure AI Agents**                  | High    | ☑☑     | ☑☑☑☑  | ☑☑☑☑  | ☑☑☑  |
| **OpenAI Responses API + Agents SDK**| Medium  | ☑☑☑☑  | ☑☑☑☑  | –  | ☑☑☑☑ |

## How to get started

### Prerequisites

- GCP account
- Activation of Vertex AI and Agent Builder
- Billing or free tier activated

### Starting stage

1. First, you need to go to the GitHub repo which contains some agents developped by Google at [this link](https://github.com/google/adk-samples/tree/main)
2. Now select an agent you find interesting
3. You need to login to your GCP account

```bash
gcloud auth login
```

4. Now you can enable some APIs

```bash
gcloud services enable aiplatform.googleapis.com
```

5. Clone the repository and go to this folder

```bash
git clone https://github.com/google/adk-samples.git
cd adk-samples/python/agents/customer-service
```

6. Install Poetry if u dont have it

```bash
pip install poetry
```

7. Install dependencies using Poetry and activate the virtual env

```bash
poetry install
poetry env activate
```

8. Rename the ``.env_example`` to ``.env`` and fill the file with these values
```bash
GOOGLE_CLOUD_PROJECT=YOUR_PROJECT_ID
GOOGLE_GENAI_USE_VERTEXAI=1
GOOGLE_CLOUD_LOCATION=us-central1
```

9. Finally run the agent and the web server

```bash
adk run customer_service
adk web
```
