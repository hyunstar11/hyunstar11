# H&M Churn Prediction Project Flowchart

```mermaid
flowchart TD
    %% External Entities
    User[👤 Business User] 
    DeepDish[🖥️ Northwestern DeepDish<br/>GPU Cluster]
    
    %% Security & Access
    subgraph Security ["🔒 Security & Access"]
        IAM[🔑 AWS IAM<br/>Identity & Access Management]
        CloudTrail[📋 AWS CloudTrail<br/>Audit Logging]
        GuardDuty[🛡️ AWS GuardDuty<br/>Threat Detection]
    end
    
    %% VPC Infrastructure
    subgraph VPC ["🏗️ VPC (10.0.0.0/22)"]
        subgraph PublicSubnet ["📡 Public Subnet (10.0.0.0/24)"]
            ALB[⚖️ Application Load Balancer]
            IGW[🌐 Internet Gateway]
        end
        
        subgraph PrivateSubnet ["🔒 Private Subnet (10.0.1.0/24)"]
            ECS[📦 ECS Fargate<br/>Frontend Application]
            VPCEndpoint[🔗 VPC S3 Endpoint]
        end
    end
    
    %% Data Processing Pipeline
    subgraph DataPipeline ["📊 Data Processing Pipeline"]
        A[📄 Data Collection<br/>Articles, Customers, Transactions]
        B[🔄 Data Processing<br/>Cleaning & Integration]
        C[📈 Exploratory Data Analysis<br/>Customer, Transaction, Article Analysis]
        D[⚙️ Feature Engineering<br/>RFM Analysis]
    end
    
    %% Model Training & Storage
    subgraph MLPipeline ["🤖 ML Pipeline"]
        E[🎯 Model Training<br/>Random Forest Classifier]
        F[📊 Model Evaluation<br/>Accuracy: 75%, ROC AUC: 83%]
        G[💾 Model Artifacts<br/>Metrics, Visualizations]
    end
    
    %% AWS Infrastructure
    subgraph AWSInfra ["☁️ AWS Infrastructure"]
        S3[🪣 Amazon S3<br/>Model Storage & Artifacts]
        ECR[📦 Amazon ECR<br/>Container Registry]
        CloudWatch[📊 CloudWatch<br/>Monitoring & Logs]
    end
    
    %% Application Flow
    subgraph AppFlow ["💻 Application Flow"]
        Input[📝 User Inputs<br/>Customer Metrics]
        Prediction[🎯 Churn Prediction<br/>Risk Assessment]
        Results[📋 Results Display<br/>Probability & Recommendations]
    end
    
    %% Data Flow Connections
    DeepDish --> A
    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> G
    
    %% AWS Upload & Deployment
    G --> S3
    E --> S3
    F --> S3
    ECR --> ECS
    S3 --> ECS
    
    %% User Access Flow
    User --> ALB
    ALB --> ECS
    ECS --> Input
    Input --> Prediction
    ECS --> S3
    Prediction --> Results
    Results --> User
    
    %% Security Integration
    IAM -.-> S3
    IAM -.-> ECR
    IAM -.-> ECS
    IAM -.-> CloudWatch
    CloudTrail -.-> S3
    GuardDuty -.-> CloudWatch
    
    %% Infrastructure Connections
    IGW --> ALB
    ALB --> ECS
    ECS --> VPCEndpoint
    VPCEndpoint --> S3
    ECS --> CloudWatch
    
    %% Styling
    classDef security fill:#ff9999,stroke:#cc0000,stroke-width:2px
    classDef infrastructure fill:#99ccff,stroke:#0066cc,stroke-width:2px
    classDef dataprocessing fill:#99ff99,stroke:#009900,stroke-width:2px
    classDef mlpipeline fill:#ffcc99,stroke:#ff6600,stroke-width:2px
    classDef application fill:#cc99ff,stroke:#6600cc,stroke-width:2px
    
    class IAM,CloudTrail,GuardDuty security
    class VPC,PublicSubnet,PrivateSubnet,ALB,ECS,ECR,S3,CloudWatch infrastructure
    class A,B,C,D dataprocessing
    class E,F,G mlpipeline
    class Input,Prediction,Results application
```

## Enhanced Project Components

### 1. **Security & Compliance Layer**
   - **AWS IAM**: Role-based access control for all AWS resources
   - **CloudTrail**: Audit logging for all API calls and resource access
   - **GuardDuty**: Threat detection and security monitoring
   - **VPC Security Groups**: Network-level security controls

### 2. **Network Architecture**
   - **VPC (10.0.0.0/22)**: Isolated network environment
   - **Public Subnet**: Houses load balancer with internet access
   - **Private Subnet**: Secure environment for application containers
   - **VPC S3 Endpoint**: Private connection to S3 without internet routing

### 3. **Data Processing Pipeline**
   - **Northwestern DeepDish**: External GPU cluster for initial processing
   - **Data Collection**: Multi-source data ingestion (CSV files)
   - **ETL Processing**: Data cleaning and integration
   - **Feature Engineering**: RFM (Recency, Frequency, Monetary) analysis

### 4. **ML/AI Pipeline**
   - **Model Training**: Random Forest classifier with hyperparameter tuning
   - **Model Evaluation**: Comprehensive metrics and validation
   - **Artifact Management**: Automated storage of models and metadata

### 5. **Production Infrastructure**
   - **Container Orchestration**: ECS Fargate for serverless containers
   - **Load Balancing**: ALB for high availability and traffic distribution
   - **Storage**: S3 for scalable object storage with lifecycle policies
   - **Monitoring**: CloudWatch for operational insights

### 6. **Application Layer**
   - **Streamlit Interface**: Interactive web application
   - **Real-time Inference**: On-demand churn prediction
   - **User Experience**: Intuitive risk assessment and recommendations

## Project Components

1. **Data Pipeline**
   - Load data from CSV files
   - Process and prepare data for modeling
   - Generate EDA visualizations
   - Create feature-engineered dataset

2. **Model Training**
   - Train Random Forest classifier
   - Generate model metrics and visualizations
   - Save model artifacts to local storage
   - Upload artifacts to S3

3. **Web Application**
   - Streamlit interface for user inputs
   - Fetch latest model from S3
   - Generate predictions based on user inputs
   - Display churn probability and risk assessment

4. **AWS Deployment**
   - Store artifacts in S3
   - Package application in Docker container
   - Deploy container via ECS Fargate
   - Expose application through Application Load Balancer
   - Monitor via CloudWatch 