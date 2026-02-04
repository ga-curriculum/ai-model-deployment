<h1>
  <span class="headline">AI Model Deployment</span>
  <span class="subhead">Hyperscaler Vendor Offerings</span>
</h1>

## What is a Hyperscaler?

Hyperscalers are large cloud providers that offer scalable, on-demand computing resources across global data centers. These companies—**Amazon Web Services (AWS), Microsoft Azure, and Google Cloud Platform (GCP)**—enable enterprises to deploy AI and machine learning (ML) models at scale, leveraging their vast infrastructure and AI-specific services.

### Key Characteristics of Hyperscalers:
- **Global Scalability:** Worldwide data centers ensure low-latency access and redundancy.
- **On-Demand Resources:** Compute and storage scale dynamically and are billed based on usage.
- **AI/ML Services:** Pre-built and customizable tools for training, deploying, and monitoring ML models.
- **Security & Compliance:** Industry-standard security protocols and regulatory compliance (e.g., GDPR, HIPAA).

### Where does the need for hyperscalers come from?

<div class="mermaid">
graph TD;
    A[Traditional On-Prem Infrastructure] -->|Limited Compute| B[Scalability Issues];
    A -->|High Maintenance Costs| C[Operational Overhead];
    B --> D[AI Workload Growth];
    C --> D;
    D -->|Demand for Compute| E[Hyperscaler Cloud Model];
    E -->|On-Demand Resources| F[Scalable AI Deployment];
    E -->|Distributed Data Centers| G[Global Access & Redundancy];
    E -->|AI/ML Services| H[Optimized AI Workflows];
</div>

## Comparing AI/ML Offerings

The three major hyperscalers provide distinct AI/ML deployment options. Below is an overview of their capabilities:

| Cloud Provider | AI/ML Deployment Services | Key Strengths | Key Limitations |
|---------------|--------------------------|---------------|----------------|
| **AWS** | SageMaker, Lambda for inference, EKS for containerized models | Broadest AI/ML service ecosystem, strong security, global reach | Pricing complexity, potentially expensive for high-compute workloads |
| **Azure** | Azure Machine Learning, AKS for model hosting, Functions for serverless inference | Strong enterprise integration (Active Directory, DevOps), hybrid cloud capabilities | AI tooling ecosystem is still evolving compared to AWS |
| **GCP** | Vertex AI, Cloud Run, TensorFlow Serving, TPU accelerators | Best for AI-first workloads, strong model training and scaling capabilities | Fewer enterprise integrations compared to AWS and Azure |

## Choosing the Right Cloud Provider
Each hyperscaler has strengths and trade-offs. The best choice depends on the **business requirements, budget, and performance needs** of the AI solution.

- **Cost vs. Performance:** Is cost optimization more important than low latency or high throughput?
- **Integration Needs:** Does the organization already rely on a specific cloud ecosystem?
- **Scalability:** Will workloads fluctuate or require rapid scaling?
- **Security & Compliance:** Are there strict regulatory or data residency requirements?


## Hyperscaler Decision-Making Activity

In this scenario based discussion activity you will:

- Apply your knowledge to a real-world consulting scenario
- Use the [Hyperscaler Decision-Making Activity Worksheet](Decision_Making_Activity.pdf) to evaluate a case study and and recommend the most suitable cloud provider.
- Discuss trade-offs and justify your recommendation with peers

Be prepared to discuss your decisions with the class when we return from breakout rooms!
