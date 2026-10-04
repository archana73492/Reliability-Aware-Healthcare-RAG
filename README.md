# Reliability-Aware Healthcare RAG

## A Retrieval-Augmented Generation Framework for Reliable Healthcare Question Answering

### Project Overview

This project develops a Retrieval-Augmented Generation (RAG) system for healthcare question answering.

Large Language Models (LLMs) can generate fluent and useful answers, but they may also produce unsupported or inaccurate information, especially in healthcare. Retrieval-Augmented Generation addresses this problem by retrieving relevant information from a trusted knowledge base and providing that evidence to the language model before generating an answer.

The main goal of this project is to investigate how a healthcare RAG system can become more reliable by evaluating not only answer generation, but also retrieval quality, evidence grounding, citation correctness, and safe response behavior.

---

## Research Motivation

Healthcare question answering requires a high level of reliability because incorrect or unsupported information can potentially lead to harmful decisions.

Traditional LLM-based question answering may suffer from:

- Hallucination
- Outdated knowledge
- Unsupported claims
- Incorrect or misleading answers
- Lack of transparent evidence
- Incorrect source attribution

RAG can reduce some of these problems by grounding the language model in external evidence.

However, simply adding RAG does not guarantee that the generated answer is reliable.

Therefore, this project investigates a broader question:

> How can healthcare RAG systems be evaluated and improved to provide accurate, evidence-grounded, correctly supported, and safer answers?

---

## Research Problem

Existing healthcare RAG systems commonly evaluate individual aspects such as:

- Retrieval performance
- Answer accuracy
- Hallucination
- Faithfulness
- Citation quality

However, these aspects are not always evaluated together.

A system may retrieve relevant documents but generate an unsupported answer.

Similarly, a system may provide citations that do not actually support the generated claims.

Therefore, this project focuses on developing a **reliability-aware evaluation framework** for healthcare RAG.

---

## Research Gap

Based on the literature reviewed in this project, an important research gap is:

> Existing healthcare RAG systems often evaluate selected components such as retrieval quality, answer accuracy, hallucination, or citation quality independently. A practical framework that jointly evaluates retrieval quality, evidence grounding, citation correctness, answer correctness, and safe abstention is still needed.

This project aims to investigate this gap.

---

## Research Objectives

### Objective 1
Develop a Retrieval-Augmented Generation system for healthcare question answering.

### Objective 2
Evaluate the quality of retrieved healthcare evidence.

### Objective 3
Measure whether generated answers are grounded in the retrieved evidence.

### Objective 4
Evaluate whether citations or sources actually support the generated claims.

### Objective 5
Investigate safe response behavior when sufficient evidence is unavailable.

### Objective 6
Compare different retrieval configurations and identify configurations that improve answer reliability.

---

## Research Questions

### RQ1
How does retrieval configuration affect healthcare RAG performance?

### RQ2
Does better retrieval quality lead to better evidence-grounded answers?

### RQ3
To what extent are generated healthcare answers supported by retrieved evidence?

### RQ4
Do the sources provided by a healthcare RAG system correctly support its generated claims?

### RQ5
Can a healthcare RAG system safely abstain when sufficient evidence is unavailable?

---

# System Architecture

The current system follows the following pipeline:

Healthcare Knowledge Base  
↓  
Text Chunking  
↓  
Sentence Embeddings  
↓  
Semantic Retrieval  
↓  
Top-K Relevant Evidence  
↓  
Large Language Model  
↓  
Generated Healthcare Answer  
↓  
Reliability Evaluation

The planned reliability layer evaluates:

- Retrieval quality
- Answer correctness
- Evidence grounding
- Citation correctness
- Safety
- Abstention

---

## Current Architecture

```text
                  Healthcare Question
                          |
                          v
                  Query Embedding
                          |
                          v
                   Semantic Search
                          |
                          v
                   Top-K Evidence
                          |
                          v
                    FLAN-T5
                          |
                          v
                  Generated Answer
                          |
             +------------+------------+
             |            |            |
             v            v            v
         Grounding    Citation      Safety
         Evaluation   Evaluation   Evaluation
