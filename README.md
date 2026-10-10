# Anti-Money Laundering Detection Using Social Network Analysis

**STAT 280 – Practical Machine Learning | Academic Group Project**

University of the Philippines Diliman

## 1. Project Overview

Money laundering is a significant challenge for financial institutions because suspicious financial activities may involve multiple accounts, interconnected transactions, and complex fund-transfer patterns.

Traditional transaction-level analysis may overlook relationships between accounts that become apparent when financial transactions are examined as a network.

This project applies **Social Network Analysis (SNA)** to simulated financial transaction data to identify laundering-involved accounts, examine their transaction relationships, and detect communities that may warrant further investigation.

Using Python and network analysis techniques, the project demonstrates how financial transaction networks can support anti-money laundering (AML) monitoring and risk-based investigation.

## 2. Business Problem

Financial institutions process large volumes of transactions, making it challenging to identify suspicious activities and interconnected accounts.

Analyzing transactions individually may fail to capture network-level patterns, such as accounts transferring funds through multiple intermediaries or groups of accounts repeatedly interacting with one another.

**Central Business Question:**

How can Social Network Analysis help identify laundering-related accounts, uncover suspicious transaction communities, and prioritize accounts for further investigation?

**Potential Stakeholders:**
- Financial institutions and banks
- AML compliance officers
- Financial crime investigation teams
- Financial regulators

## 3. Project Objectives

**Objective 1: Identify laundering-involved accounts and their immediate neighborhoods.**

Identify accounts associated with laundering-labeled transactions and examine their direct transaction relationships to understand their connections within the financial network.

**Objective 2: Detect laundering-related communities and prioritize high-risk accounts.**

Identify groups of interconnected accounts, examine their concentration of laundering-related activity, and rank accounts that may warrant further investigation.

## 4. Dataset

**Dataset:** IBM Transactions for Anti-Money Laundering

**Source:** Kaggle

**Dataset Link:** https://www.kaggle.com/datasets/ealtman2019/ibm-transactions-for-anti-money-laundering-aml

The dataset contains simulated financial transactions designed for research on anti-money laundering detection.

Relevant information includes:

- Sender and receiver account identifiers
- Transaction amounts
- Transaction timestamps
- Transaction currencies
- Laundering-related transaction labels

The dataset provides an opportunity to model financial transactions as a network and examine how accounts are interconnected.

**Data Privacy Note:** The dataset contains synthetic transactions rather than actual customer financial records.

## 5. Methodology

The analysis was implemented in Python using Google Colab.

### Step 1: Data Preparation

- Import and inspect the transaction dataset.
- Identify transactions labeled as laundering-related.
- Extract accounts involved in laundering-labeled transactions.
- Identify directly connected counterparties.
- Prepare the edge list for network construction.

### Step 2: Network Construction

Financial transactions are represented as a directed graph:

- **Nodes:** Financial accounts
- **Edges:** Directed financial transaction relationships
- **Direction:** Movement of funds from sender to receiver

A laundering-centered subgraph is constructed to focus the analysis on laundering-involved accounts and their immediate transaction neighborhoods.

### Step 3: Network Characterization

The network is examined using:

- Number of nodes and edges
- Degree distribution
- Network density
- Weakly connected components
- Strongly connected components

These measures describe the network's size, connectivity, concentration, and overall structure.

### Step 4: Centrality Analysis

Network centrality measures are used to examine the structural importance of accounts.

These include:

- **Degree Centrality:** Measures the number of direct connections associated with an account.
- **PageRank:** Identifies accounts that may be structurally important based on their connections to other accounts.
- **Betweenness Centrality:** Identifies accounts that may serve as bridges between different parts of the network.

### Step 5: Community Detection

Community detection techniques are applied to identify groups of interconnected accounts.

The analysis examines:

- Community size
- Number of laundering-involved accounts
- Proportion of laundering-involved accounts
- Number of laundering-labeled transaction relationships
- Connections between accounts within selected communities

These indicators help characterize communities for further investigation.

### Step 6: Visualization and Interpretation

Network visualizations are generated to examine:

- Account relationships
- Laundering-involved accounts
- Highly connected accounts
- Community structures
- Potentially important transaction pathways

The findings are interpreted in terms of their possible relevance to AML investigation.

## 6. Key Findings

### Finding 1: The laundering-centered network is highly sparse.

The analyzed subgraph contains:

| Network Metric | Result |
|---|---:|
| Number of accounts (nodes) | 64,067 |
| Transaction relationships (edges) | 82,238 |
| Network density | Approximately 0.000020 |
| Weakly connected components | 147 |
| Strongly connected components | 63,269 |

