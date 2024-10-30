
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

## Running the App

1. Ensure you have a **Google Cloud service account key** file (`.json` format) with access to Vertex AI.

2. Run the Docker container, replacing `/path/to/your/service_account.json` with the actual path to your credentials file on your local machine:

   ```bash
   docker run -p 8501:8501 \
       -e GOOGLE_APPLICATION_CREDENTIALS=/app/service_account.json \
       -v /path/to/your/service_account.json:/app/service_account.json \
       ghcr.io/babak01/vertex-ai-llm-comparator-docker:latest
   ```

   This command:
   - Exposes the Streamlit app on port 8501.
   - Sets the `GOOGLE_APPLICATION_CREDENTIALS` environment variable within the container.
   - Mounts your service account JSON file into the container at `/app/service_account.json`.

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
