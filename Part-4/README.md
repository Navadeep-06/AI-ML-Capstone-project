# 🚀 Part 4 – LLM Powered Model Prediction Explanation (Track C)

## 📌 Objective

This project implements **Track C – Model Prediction Explanation Pipeline** from the Applied AI & ML Essentials Capstone.

The objective is to integrate the trained Machine Learning model from **Part 3** with a **Large Language Model (LLM)** using the **Groq API** to generate structured JSON explanations for predictions.

---

# 🧠 Workflow

✅ Load trained model (`best_model.pkl`)

⬇️

✅ Predict class & probability

⬇️

✅ Send prediction details to Groq LLM

⬇️

✅ Receive structured JSON response

⬇️

✅ Validate JSON schema

⬇️

✅ Apply PII Guardrails

⬇️

✅ Display final explanation

---

# 🤖 Machine Learning Model

**Algorithm:** Random Forest Classifier

Loaded using:

```python
import joblib

model = joblib.load("best_model.pkl")
```

---

# 🌐 LLM Provider

**Provider:** Groq API

**Model Used:** `llama-3.1-8b-instant` *(Replace with your actual model if different.)*

**Temperature:** `0`

### Why Temperature = 0?

Temperature 0 produces deterministic and consistent outputs, making it ideal for structured JSON generation and schema validation.

---

# 📝 System Prompt

```
You are an AI assistant that explains machine learning predictions.

Always return ONLY valid JSON.

The JSON must contain:

prediction_label
confidence_level
top_reason
second_reason
next_step

Do not include markdown.
Do not include extra text.
```

---

# 📥 User Prompt Template

```
Feature Values:
{feature_values}

Predicted Class:
{prediction}

Prediction Probability:
{probability}

Generate a structured JSON explanation.
```

---

# 📄 Expected JSON Schema

```json
{
  "type": "object",
  "properties": {
    "prediction_label": {
      "type": "string"
    },
    "confidence_level": {
      "type": "string"
    },
    "top_reason": {
      "type": "string"
    },
    "second_reason": {
      "type": "string"
    },
    "next_step": {
      "type": "string"
    }
  },
  "required": [
    "prediction_label",
    "confidence_level",
    "top_reason",
    "second_reason",
    "next_step"
  ]
}
```

---

# 🛡️ Guardrails

Before every API request, a regex-based validation checks for Personally Identifiable Information (PII).

Blocked Inputs:

- 📧 Email Addresses
- 📱 Phone Numbers

Example:

❌ Input

```
My email is example@gmail.com
```

Output

```
Input blocked: PII detected.
```

✅ Safe Input

```
Explain this prediction.
```

Output

```
LLM request executed successfully.
```

---

# 🌡️ Temperature Comparison

| Temperature | Result |
|------------|--------|
| **0** | ✅ Consistent and deterministic JSON |
| **0.7** | 🎲 More creative but inconsistent outputs |

Temperature **0** was selected because structured AI tasks require predictable responses.

---

# 📊 Demonstration Results

| Sample | Prediction | Probability | JSON Validation |
|---------|------------|-------------|-----------------|
| Sample 1 | High Price | 0.94 | ✅ PASS |
| Sample 2 | Low Price | 0.22 | ✅ PASS |
| Sample 3 | High Price | 0.87 | ✅ PASS |

---

# 📦 Libraries Used

- pandas
- numpy
- joblib
- requests
- json
- jsonschema
- re
- python-dotenv

---

# 🔐 Environment Variables

API keys are stored securely.

`.env`

```
GROQ_API_KEY=your_api_key_here
```

No API keys are hardcoded.

---

# 📁 Project Structure

```
Part-4/
│
├── app.ipynb
├── Guardrails.ipynb
├── README.md
├── requirements.txt
├── .env.example
├── .gitignore
└── best_model.pkl
```

---

# ✅ Features Implemented

✔️ Loaded trained ML model

✔️ Connected to Groq API

✔️ Generated structured JSON explanations

✔️ JSON Schema Validation

✔️ PII Guardrails

✔️ Environment Variable Support

✔️ Temperature Comparison

✔️ Three Prediction Demonstrations

---

# 🎯 Conclusion

This project successfully integrates a trained **Random Forest Classifier** with the **Groq LLM API** to generate structured explanations for predictions.

The pipeline ensures:

- ✅ Reliable ML predictions
- 🤖 LLM-powered explanations
- 📄 Valid JSON outputs
- 🛡️ PII protection
- 🔐 Secure API key management
- 🚀 Production-ready workflow

**Thank you! 😊**