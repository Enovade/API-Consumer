# Consuming Your First API in Azure API Management

**Duration**: 10 minutes  
**Objective**: Learn to manually define an HTTP API in Azure APIM, add operations to proxy a Node.js/Fastify backend and test the API.  
**Target Audience**: API Consumers or developers familiar with REST APIs and basic Azure APIM concepts.  
**Context**: This hands-on assumes a pre-deployed Fastify backend with `/pengguna` endpoints (e.g., `GET /pengguna`) hosted at `http://latihan.cloud-connect.asia:8080`.

---

## Prerequisites
- **Azure Account**: Access to an Azure subscription with an APIM instance created. Complete the quickstart at [Create an Azure API Management instance](https://learn.microsoft.com/azure/api-management/get-started-create-service-instance) if needed.[](https://learn.microsoft.com/en-us/azure/api-management/get-started-create-service-instance)
- **Fastify Backend**: A deployed Node.js/Fastify API with endpoints:
  - `GET /pengguna`: Returns a list of pengguna 
- **Tools**:
  - **Azure Portal**: For configuring APIM.
  - **Postman**: For testing API calls.
  - **API Key**: Obtained from the APIM Developer Portal.
- **Permissions**: Contributor or higher role on the APIM instance to add and configure APIs.

---

## Steps

### Step 1: Create a Blank HTTP API in Azure APIM (10 minutes)
1. **Log in to Azure Portal**:
   - Navigate to `https://portal.azure.com`.
   - Search for and select **API Management services**.
   - Select your APIM instance (e.g., `ktmb-apim`).

2. **Add a New API**:
   - In the APIM instance, go to the left menu > **APIs** > **+ Add API**.
   - Under **Create from scratch**, select **HTTP** to manually define an HTTP API.
   - In the **Create an HTTP API** dialog, choose **Full** to configure all settings.
   - Enter the following details:
     - **Display name**: `Pengguna API`
     - **Name**: `pengguna-api`
     - **Description** (optional): `API for managing pengguna, proxied to a Fastify backend.`
     - **Web service URL**: `http://latihan.cloud-connect.asia:8080/pengguna` (replace with your Fastify backend URL).
     - **API URL suffix**: `pengguna` (this makes the API accessible at `https://apim.ktmb.com.my/pengguna/api`.
     - **URL scheme**: Select **HTTPS** for security.
     - **Pengguna**: Check **Starter** and **Unlimited** to associate the API with these default products.
     - **Versioning**: Skip for simplicity (leave unchecked).
   - Click **Create**.

3. **Verify API Creation**:
   - In the **APIs** section, confirm that **Pengguna API** appears in the list.
   - Note the API’s gateway URL (e.g., `https://apim.ktmb.com.my/crs/api/pengguna`).

**Expected Outcome**: A blank HTTP API named `Pengguna API` is created, ready to proxy requests to the Fastify backend.

---

### Step 2: Add Operations to the API
1. **Add a GET Operation**:
   - Select **Pengguna API** in the **APIs** section.
   - Click **+ Add Operation**.
   - Configure the operation:
     - **Display name**: `Fetch Products`
     - **URL**: Select **GET** and enter `/pengguna` in the resource field.
     - **Description** (optional): `Retrieve a list of products.`
   - Click **Save**.
   - This maps to the backend’s `GET /pengguna` endpoint (e.g., `https://apim.ktmb.com.my/crs/api/pengguna`).
