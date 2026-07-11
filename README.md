# Building-Benchmark: A Comprehensive Benchmark Library for Building Information Modeling Methods

Building-Benchmark is an open-source library for researchers to conduct building information modeling, which covers **data generation** and **modeling**. 

## 📰 News
- **2025-06-28**: Building-Benchmark has been set up!

## ✨ Highlights
This repository provides a modular codebase to benchmark different models on various datasets in an easy way. Specifically, we feature on:

- **State-of-the-art Models**: Advanced methods proposed in recent years, including federated learning, decision-focused learning, etc.
- **Multi Datasets**: Various building information datasets from energy, health, and other domains.
- **Comprehensive Evaluation**: Both quantitative and qualitative methods for fidelity, usefulness, and accuracy.

## ⚙️ Installation
We recommend first creating a virtual environment and activating it. Then you can install the necessary libraries by running the following command.
```bash
Space left for code
```

##  🏰 Method zoo
This repository includes 25+ state-of-the-art building information modeling methods (and their variants). Our method zoo will be updated on a regular basis.

| 🤖 Name             | 🗂️ Model Type | Synthesis          |         | Class label        |
| --------------------- | ---------- | ------------------ |  ------------------ | ------------------ |
| Federated learning            |        | :white_check_mark: | :white_check_mark: | data-driven |
| Smart model-then-control              |      | :white_check_mark: |                   |  data-driven            |


##  📝 Datasets
This repository presents over 10 widely used building information datasets. Some of them come naturally with missing values and class labels, supporting to benchmark different kinds of models.


| 🤖Name        | 🧭 Resolution     | 📦 Dimension |⭕️ Missing value      | 🏷️ Class label |
| ----------- | -------------- | --------- | ------------------ | ----------- | 
| EnergyPlus     |    | N         | -                  | -           | 
|    |    | 2         | -                  | 2           | 

## 🔍Verification Methods
To comprehensively evaluate the effectiveness of the proposed methods, we conduct a standardized verification procedure across multiple building modeling datasets. The evaluation compares all candidate methods under consistent experimental settings and assesses their performance in terms of modeling accuracy, robustness, computational efficiency, and generalizability. Quantitative results are reported using predefined evaluation metrics, while qualitative examples are provided to illustrate the practical modeling performance of each method.

## 📊 Results
We compared all the above-mentioned methods in multiple datasets, 

Table I summarizes the numerical results on accuracies.

**Table I. Accuracy results of different methods on multiple datasets.**
| Method    |  Dataset 1   | Dataset 2 | Dataset 3     | Dataset 4 |
| ----------- | ---------- | --------- | ------------- | --------- | 
| method 1    |            | N         | -             | -         | 
| method 2   |             | 2         | -             | 2         | 
| method 3   |             | 2         | -             | 2         | 
| method 4   |             | 2         | -             | 2         | 

**Table II. Efficiency comparisons of different methods on multiple datasets.**
| Method    |  Dataset 1   | Dataset 2 | Dataset 3     | Dataset 4 |
| ----------- | ---------- | --------- | ------------- | --------- | 
| method 1    |            | N         | -             | -         | 
| method 2   |             | 2         | -             | 2         | 
| method 3   |             | 2         | -             | 2         | 
| method 4   |             | 2         | -             | 2         | 

**Table III. Operational cost of different methods on multiple datasets.**
| Method    |  Dataset 1   | Dataset 2 | Dataset 3     | Dataset 4 |
| ----------- | ---------- | --------- | ------------- | --------- | 
| method 1    |            | N         | -             | -         | 
| method 2   |             | 2         | -             | 2         | 
| method 3   |             | 2         | -             | 2         | 
| method 4   |             | 2         | -             | 2         | 

## 📎 Citation
If you enjoy or benefit from using `BEMS-sharing`, a citation to this repository will be greatly appreciated！
```BibTeX
@misc{Building-Benchmark,
  author = {Author Name},
  title = {Repository Title},
  year = {2024},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/Building-Energy-Modeling/Building-Benchmark}},
  note = {Accessed: 2026-06-27}
}
```
