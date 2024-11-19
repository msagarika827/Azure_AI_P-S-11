# Azure_AI_P-S-11
# Azure OpenAI Lab - Using Your Own Data

This project demonstrates how to integrate Azure OpenAI with your own data using Retrieval Augmented Generation (RAG). In this example, we use Margie's Travel brochures data to ground the model's responses, leveraging Azure AI Search for indexing and storage to manage data.

## Table of Contents
- [Prerequisites]
- [Provision Azure Resources]
- [Upload Your Data]
- [Deploy AI Models]
- [Create an Index]
- [Configure the Application]
- [Run the Application]
- [Cleanup]

## Prerequisites
- **Azure Subscription** with access to Azure OpenAI services.
- **Visual Studio Code** installed.
- **Git** installed.

## Provision Azure Resources

1. **Azure OpenAI Resource**: 
   - Subscription: Choose an approved Azure subscription.
   - Resource Group: Use the provided or create a new one.
   - Region: Choose from one of the following:
   - Pricing tier: 

2. **Azure AI Search Resource**:
   - Service Name: A unique name of your choice.
   - Pricing tier: 

3. **Azure Storage Account**:
   - Storage Account Name: 
   - Performance: 
   - Redundancy: 

## Upload Your Data

1. In Azure Portal, navigate to your Storage Account and open **Blob Containers**.
2. Create a container.
3. Upload the `.pdf` brochures to the root folder of the container.

## Deploy AI Models

1. Navigate to the **Azure OpenAI Resource** in the portal and open it in **Azure AI Studio**.
2. Deploy the following models:
   - **Text Embedding Model**: .
     - Deployment Name:
   - **GPT Model**: 
     - Deployment Name: 

## Create an Index

1. Navigate to the **Azure AI Search Resource**.
2. Go to the **Import and Vectorize Data** page.
3. Choose `Azure Blob Storage` and select:
   - Blob container: 
   - Azure OpenAI: Select the text-embedding model created earlier.
4. Enable **semantic ranking** and set the index name prefix .

## Configure the Application

1. Clone the project repository from GitHub: git clone https://github.com/MicrosoftLearning/mslearn-openai
2. Open the project in **Visual Studio Code**.

- **Install Dependencies**:
  - Python:
    ```
    pip install openai==1.13.3
    ```
4. Update the configuration file with the following details:
- Endpoint and Key from Azure OpenAI Resource.
- Deployment name of your GPT model.
- Endpoint and Key of the Azure AI Search service.
- Search Index name: .

## Run the Application

1. In the integrated terminal, navigate to your language-specific folder .
2. Run the application:
- Python:
  ```
  ____.py
  ```
3. Check the console for responses to the prompt, such as "Tell me about London," using the indexed data.
