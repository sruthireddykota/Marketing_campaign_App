#  AI Marketing Tool

An AI-powered Streamlit application that generates age-targeted marketing content — including sales copies, tweets, and product descriptions — using Azure OpenAI and LangChain's Few-Shot Prompting.

---

## Overview

This tool takes a user-provided text input and generates tailored marketing content based on the selected task type and target age group. It leverages few-shot prompting to ensure the tone and language match the intended audience — whether a Kid, Adult, or Senior Citizen.

---

## Features

-  Generates sales copies, tweets, and product descriptions
-  Age-targeted responses (Kid, Adult, Senior Citizen)
-  Few-shot prompting for context-aware, audience-specific output
-  Adjustable word limit via slider
-  Powered by Azure OpenAI with dynamic temperature control

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Streamlit |
| LLM | Azure OpenAI (Chat model) |
| Prompting | LangChain Few-Shot Prompt Template |
| Example Selection | LangChain Length-Based Example Selector |
| Orchestration | LangChain Core |

---

## Project Structure
```
├── app.py              # Main Streamlit app with LLM logic and UI
├── requirements.txt    # Python dependencies
└── README.md
```

---

## Prerequisites

- Python 3.9+
- An [Azure OpenAI](https://azure.microsoft.com/en-us/products/ai-services/openai-service) account with a chat model deployment (e.g., `gpt-4o` or `gpt-35-turbo`)

---

## Installation

**1. Clone the repository**
```bash
git clone <your-repo-url>
cd <repo-folder>
```

**2. Install dependencies**
```bash
pip install -r requirements.txt
```

**3. Configure secrets**

Create a `.streamlit/secrets.toml` file in the project root:
```toml
AZURE_OPENAI_ENDPOINT   = "https://your-resource.openai.azure.com/"
AZURE_OPENAI_API_KEY    = "your-azure-openai-api-key"
AZURE_OPENAI_DEPLOYMENT = "your-chat-deployment-name"
```

---

## Usage

**1. Run the app**
```bash
streamlit run app.py
```

**2. In the browser UI:**
- Enter your **text or topic** in the text area
- Select the **task type** (Sales Copy, Tweet, or Product Description)
- Select the **target age group** (Kid, Adult, or Senior Citizen)
- Adjust the **word limit** using the slider
- Click **"Generate"**

**3. Results:** The app displays AI-generated marketing content tailored to your selected audience and task.

---

## How It Works
```
User Input (Text + Task Type + Age Group + Word Limit)
            ↓
  Age Group → Few-Shot Examples Selected
            ↓
  LengthBasedExampleSelector → Filters Examples by Token Limit
            ↓
  FewShotPromptTemplate → Builds Final Prompt
            ↓
  Azure OpenAI → Generates Response
            ↓
    Display in Streamlit UI
```

1. The user provides a topic, selects a task type and age group.
2. Based on the age group, a curated set of few-shot examples is loaded.
3. `LengthBasedExampleSelector` dynamically selects examples within the token limit.
4. A `FewShotPromptTemplate` constructs the final prompt with prefix, examples, and suffix.
5. Azure OpenAI generates a tailored response which is displayed in the UI.

---

## Age Group Behavior

| Age Group | Tone & Style |
|---|---|
| Kid | Playful, imaginative, simple language with fun analogies |
| Adult | Informative, professional, balanced and thoughtful |
| Senior Citizen | Warm, nostalgic, respectful and relatable |

---
End of Documentation
---
