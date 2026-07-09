# Political Speech Framing with NLP

## Overview

This project analyzes how Italian political discourse differs across domestic and international institutional settings.

The analysis compares Italian parliamentary speeches and Italian speeches at the United Nations from 2006 to 2022, focusing on two policy domains:

- migration
- military and defense policy

The project combines supervised classification, topic modeling, translation, and summarization to study differences in political stance and thematic framing.

## Research Question

How does Italy frame migration and military-related issues differently in domestic parliamentary debate compared to international speeches at the United Nations?

## Data

The project uses three main sources:

- Italian parliamentary speeches from ItaParlCorpus
- Italian speeches at the United Nations General Debate
- Manifesto Project quasi-sentences for supervised fine-tuning

The parliamentary speeches are in Italian, while the UN speeches are in English. The analysis covers the period from 2006 to 2022.

## Methods

The project includes the following NLP tasks:

### 1. Data Preparation

The first notebook prepares the raw corpora for downstream NLP tasks.

It includes:

- data loading
- light text cleaning
- Italian sentence segmentation
- keyword-based filtering for migration and defense topics
- selection of top speeches by year and party-family group

### 2. BERT Classification

A multilingual BERT model is fine-tuned on selected Manifesto Project quasi-sentences.

The model predicts whether a sentence expresses a positive or negative stance toward migration or defense-related policy.

The fine-tuned model reaches approximately 0.81 macro-F1 on the development set.

### 3. LDA Topic Modeling

Latent Dirichlet Allocation is applied to identify the main themes in the selected speeches.

Separate LDA models are estimated for:

- migration-related parliamentary speeches
- military-related parliamentary speeches
- migration-related UN speeches
- military-related UN speeches

Topic coherence and diversity are used to guide the choice of the number of topics.

### 4. Translation

Italian parliamentary speeches are translated into English using OPUS-MT.

This allows the summarization task to operate on a single language.

### 5. Summarization

A hierarchical summarization pipeline is implemented using BART-large-CNN.

Summaries are produced at group level, where groups are defined by:

- source
- topic
- party family
- year

## Main Findings

The BERT classification results suggest that parliamentary speeches are more often classified as negative, while UN speeches are more often classified as positive.

This pattern is especially visible for migration-related discourse, where UN speeches tend to frame migration more through humanitarian and international-cooperation language, while parliamentary speeches include more domestic regulation, asylum, border, and political-contestation themes.

The LDA topic models help contextualize these differences by showing that domestic and international settings emphasize different thematic frames.