The low network density indicates that only a very small proportion of all possible account-to-account relationships exists in the analyzed network.

### Finding 2: Most accounts belong to one large weakly connected component.

The largest weakly connected component contains approximately **62,459 accounts, representing 97.5% of the analyzed network**.

This indicates that most accounts are connected through transaction relationships when transaction direction is ignored.

However, the large number of strongly connected components suggests that mutual reachability through directed transaction paths is limited.

### Finding 3: A small number of accounts have exceptionally high outgoing connectivity.

Two accounts were observed to have 14,230 and 8,846 outgoing transaction relationships, respectively.

Together, these account-level outgoing connection counts represent approximately 28% of the network's recorded edges.

This indicates that a relatively small number of accounts have disproportionately large numbers of outgoing connections.

Such accounts may be useful starting points for examining transaction distribution patterns.

However, high connectivity alone does not establish suspicious or criminal activity.

### Finding 4: Community analysis provides additional context for investigation.

Community detection allows interconnected accounts to be examined as groups rather than only as individual accounts.

By comparing community size, laundering-related account concentration, and laundering-labeled transaction relationships, investigators can identify communities that may warrant closer examination.

These network characteristics provide complementary information for prioritizing further investigation.

## 7. Business Implications

The project demonstrates several potential applications of Social Network Analysis in financial crime investigation.

| Analytical Output | Potential Business Application |
|---|---|
| Identification of laundering-related accounts | Establish an initial investigation population |
| Account connectivity analysis | Identify highly connected accounts |
| Centrality measures | Prioritize structurally important accounts |
| Community detection | Examine groups of interconnected accounts |
| Network visualization | Support interpretation of transaction relationships |

Network-based analysis can complement transaction-level monitoring by helping investigators understand relationships among accounts, identify patterns of interest, and organize investigative priorities.

## 8. Tools and Technologies

**Programming Language**
- Python

**Data Processing**
- Pandas

**Network Analysis**
- NetworkX

**Data Visualization**
- Matplotlib

**Development Environment**
- Google Colab
- Jupyter Notebook

**Version Control and Portfolio**
- GitHub

## 9. How to Run the Project

1. Download or clone this GitHub repository.
2. Open the Jupyter Notebook (`.ipynb`) file using Google Colab or Jupyter.
3. Download the IBM AML dataset from the Kaggle source linked above.
4. Install the Python libraries required by the notebook.
5. Update dataset paths to match your environment.
6. Run the notebook cells in sequence.

The notebook contains the Python implementation and accompanying analytical explanations.

## 10. Limitations

- The dataset contains simulated financial transactions and may not fully represent real-world financial behavior.
- The laundering-centered network focuses on a selected subset of accounts and transactions rather than the entire transaction network.
- Network centrality and community membership are structural indicators and do not independently establish criminal activity.
- The results may be sensitive to network construction choices and community detection methods.
- The analysis does not establish the operational effectiveness of the approach in a live AML monitoring environment.

Further work could incorporate additional transaction characteristics, temporal analysis, and predictive modeling.

## 11. Project Contributors

This project was collaboratively developed as part of **STAT 280 – Practical Machine Learning** at the University of the Philippines Diliman.

### Team Members and Contributions

| Contributor | Primary Responsibilities |
|---|---|
| **Mico** | Network construction, fraud attribute mapping, community and fraud-ring analysis, code integration, and cleanup |
| **Drea** | Data preparation and cleaning, Network Exploratory Data Analysis (EDA), network measures, network visualization, and interpretation |
| **Gids** | Data preparation and cleaning, Network Exploratory Data Analysis (EDA), network measures, network visualization, and interpretation |
| **Dani** | Network construction, fraud attribute mapping, community and fraud-ring analysis, code integration, and cleanup |


### Collaborative Activities

All team members jointly participated in:

- Reviewing the Social Network Analysis template and adapting its methodology.
- Identifying and evaluating potential datasets.
- Selecting the final dataset and assessing its feasibility.
- Defining the fraud detection problem and analytical objectives.
- Reviewing the completed notebook.
- Conducting the final execution, validation, and reproducibility checks.

**Contribution Note:** The responsibilities listed above reflect the project's agreed division of work. The analysis, findings, and final outputs are products of collaborative team effort.

## 12. Project Information

**Project Type:** Academic Group Project

**Course:** STAT 280 – Practical Machine Learning

**Institution:** University of the Philippines Diliman

**Field:** Data Science, Social Network Analysis, Financial Crime Analytics

---

*This project was developed for academic purposes. Its findings are intended to demonstrate analytical methods and should not be interpreted as evidence of criminal conduct by any particular account holder.*
