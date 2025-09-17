# Neural Network and Deep Learning Course : Final Project

This notebook presents a project combining **Agentic AI** and **Retrieval-Augmented Generation (RAG)** to simulate a realistic, collaborative workflow involving the creation of a visual dashboard based on used car sales data.


The objective is to produce an interpreted visual report using:
- A client request document (`customer_needs.txt`)
- A structured dataset (`used_car_sales.csv`)

Three specialized AI agents collaborate in this simulation:
- **Project Manager**: understands client needs using RAG
- **Data Analyst**: explores and analyzes the CSV data
- **Developer**: generates code to visualize relevant insights

Dataset : https://www.kaggle.com/datasets/sandeep1080/used-car-sales/data

Source : Kaggle
## Introduction

This project simulates a realistic, collaborative workflow using **multiple AI agents** using **LangChain** and **Retrieval-Augmented Generation (RAG)**. 

The purpose of the project is to implement very inovative technologies : RAG and especially the Agentic AI, in a real life use-case and to make the most of their potential.

Unlike standard single-model systems, we design a **multi-role agent environment** to replicate how human teams tackle business data challenges. Each agent plays a unique role:
- The **Project Manager** extracts goals from a real business request (via RAG)
- The **Data Analyst** investigates the dataset and extracts insights
- The **Developer** produces dynamic visualizations tailored to the insights

This approach combines **modularity**, **contextual reasoning**, and **dynamic data retrieval**, offering a novel way to automate structured team workflows.

The goal: generate a report, answering the users query, about real-world used car sales data — with full autonomy and agent-to-agent coordination.

### Technologies Used

Definitions : 
* **LangChain Agents** are AI-powered decision-makers that can reason step by step and interact with tools (like Python functions or search engines) to complete complex tasks. Each agent in this project has a specific role (e.g. Project Manager, Analyst, Reporter) and uses a combination of prompts and tools to process data, execute code, and generate business insights.
They are **autonomous, adaptative and goal oriented**.

* **RAG (Retrieval-Augmented Generation)** combines a language model with a document retriever. Instead of relying only on the model's internal knowledge, RAG allows the agent to search through external documents (like our customer_needs.txt) and use that context to generate more accurate and relevant outputs. In our case, the PM Agent uses RAG to align its task planning with the business requirements stored in this file.

  ### Dataset Description

The dataset `used_car_sales.csv` contains detailed records of used car transactions across various dealerships and locations. It includes:

- Car characteristics: type, brand, color, gearbox, etc.
- Transaction data: purchase and sale dates, prices, margins
- Agent performance: names, ratings, commissions, feedback
- Customer behavior: sale status, feedback quality

With 25 columns and a diverse mix of categorical and numerical features, this dataset is highly suitable for simulating business intelligence tasks. And very easy to use.

It allows agents to perform meaningful analysis such as:
- Tracking performance by car type or sales agent
- Identifying high-margin deals
- Exploring relationships between color, feedback, and success -> We could perform machine learning task, we won't because we focus on agents but the combination of both would be very interesting

Developing this multi-agent system to autonomously analyze a dataset and generate business reports presented several interesting challenges, both technical and conceptual.

### Challenges and Limitations
One of the key difficulties was ensuring that each agent, especially the Project Manager, Analyst, and Reporter, operated cohesively despite relying on independent LLM calls. Prompt design played a central role here: while we aimed for flexibility and generality, overly broad prompts sometimes caused the agents to hallucinate or produce generic, ungrounded outputs. For example, the Reporter occasionally invented insights (e.g., listing "Car A" or "Agent X", or create names like Bob and Charlie in the first example) when the Analyst had failed to extract concrete results from the dataset.

A related issue was column name mismatches. Because the Project Manager and Analyst agents rely on inferred column semantics from user queries and sample rows, discrepancies between expected and actual column names (e.g., "selling_price" vs "Price") led to failed tasks or skipped analysis. Initially, these were not well handled, resulting in empty or misleading reports. That why we fixed them (in the first cells of the notebook)

How We Addressed Them ?


To combat hallucination and inconsistency, we refined the prompts significantly:

The PM Agent was instructed to only generate tasks feasible given the actual structure of the dataset.

The Analyst Agent was guided to clearly print and label results, and to skip tasks when required columns were missing — explicitly mentioning the cause.

The Reporter Agent was constrained to only summarize what was actually computed, and never to fabricate content when results were unavailable.



### Areas for Improvement
This project underscored the importance of robust **prompt engineering** when orchestrating LLMs in structured workflows. It also highlighted the fragility of such systems when relying on implicit assumptions about data. In the future, we could improve reliability by:

Automatically detecting and normalizing column names via fuzzy matching.

Introducing feedback loops: e.g., if the Reporter detects a lack of results, it could signal the PM or Analyst to retry or adjust.

Adding memory or a session context, so that agents can refer to prior steps more consistently.

Lastly, while the pipeline performs well on well-structured datasets, it remains sensitive to noisy or incomplete data. Enhancing its ability to adapt to varying schema — potentially via schema reasoning or few-shot column description — would be a valuable next step.
