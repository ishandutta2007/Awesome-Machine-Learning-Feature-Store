# Awesome-Machine-Learning-Feature-Store

# Top Machine Learning Feature Store Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Feature Management, Online/Offline Serving & Self-Hosted Feature Stores*  
**Last updated: October 2026**

This repository tracks notable **commercial feature stores** and **open-source projects** that manage feature definitions, ensure training-serving consistency, and serve features at low latency — eliminating training/serving skew and enabling feature reuse across ML teams.

**Examples** include Amazon SageMaker Feature Store, Tecton, Hopsworks, Databricks Feature Store, Google Vertex AI Feature Store, Molecula FeatureBase, Rasgo, Qwak, Iguazio, and Feast Cloud (the category leaders).

**Open-source emphasis**: Feature stores are one of the strongest open-source domains in ML infrastructure. **Feast** leads with over 7,000 GitHub stars as the most popular open-source feature store . **Hopsworks** provides a real-time AI lakehouse with a Python-centric feature store . **Featureform** acts as a virtual feature store orchestrating existing data infrastructure . **Feathub** from Alibaba brings stream-batch unified feature computation with Flink integration . This section is heavily expanded.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Amazon SageMaker Feature Store](https://aws.amazon.com/sagemaker/feature-store/)**  
  **AWS's fully managed feature store** — online store for low-latency serving and offline store for training data . **Online Store pricing**: $1.75/million read units, $7.45/million write units, $2.726/GB-month storage . **Offline Store** uses standard S3 pricing ($0.023/GB-month) with Parquet format . **Free tier**: first 10 GB online and 100 GB offline storage . **Hidden cost**: every `get_record` call costs ~$0.002 at scale — 1M daily inference requests = $60/month in API charges alone . **Best for AWS-native ML workloads**.

- **[Tecton](https://www.tecton.ai/)**  
  **Enterprise feature platform from the creators of Uber Michelangelo** — real-time and batch feature engineering with managed online store . **Pricing**: consumption-based via Feature Compute Units (FCUs) covering streaming ingestion, offline transformations, and online serving . **BYOC multi-cloud deployment** (AWS/GCP/Azure) with Unity Catalog governance and SOC 2 Type II compliance . **Cost crossover**: Tecton wins on cost above ~1-2M users; below that, self-hosted Feast is cheaper if you can absorb the ops burden . **Best for enterprises wanting managed feature platform at scale**.

- **[Databricks Feature Store](https://www.databricks.com/product/feature-store)**  
  **Feature store integrated with the Databricks Lakehouse** — billed at cost with no premium: you pay for underlying serverless compute, online store (Lakebase), and serving infrastructure . **Feature materialization** runs as serverless compute (FEATURE_STORE product SKU) . **Cost optimization**: group features sharing offline destination, online destination, and trigger into a single `materialize_features` call to reduce pipeline count . **Best for organizations already using Databricks**.

- **[Google Vertex AI Feature Store](https://cloud.google.com/vertex-ai/docs/featurestore)**  
  **Google's managed feature store** — **Legacy version deprecated February 17, 2026**; full shutdown February 17, 2027 . **Vertex AI Feature Store (v2)** is the recommended replacement, launched November 17, 2023 . **Pricing**: ~$0.10/1M reads and ~$0.10/GB/month columnar storage as of April 2026 . **Quota**: 10,000 reads/second per FeatureStore resource . **Best for GCP-native organizations migrating to v2**.

- **[Hopsworks (Managed)](https://www.hopsworks.ai/)**  
  **Managed Hopsworks** — serverless app available at app.hopsworks.ai with Gmail/GitHub registration . **Managed cloud** on AWS, Azure, and GCP with feature store, model registry, and MLOps capabilities . **Best for teams wanting managed Hopsworks**.

- **[Iguazio](https://www.iguazio.com/)**  
  **MLOps platform with built-in feature store** — real-time feature serving and model monitoring . **Best for enterprise MLOps**.

- **[Qwak](https://www.qwak.com/)**  
  **ML platform with feature store** — feature engineering, model training, and serving in one platform . **Best for end-to-end ML workflows**.

- **[Rasgo](https://www.rasgo.ai/)**  
  **Feature store and analytics platform** — SQL-based feature generation and management . **Best for SQL-centric feature engineering**.

- **[Molecula FeatureBase](https://www.molecula.com/)**  
  **Feature store built on FeatureBase** — real-time analytics and feature serving at scale . **Best for high-performance feature serving**.

## Open-Source GitHub Projects

### Core Feature Stores

- **[Feast](https://github.com/feast-dev/feast)**  
  **The leading open-source feature store with 7,000+ GitHub stars**, Apache-2.0 licensed . **Makes features consistently available for training and serving** — manages offline store (historical data), online store (low-latency serving), and feature server . **Point-in-time correct joins** — generates training data with `AS OF` joins returning feature values with largest `effective_timestamp <= event_timestamp`, preventing future data leakage . **Pluggable architecture**: offline stores (Parquet on S3), online stores (Redis/DynamoDB), and registries . **Cost advantage**: at 50k-500k users, Feast on AWS is significantly cheaper than Tecton — the crossover happens around 1-2M users . **Trade-off**: higher on-call burden — pages-per-week ran 6× higher than Tecton in one comparison . **Best for teams wanting control over feature infrastructure**.

- **[Hopsworks](https://github.com/logicalclocks/hopsworks)**  
  **Real-time AI Lakehouse with Python-centric Feature Store**, AGPL-3.0 licensed with **1,299+ GitHub stars** . **Modular platform** — use just feature store or full MLOps stack . **Time-travel support** on Hudi/Iceberg offline tables . **Project-based multi-tenancy** with secure sandboxes and fine-grained asset sharing . **Integrations**: Databricks, SageMaker, Kubeflow, Spark, Flink . **Deployment**: serverless app, managed cloud, or on-premise . **Best for real-time AI lakehouse deployments**.

- **[Featureform](https://github.com/featureform/featureform)**  
  **The Virtual Feature Store**, Apache-2.0 licensed with **1,978+ GitHub stars** . **Orchestrates existing data infrastructure** — define, version, and serve ML features via declarative Python API without replacing current systems . **Works with existing Spark, Snowflake, Redis, and more** . **Best for teams wanting feature store capabilities without infrastructure migration**.

- **[Feathub (Alibaba)](https://github.com/alibaba/feathub)**  
  **Stream-batch unified feature store**, Apache-2.0 licensed with **349+ GitHub stars** . **Consistent feature computation across offline, nearline, and online** . **Apache Flink 1.16 for real-time** with millisecond latency; **Apache Spark 3.3 for offline** with high throughput . **Pythonic SDK** with declarative feature definitions and point-in-time correctness . **Built-in feature monitoring** and feature registry . **Trade-off**: smaller community, heavy reliance on Flink for real-time . **Best for real-time ML with Flink**.

### Additional Strong Open-Source Options

- **Chronon (Airbnb)** — Feature engineering platform with point-in-time correctness guarantees .
- **Michelangelo (Uber)** — The canonical feature store pattern that inspired the industry; ~10,000 curated features and 250,000+ predictions/second .
- **Feast on Azure** — Azure plugins for Feast maintained by Microsoft .
- **SageMaker Feature Store streaming aggregation** — AWS samples for streaming feature aggregation .

**Frameworks for building custom feature store solutions**: Combine **Feast** for the most mature open-source feature store with pluggable offline/online stores and point-in-time correctness . Use **Hopsworks** for a real-time AI lakehouse with modular feature store and multi-tenancy . Deploy **Featureform** for virtual feature store that orchestrates existing infrastructure without migration . Choose **Feathub** for stream-batch unified computation with Flink integration . Note that true enterprise feature platforms with managed infrastructure, automatic scaling, and vendor-supported SLAs (SageMaker Feature Store, Tecton, Databricks Feature Store) remain primarily commercial territory; open-source stacks provide strong feature management, point-in-time correctness, and serving foundations that require integration for complete feature store deployments.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Feature stores handle sensitive ML training data and real-time serving traffic. Self-hosted solutions require proper security hardening, access controls, and compliance with data privacy regulations.
- **Point-in-time correctness is critical** — without `AS OF` joins, models learn from future information and produce zero online lift . Ensure your feature store implements this correctly.
- **Cost scales with read/write volume** — SageMaker Feature Store costs $1.75/million reads and $7.45/million writes . Tecton's FCU-based pricing requires careful monitoring . At scale, self-hosted Feast on AWS can be significantly cheaper below 1-2M users .
- **License considerations**: Feast uses Apache-2.0, Hopsworks uses AGPL-3.0, Featureform uses Apache-2.0, and Feathub uses Apache-2.0. Verify licensing against your use case before committing.
- The open-source ecosystem provides strong feature management, point-in-time correctness, and serving foundations, but **managed infrastructure, automatic scaling, and vendor-supported SLAs** remain primarily commercial offerings.

---

**Made for ML engineers, data scientists, and organizations seeking feature store sovereignty.**  
Let's make machine learning feature stores more open, transparent, and consistent.
