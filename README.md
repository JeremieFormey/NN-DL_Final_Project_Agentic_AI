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
