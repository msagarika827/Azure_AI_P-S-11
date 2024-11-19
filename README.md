# Azure_AI_P-S-11
# Azure OpenAI Lab - Using Your Own Data

This project demonstrates how to integrate Azure OpenAI with your own data using Retrieval Augmented Generation (RAG). In this example, we use Margie's Travel brochures data to ground the model's responses, leveraging Azure AI Search for indexing and storage to manage data.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Provision Azure Resources](#provision-azure-resources)
- [Upload Your Data](#upload-your-data)
- [Deploy AI Models](#deploy-ai-models)
- [Create an Index](#create-an-index)
- [Configure the Application](#configure-the-application)
- [Run the Application](#run-the-application)
- [Cleanup](#cleanup)

## Prerequisites
- **Azure Subscription** with access to Azure OpenAI services.
- **Visual Studio Code** installed.
- **Git** installed.

## Provision Azure Resources

1. **Azure OpenAI Resource**: 
   - Subscription: Choose an approved Azure subscription.
   - Resource Group: Use the provided or create a new one.
   - Region: Choose from one of the following: `Australia East`, `Canada East`, `East US`, `France Central`, etc.
   - Pricing tier: `Standard S0`.

2. **Azure AI Search Resource**:
   - Service Name: A unique name of your choice.
   - Pricing tier: `Basic`.

3. **Azure Storage Account**:
   - Storage Account Name: A unique name.
   - Performance: `Standard`.
   - Redundancy: `Locally redundant storage (LRS)`.

## Upload Your Data

1. Download the travel brochures data from [this link](https://aka.ms/own-data-brochures).
2. In Azure Portal, navigate to your Storage Account and open **Blob Containers**.
3. Create a container named `margies-travel`.
4. Upload the `.pdf` brochures to the root folder of the `margies-travel` container.

## Deploy AI Models

1. Navigate to the **Azure OpenAI Resource** in the portal and open it in **Azure AI Studio**.
2. Deploy the following models:
   - **Text Embedding Model**: `text-embedding-ada-002`.
     - Deployment Name: `text-embedding-ada-002`.
   - **GPT Model**: `gpt-35-turbo-16k` (or `gpt-35-turbo` if unavailable).
     - Deployment Name: `gpt-35-turbo-16k`.

## Create an Index

1. Navigate to the **Azure AI Search Resource**.
2. Go to the **Import and Vectorize Data** page.
3. Choose `Azure Blob Storage` and select:
   - Blob container: `margies-travel`.
   - Azure OpenAI: Select the text-embedding model created earlier.
4. Enable **semantic ranking** and set the index name prefix to `margies-index`.

## Configure the Application

1. Clone the project repository from GitHub: git clone https://github.com/MicrosoftLearning/mslearn-openai
2. Open the project in **Visual Studio Code**.
3. Choose the appropriate language folder (`CSharp` or `Python`):
- **Install Dependencies**:
  - C#:
    ```
    dotnet add package Azure.AI.OpenAI --version 1.0.0-beta.14
    ```
  - Python:
    ```
    pip install openai==1.13.3
    ```
4. Update the configuration file with the following details:
- Endpoint and Key from Azure OpenAI Resource.
- Deployment name of your GPT model.
- Endpoint and Key of the Azure AI Search service.
- Search Index name: `margies-index`.

## Run the Application

1. In the integrated terminal, navigate to your language-specific folder (`CSharp` or `Python`).
2. Run the application:
- C#:
  ```
  dotnet run
  ```
- Python:
  ```
  python ownData.py
  ```
3. Check the console for responses to the prompt, such as "Tell me about London," using the indexed data.

## Cleanup

To avoid incurring additional costs, remember to delete all Azure resources used in this lab:

1. Go to [Azure Portal](https://portal.azure.com).
2. Delete the following resources:
- Azure OpenAI Resource.
- Azure AI Search Resource.
- Azure Storage Account.

## Congratulations!

You have successfully completed the lab exercise. If you have any issues or need further assistance, feel free to consult the Azure documentation or reach out to support.
