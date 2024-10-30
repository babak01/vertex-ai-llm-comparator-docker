
# Vertex AI LLM Comparator Docker Image

This repository provides a pre-built Docker image to run the Vertex AI LLM Comparator app, which allows users to compare responses from different LLM frameworks—Autogen, LangChain, and LangGraph—using Google Cloud’s Vertex AI.

## About the Project

The Vertex AI LLM Comparator app enables easy comparison of language model outputs from various frameworks to support informed model selection and performance insights. The application integrates Google Cloud credentials, allowing users to test responses in real-time.

## Getting Started

To use this Docker image, you'll need:
- [Docker installed](https://docs.docker.com/get-docker/) on your local machine.
- A Google Cloud account and service account credentials with Vertex AI API access.
- A valid Google Cloud Project ID and Region.

### Pulling the Docker Image

The Docker image for this app is hosted on GitHub Container Registry (GHCR). You can pull it directly using:

```bash
docker pull ghcr.io/babak01/vertex-ai-llm-comparator-docker:latest
```

## Setting Up Google Cloud and Enabling Vertex AI API

To run this app, you’ll need a Google Cloud Project with Vertex AI API enabled and a service account with the necessary permissions.

1. **Create a Google Cloud Project** (if you don’t have one already):
   - Go to the [Google Cloud Console](https://console.cloud.google.com/).
   - Click on **Select a project** > **New Project** and follow the prompts.

2. **Enable the Vertex AI API**:
   - In the Google Cloud Console, navigate to **APIs & Services** > **Library**.
   - Search for **Vertex AI API** and click on it.
   - Click **Enable** to activate the API for your project.

3. **Create a Service Account**:
   - Go to **IAM & Admin** > **Service Accounts** in the Cloud Console.
   - Click **Create Service Account** and enter a name and description.
   - Under **Grant this service account access to the project**, add the following roles:
     - `Vertex AI User`
     - `Storage Object Viewer` (for any data stored in Google Cloud Storage, if required)

4. **Download the Service Account Key**:
   - After creating the service account, go to the **Keys** tab.
   - Click **Add Key** > **Create New Key** and select **JSON**.
   - Save the downloaded JSON key file securely; this file will be used to authenticate the app.

## Running the App

1. Ensure you have the Google Cloud service account key file (`.json` format) that you downloaded in the previous step.

2. Run the Docker container. On Unix-based systems (Linux/macOS), use the following command, replacing `/path/to/your/service_account.json` with the actual path to your credentials file:

   ```bash
   docker run -p 8501:8501 \
       -e GOOGLE_APPLICATION_CREDENTIALS=/app/service_account.json \
       -v /path/to/your/service_account.json:/app/service_account.json \
       ghcr.io/babak01/vertex-ai-llm-comparator-docker:latest
   ```

   On **Windows PowerShell**, use the following command with backticks (`` ` ``) for line continuation:

   ```powershell
   docker run -p 8501:8501 `
       -e GOOGLE_APPLICATION_CREDENTIALS=/app/service_account.json `
       -v C:\path\to\your\service_account.json:/app/service_account.json `
       ghcr.io/babak01/vertex-ai-llm-comparator-docker:latest
   ```

   These commands:
   - Expose the Streamlit app on port 8501.
   - Set the `GOOGLE_APPLICATION_CREDENTIALS` environment variable within the container.
   - Mount your service account JSON file into the container at `/app/service_account.json`.

3. Open your browser and go to [http://localhost:8501](http://localhost:8501) to access the app.

## Configuration

- **Google Cloud Project ID** and **Region** are required when initializing Vertex AI in the app interface.
- After entering your Project ID and Region, click **Initialize Vertex AI** in the app to connect.

## Features

- Compare responses from Autogen, LangChain, and LangGraph frameworks.
- Real-time analysis using Vertex AI, tailored to your Google Cloud project.

## Repository Structure

This repository is public and contains only the Docker image. The source code is maintained privately but can be executed in this environment seamlessly.

## License

Distributed under the MIT License. See `LICENSE` for more information.

## Contact

For questions or feedback, please contact [babak01](https://github.com/babak01).
