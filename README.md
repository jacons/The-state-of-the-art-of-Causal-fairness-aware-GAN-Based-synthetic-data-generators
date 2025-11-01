# The state-of-the-art of Causal fairness-aware GAN-Based synthetic data generators
**Report for "Statistics for Machine Learning" Ph.D A.y. Course 24/25**
***

## 📑 Overview

This repository contains the report on the **State-of-the-Art of synthetic data generators** based on **Generative Adversarial Networks (GANs)** that incorporate the concept of **Causal Fairness-Aware**.

The primary goal of these methodologies is twofold:
* Generate high-quality **tabular synthetic data** that closely resembles the real dataset.
* Remove **discriminatory biases** intrinsic to historical datasets.

The ultimate aim is to produce **discrimination-free** datasets, ensuring that any Machine Learning (ML) model trained on such data is inherently fair.

## 💻 Algorithms Analyzed

The report critically analyses and compares four cutting-edge architectures, presented in chronological order of publication, leveraging insights from the fields of Causal Inference and Generative Models.

### 1. FairGAN (2018)
* **Full Name:** Fairness-aware Generative Adversarial Network.
* **Principle:** It was one of the first GAN-based approaches to address discrimination in tabular Synthetic Data Generation (SDG).
* **Mechanism:** It extends the standard GAN architecture by introducing an **additional fairness constraint ($\lambda J_2$)**. This constraint forces the generator to make the *unprotected features* and the *target variable* statistically independent of the *protected attribute*.
* **Fairness Notion:** Primarily focused on satisfying **Demographic Parity (DP)** and **Fairness Through Unawareness (FTU)**.

### 2. CFGAN (Causal fairness-aware GAN) (2019)
* **Principle:** It combines the **CausalGAN** architecture with **causal reasoning** to impose stronger fairness guarantees than previous statistical methods.
* **Mechanism:** The architecture uses two generators and two discriminators. The key mechanism consists of minimising the **"change in distribution"** (e.g., Total Effect, Path-Specific Effect, or Counterfactual Effect) caused by an **intervention ($do$-operator)** on the protected attribute within the causal structure.
* **Requirement:** Requires a priori knowledge of the data's **causal structure (causal graph)**.

### 3. DECAF (2021)
* **Full Name:** Generating Fair Synthetic Data Using Causally-Aware Generative Networks.
* **Principle:** It formalises fairness through **graphical conditions**, enabling flexible *debiasing* strategies that are directly linked to the underlying causal model.
* **Mechanism:** It leverages the **d-separation** property in the causal graph to identify and **selectively remove edges** (i.e., causal paths) that propagate discrimination. The removal of an edge is explicitly modelled as the application of a **do-operator** on the conditional distribution.
* **Fairness Notions:** Can satisfy **Conditional Fairness (CF)**, **FTU**, and **DP** by strategically modifying the graph structure.

### 4. CFSDG (Counterfactual Fairness in Synthetic Data Generation) (2022)
* **Principle:** Represents the most recent approach analysed, shifting the focus towards fairness guarantees achieved through **counterfactual reasoning**.
* **Fairness Notion:** **Counterfactual Fairness (COF)** (Definition 4).
* **Mechanism:** It introduces a specific **counterfactual loss** that forces the model to generate the **same outcome** for an individual, even if their *protected attribute* were different, while holding all other non-descendent factors constant. The goal is incentive alignment: an accurate predictor trained on this data will inherently be fair.

## 🚀 Report Conclusions

Despite significant contributions to both data utility and fairness, the primary challenges remain. Most causal fairness-aware GANs rely on the assumption of having access to a **known and faithful causal graph** (which is often unrealistic or hard to discover). Furthermore, while the models are structurally grounded in causal theory, the internal GAN-based generators often operate as **black boxes**. Future research may explore using interpretable generative models to replace the GAN sub-components, thereby achieving full comprehensibility of the data generation process.
