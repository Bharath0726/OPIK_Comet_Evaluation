# OPIK_Comet_Evaluation

# 🚀 LLM Evaluation and Observability with Comet Opik

This repository demonstrates how to use **Comet Opik** for comprehensive LLM application evaluation, observability, and prompt management using a practical RAG (Retrieval-Augmented Generation) pipeline example.

## 📋 Table of Contents

- [What is Comet Opik?](#what-is-comet-opik)
- [Why Use This Notebook?](#why-use-this-notebook)
- [Key Features Demonstrated](#key-features-demonstrated)
- [Setup and Installation](#setup-and-installation)
- [Notebook Overview](#notebook-overview)
- [Evaluation Metrics](#evaluation-metrics)
- [Use Cases](#use-cases)
- [Getting Started](#getting-started)

## 🤖 What is Comet Opik?

**Comet Opik** is a comprehensive platform designed for **LLM application observability, evaluation, and prompt management**. It provides:

- **🔍 LLM Call Tracking**: Automatic logging of all LLM interactions with detailed metadata
- **📊 Evaluation Framework**: Built-in metrics for assessing LLM response quality
- **🎯 Prompt Versioning**: Track and manage different prompt versions and their performance
- **📈 Performance Analytics**: Detailed insights into model performance, costs, and latency
- **🔗 Framework Integration**: Seamless integration with popular frameworks like LlamaIndex, LangChain
- **💾 Dataset Management**: Create, manage, and version evaluation datasets

## 🎯 Why Use This Notebook?

This notebook serves as a **complete guide** for implementing production-ready LLM evaluation and monitoring. It's perfect for:

- **ML Engineers** building RAG applications
- **Data Scientists** evaluating LLM performance
- **Product Teams** monitoring LLM applications in production
- **Researchers** conducting LLM experiments and comparisons

## ✨ Key Features Demonstrated

### 1. **LLM Call Tracking & Observability**
```python
from opik.integrations.openai import track_openai
openai_client = track_openai(openai.OpenAI())
```
- Automatic logging of all OpenAI API calls
- Token usage and cost tracking
- Response time monitoring
- Error tracking and debugging

### 2. **RAG Pipeline Integration**
```python
from opik.integrations.llama_index import LlamaIndexCallbackHandler
Settings.callback_manager = CallbackManager([opik_callback_handler])
```
- Complete RAG pipeline observability
- Document retrieval tracking
- Context relevance monitoring
- End-to-end trace visualization

### 3. **Comprehensive Evaluation Metrics**
- **🎭 Hallucination Detection**: Identifies when models generate false information
- **🎯 Answer Relevance**: Measures how well answers address the questions
- **📍 Context Precision**: Evaluates retrieval quality
- **🔄 Context Recall**: Measures information completeness

### 4. **Dataset Management**
```python
dataset = client.get_or_create_dataset(name="Test dataset")
dataset.insert(qa_pairs)
```
- Version-controlled evaluation datasets
- Easy data ingestion and management
- Reproducible evaluation workflows

### 5. **Automated Evaluation Pipeline**
```python
evaluation = evaluate(
    dataset=dataset,
    task=evaluation_task,
    scoring_metrics=[hallucination_metric, answer_relevance_metric],
    experiment_config={"model": MODEL}
)
```

## 🛠 Setup and Installation

### Prerequisites
```bash
pip install opik llama-index llama-index-agent-openai llama-index-llms-openai
pip install openai pandas python-dotenv
```

### Environment Setup
Create a `.env` file with:
```env
OPENAI_API_KEY=your-openai-api-key-here
COMET_API_KEY=your-comet-api-key-here
```

### Comet Account Setup
1. Create a free account at [Comet.com](https://www.comet.com/signup?from=llm&=opik&utm_medium=colab&utm_content=llamaindex&utm_campaign=opik)
2. Get your API key from the dashboard
3. Configure Opik: `opik.configure(use_local=False)`

## 📖 Notebook Overview

### Section 1: Basic Setup & Configuration
- Environment setup and API key configuration
- Opik initialization and basic tracking

### Section 2: Simple LLM Tracking
- Basic OpenAI integration
- Function-level tracking with decorators
- Model availability checking

### Section 3: RAG Pipeline Implementation
- Document loading and indexing
- LlamaIndex integration with Opik
- Query engine setup with observability

### Section 4: Dataset Preparation
- Loading evaluation datasets
- Data formatting for Opik
- Dataset versioning and management

### Section 5: Comprehensive Evaluation
- Multi-metric evaluation setup
- Automated testing pipeline
- Results analysis and visualization

## 📊 Evaluation Metrics

| Metric | Purpose | What it Measures |
|--------|---------|------------------|
| **Hallucination** | Factual Accuracy | Detects generated false information |
| **Answer Relevance** | Quality Assessment | How well answers address questions |
| **Context Precision** | Retrieval Quality | Accuracy of retrieved context |
| **Context Recall** | Information Coverage | Completeness of retrieved information |

## 🎨 Use Cases

### 1. **Production Monitoring**
- Monitor LLM applications in real-time
- Track performance degradation
- Alert on unusual patterns or errors

### 2. **Model Comparison**
- A/B test different models
- Compare prompt versions
- Evaluate fine-tuned vs. base models

### 3. **Prompt Engineering**
- Version control for prompts
- Track prompt performance over time
- Optimize prompts based on metrics

### 4. **Quality Assurance**
- Automated testing for LLM applications
- Regression testing for model updates
- Continuous evaluation pipelines

### 5. **Research & Development**
- Experiment tracking for ML research
- Reproducible evaluation workflows
- Performance benchmarking

## 🚀 Getting Started

1. **Clone this repository**
   ```bash
   git clone <your-repo-url>
   cd <repo-name>
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env
   # Edit .env with your API keys
   ```

4. **Run the notebook**
   ```bash
   jupyter notebook Comet_opik.ipynb
   ```

5. **Explore the Opik Dashboard**
   - View traces and logs
   - Analyze evaluation results
   - Monitor performance metrics

## 🔧 Advanced Features

### Prompt Versioning
```python
@track(tags=["prompt_v1", "production"])
def my_llm_function(input_text):
    # Your LLM logic here
    pass
```

### Custom Metrics
```python
from opik.evaluation.metrics import BaseMetric

class CustomMetric(BaseMetric):
    def score(self, **kwargs):
        # Your custom scoring logic
        pass
```

### Batch Evaluation
```python
results = evaluate_batch(
    inputs=test_inputs,
    model_function=my_model,
    metrics=[custom_metric1, custom_metric2]
)
```

## 📈 Benefits

- **🎯 Improved Model Performance**: Systematic evaluation leads to better models
- **💰 Cost Optimization**: Track and optimize API usage and costs
- **🔒 Quality Assurance**: Automated testing prevents regressions
- **📊 Data-Driven Decisions**: Make informed choices based on metrics
- **🚀 Faster Development**: Streamlined evaluation workflows
- **🔍 Debug Capabilities**: Detailed traces help identify issues quickly

## 🤝 Contributing

Feel free to contribute by:
- Adding new evaluation metrics
- Improving documentation
- Sharing use cases and examples
- Reporting issues and bugs

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 📞 Support

- 📚 [Opik Documentation](https://www.comet.com/docs/opik/)
- 💬 [Community Discord](https://discord.gg/comet)
- 🐛 [Issue Tracker](https://github.com/comet-ml/opik/issues)

---

**Ready to elevate your LLM applications?** Start exploring the notebook and see the power of comprehensive LLM observability in action! 🚀 
