# VMware Chatbot Application

This project implements a conversational AI chatbot designed to interact with VMware environments. It leverages a Large Language Model (LLM) to understand natural language queries, execute API calls against a VMware API (or a dummy data source), and provide human-readable responses, including structured data with download options.

## Table of Contents

1.  [Introduction](#1-introduction)
2.  [Features](#2-features)
3.  [Prerequisites](#3-prerequisites)
4.  [Setup and Installation](#4-setup-and-installation)
5.  [Configuration](#5-configuration)
6.  [Running the Application](#6-running-the-application)
7.  [Application Components](#7-application-components)
8.  [Flow of Sequence (How it Works)](#8-flow-of-sequence-how-it-works)
9.  [Major Libraries Used](#9-major-libraries-used)
10. [How to Use the Chatbot](#10-how-to-use-the-chatbot)
11. [Troubleshooting](#11-troubleshooting)
12. [Security Considerations](#12-security-considerations)

---

### 1. Introduction

The VMware Chatbot provides an intuitive way to query and retrieve information from your VMware infrastructure using natural language. It acts as an intelligent assistant, capable of understanding complex requests, executing relevant API operations, and summarizing the results in an easily digestible format.

### 2. Features

* **Natural Language Interaction:** Communicate with your VMware environment using plain English.
* **API Tool Integration:** Automatically identifies and calls relevant API endpoints based on your queries (e.g., list VMs, check health).
* **OAuth 2.0 Authentication:** Securely authenticates with your VMware API using the Resource Owner Password Credentials (ROPC) flow.
* **Dynamic Data Presentation:** Displays tabular API responses as formatted Markdown tables directly in the chat.
* **Data Export:** Allows downloading of tabular data as CSV or PDF reports.
* **Configurable Backend:** An admin panel to easily set up API keys, OpenAPI spec URLs, and OAuth credentials.
* **Dummy Data Mode:** Functions with local `vinfo.json` data for development/testing without a live API connection.

### 3. Prerequisites

Before you begin, ensure you have the following installed:

* **Python 3.8+**: The backend is built with Flask.
* **pip**: Python package installer (usually comes with Python).
* **A VMware API Backend**: This application is designed to interact with a VMware API that exposes its capabilities via an OpenAPI (Swagger) specification.
    * **Alternatively, for development/testing, the application can run in "dummy data" mode using the provided `vinfo.json` and dummy OpenAPI spec.**
* **An OAuth 2.0 Server**: Your VMware API should have an OAuth 2.0 server for authentication (e.g., a `/token` endpoint).

### 4. Setup and Installation

Follow these steps to get the application running:

1.  **Clone the Repository (or set up files):**
    If you have a Git repository, clone it:
    ```bash
    git clone <your-repository-url>
    cd vmware-chatbot
    ```
    Otherwise, ensure all project files (`app.py`, `openapi_bundler.py`, `config.json`, `vinfo.json`, `templates/`, `static/`) are in their correct relative paths.

2.  **Create a Virtual Environment (Recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate # On Windows: .\venv\Scripts\activate
    ```

3.  **Install Python Dependencies:**
    Create a `requirements.txt` file in your project root with the following content:
    ```
    Flask
    requests
    google-generativeai
    PyYAML
    jsonref
    ```
    Then, install them:
    ```bash
    pip install -r requirements.txt
    ```

4.  **Prepare `vinfo.json`:**
    The `vinfo.json` file is included in the project and serves as a local dummy data source for VM information. Ensure it's present in the root directory alongside `app.py`. It's used when the chatbot operates in dummy API mode.

5.  **Generate `openapi.json`:**
    The `openapi_bundler.py` script is used to merge multiple OpenAPI specification files into a single `openapi.json` file, which your Flask app will consume. This is crucial for the chatbot to understand your API's capabilities.

    * Ensure your individual OpenAPI spec files (e.g., `vcenter.yaml`, `vi-json.yaml`, `sddc-manager-openapi.json`, `vsan-data-protection-openapi.yaml`) are present in the root directory.
    * **Crucially, ensure at least one of your input OpenAPI files (or the `dummy_vcenter_yaml` within `openapi_bundler.py` itself if you're using its default placeholders) contains a `servers` block at the root level, pointing to your API's base URL.** For example:
        ```json
        {
          "openapi": "3.0.0",
          "info": { ... },
          "servers": [
            {
              "url": "http://localhost:8000",
              "description": "Local API Server"
            }
          ],
          "paths": { ... }
        }
        ```
    * Run the bundler:
        ```bash
        python openapi_bundler.py
        ```
        This will create (or update) `openapi.json` in your project root.

### 5. Configuration

The application's settings are managed via `config.json` and the Admin Panel.

1.  **Initial `config.json`:**
    Create a `config.json` file in your project root with the following structure. You'll fill in the actual values via the Admin Panel.
    ```json
    {
        "GEMINI_API_KEY": "",
        "OPENAPI_SPEC_URL": "[http://0.0.0.0:8000/openapi.json](http://0.0.0.0:8000/openapi.json)",
        "OAUTH_SERVER_URL": "[http://0.0.0.0:8000/token](http://0.0.0.0:8000/token)",
        "OAUTH_CLIENT_ID": "",
        "OAUTH_CLIENT_SECRET": "",
        "OAUTH_USERNAME": "admin",
        "OAUTH_PASSWORD": "adminpass",
        "OAUTH_SCOPE": ""
    }
    ```

2.  **Using the Admin Panel:**
    After running the application (see next section), navigate to `http://localhost:5000/admin` in your web browser. Here, you can:
    * **Gemini API Key:** Enter your Google Gemini API key. Without this, the chatbot's AI capabilities will be limited.
    * **OpenAPI Spec URL:** Provide the URL where your API's `openapi.json` file is served (e.g., `http://0.0.0.0:8000/openapi.json`). If this is empty or invalid, the chatbot will fall back to its internal dummy OpenAPI spec.
    * **OAuth 2.0 ROPC Configuration:**
        * **OAuth Server URL:** The URL of your OAuth token endpoint (e.g., `http://0.0.0.0:8000/token`).
        * **OAuth Client ID / Secret:** Your OAuth client credentials.
        * **OAuth Username / Password:** Credentials for the Resource Owner Password Credentials (ROPC) flow.
        * **OAuth Scope (optional):** Any specific scopes required for your API access.

    Click "Save Configuration" after making changes. The application will automatically reload with the new settings.

### 6. Running the Application

1.  **Start your API Server (if applicable):**
    If you have a separate API backend that serves the `openapi.json` and handles VMware data, ensure it's running and accessible at the `OPENAPI_SPEC_URL` you configured (e.g., `http://0.0.0.0:8000`).

2.  **Start the Flask Chatbot Application:**
    From your project's root directory:
    ```bash
    python app.py
    ```
    This will start the Flask development server, usually on `http://0.0.0.0:5000`.

3.  **Access the Chatbot:**
    Open your web browser and navigate to `http://localhost:5000`.

### 7. Application Components

The project is structured into several key components:

* **`app.py`**:
    * The main Flask application file.
    * Handles web routes (`/`, `/admin`, `/chat`, `/download_csv`, `/get_message_data`).
    * Manages configuration loading and saving (`Config` class).
    * Integrates with the LLM (`LLMIntegration` class) for natural language processing and response generation.
    * Manages API tool discovery and execution (`MCPServer` class).
    * Handles OAuth 2.0 authentication (`OAuthHandler` class).
    * Serves as the central orchestrator for the chatbot's logic.

* **`templates/index.html`**:
    * The main user interface for the chatbot.
    * Displays chat messages.
    * Provides the input field and send button.
    * Dynamically renders bot responses, including Markdown tables.
    * Includes JavaScript for client-side interactivity and download features (CSV/PDF).

* **`templates/admin.html`**:
    * The web-based configuration panel.
    * Allows users to input and save API keys, OpenAPI URLs, and OAuth credentials.
    * Displays startup messages and configuration warnings.
    * Includes an interactive help guide.

* **`openapi_bundler.py`**:
    * A utility script to merge multiple OpenAPI YAML/JSON files into a single `openapi.json`.
    * Resolves `$ref` pointers within the merged specification.
    * This script is crucial for generating the comprehensive `openapi.json` that the chatbot uses to understand your API.

* **`vinfo.json`**:
    * A static JSON file containing dummy Virtual Machine (VM) inventory data.
    * Used by `app.py` when the chatbot is operating in "dummy API" mode, providing sample data for VM-related queries without needing a live API connection.

* **`config.json`**:
    * A JSON file used to persist application configuration settings (API keys, URLs, credentials).
    * Loaded by the `Config` class in `app.py`.

* **`static/` directory**:
    * **`static/css/style.css`**: Custom CSS for additional styling beyond Tailwind CSS.
    * **`static/images/`**: Contains icons for download buttons (e.g., `csv.png`, `pdf.png`).
    * **`static/js/main.js`**: Client-side JavaScript for handling chat interactions, sending messages to the backend, appending responses, and managing UI elements.

### 8. Flow of Sequence (How it Works)

The chatbot operates through a well-defined flow:

1.  **User Initiates Query:**
    * You type a message in the chat input field on `index.html`.
    * Client-side JavaScript (`main.js`) captures this message.

2.  **Query Sent to Backend:**
    * `main.js` sends your message via an AJAX POST request to the `/chat` endpoint in the Flask backend (`app.py`).

3.  **LLM Decision Making:**
    * Inside `app.py`, your query, along with a detailed description of all available API tools (derived from the `openapi.json` spec), is sent to the Large Language Model (LLM - Gemini).
    * The LLM analyzes your intent and decides:
        * **Option A: Call an API Tool:** If your query requires specific data or an action (e.g., "list VMs," "check health"), the LLM returns a JSON object indicating the `tool_name` (operationId) and any `parameters` needed.
        * **Option B: Direct Conversational Response:** If the query is general or informational, the LLM returns a direct text response.

4.  **API Tool Execution (If applicable - Option A):**
    * If a tool call is indicated, `app.py`'s `MCPServer` component prepares to execute the API call.
    * The `OAuthHandler` ensures the request is authenticated by acquiring or refreshing an access token.
    * The `MCPServer` constructs the correct API URL and headers (including the authorization token) based on the OpenAPI specification and the LLM's parameters.
    * The API call is made to your VMware API backend (or the dummy API logic if configured).

5.  **Data Retrieval and LLM Summarization:**
    * The API backend responds with raw data (e.g., a list of VMs in JSON format) or an error.
    * This raw data is then sent back to the LLM (along with your original query) for summarization.
    * The LLM is specifically prompted to transform complex JSON data into concise, human-readable summaries, often converting lists of objects into Markdown tables.

6.  **Response Sent to Frontend:**
    * The LLM's final natural language response (which might include Markdown) is sent back from `app.py` to `main.js` in the frontend.

7.  **Response Display and Interactivity:**
    * `main.js` receives the bot's response.
    * `Marked.js` is used to render any Markdown content (like tables) into proper HTML within the chat bubble.
    * If the bot's response contains a Markdown table, `main.js` dynamically adds "Download CSV" and "Download PDF" buttons below the message.
    * The chat interface automatically scrolls to display the latest message.
    * Clicking the download buttons triggers separate backend endpoints (`/download_csv/<index>` or `/get_message_data/<index>`) to retrieve the raw data and generate the respective file.

### 9. Major Libraries Used

**Python (Backend):**

* **Flask**: A micro web framework for Python, used for building the web application and API endpoints.
* **requests**: An elegant and simple HTTP library for making API calls to external services (like your VMware API or OAuth server).
* **google-generativeai**: Google's official client library for interacting with the Gemini API (the LLM).
* **PyYAML**: A YAML parser and emitter for Python, used for loading YAML-formatted OpenAPI specifications.
* **jsonref**: A library for resolving JSON references (`$ref`) in JSON/YAML documents, crucial for bundling OpenAPI specs.
* **csv**: Python's built-in module for CSV file reading and writing.
* **io**: Python's built-in module for working with I/O streams, used for in-memory CSV generation.

**JavaScript (Frontend):**

* **Tailwind CSS**: A utility-first CSS framework used via CDN for rapid and responsive styling of the HTML pages.
* **Marked.js**: A JavaScript library that parses Markdown text and converts it into HTML, enabling rich text formatting in chat responses.
* **html2canvas**: A JavaScript library that allows you to take screenshots of web pages or specific DOM elements, used as a dependency for jsPDF to render HTML.
* **jsPDF**: A client-side JavaScript library for generating PDF documents directly in the browser.
* **jspdf-autotable**: A plugin for jsPDF that simplifies the creation of tables within PDF documents, used for exporting structured data.

### 10. How to Use the Chatbot

Once the application is running and configured:

1.  **Access the Chat Interface:** Open your browser to `http://localhost:5000`.
2.  **Start Chatting:** Type your queries in the input field at the bottom and press Enter or click "Send".
3.  **Ask for VMware Data:**
    * **General VM Information:** Try queries like "List all VMs," "Show me the virtual machines," or "What VMs do I have?" (This will use the `/vmware_data/vinfo` endpoint).
    * **Specific VM Fields:** Ask for particular details, e.g., "What are the powerstates of the VMs?", "Tell me the DNS names of all VMs," "How much memory do the VMs have?" (This uses the `/vmware_data/vinfo/{field_name}` endpoint).
    * **Appliance Health/Services:** "Is the appliance healthy?", "List appliance services."
4.  **Observe Responses:**
    * The chatbot will interpret your query.
    * If an API call is made, you'll see a "Thinking..." indicator.
    * Responses containing tabular data (like VM lists) will be formatted as clear Markdown tables.
5.  **Download Data:**
    * For any bot message that includes a table, you will see a "Download CSV" and "Download PDF" button below the message bubble.
    * Click "Download CSV" to get the raw tabular data in CSV format.
    * Click "Download PDF" to generate a formatted PDF report of the table.
6.  **Configure Settings:**
    * Click the "Admin Panel" link in the chat header (or navigate directly to `http://localhost:5000/admin`).
    * Update your API keys, URLs, and OAuth credentials as needed.
    * Use the "Help" icon in the Admin Panel for an interactive guide on the application's internal workings.

### 11. Troubleshooting

* **"config.json not found" / "Error decoding config.json"**:
    * Ensure `config.json` exists in the root directory and is valid JSON.
    * Use the Admin Panel to save configuration, which will create/update this file.
* **"Gemini API Key is missing"**:
    * Go to the Admin Panel (`/admin`) and enter your valid Gemini API Key.
* **"No 'servers' found in OpenAPI spec"**:
    * This means the `openapi.json` file being served at your `OPENAPI_SPEC_URL` (e.g., `http://0.0.0.0:8000/openapi.json`) is missing the top-level `servers` array.
    * You **must** modify the source of your `openapi.json` (e.g., in your API backend's code, or the `openapi_bundler.py` script's dummy definitions) to include a `servers` block like:
        ```json
        "servers": [
          {
            "url": "http://localhost:8000",
            "description": "Local API Server"
          }
        ],
        ```
    * After modifying, restart your API server (if separate) and then restart `app.py`.
* **"HTTP Error: 404 - Object type 'vm' not supported or no column descriptions defined."**:
    * This indicates a mismatch between the API path the chatbot is trying to call and what your actual API (or its `openapi.json` definition) expects.
    * Ensure the path for fetching all VM data in your `openapi.json` is exactly `/vmware_data/vinfo` and that the corresponding endpoint in your API backend handles this path.
    * Verify the `operationId` `get_vmware_data_vmware_data__object_type__get` in your `openapi.json` maps to this correct path.
* **"Failed to obtain OAuth access token."**:
    * Check your OAuth Server URL, Client ID, Client Secret, Username, and Password in the Admin Panel.
    * Ensure your OAuth server is running and accessible.
    * Verify the credentials are correct for the ROPC flow.
* **Chatbot doesn't respond or gives generic errors**:
    * Check the Flask console for any Python tracebacks or error messages.
    * Ensure your Gemini API key is valid and has sufficient quota.
    * Review the `tool_prompt` and `llm_decision_raw` output in the Flask console to see what the LLM is deciding.

### 12. Security Considerations

* **`verify=False` in `requests`**: The code uses `verify=False` in `requests` calls (for both OpenAPI fetching and API calls). This disables SSL certificate verification and is **highly insecure for production environments**. It's used here for development simplicity, especially with self-signed certificates or local HTTP servers. **For production, remove `verify=False` and ensure proper SSL certificate validation.**
* **OAuth Credentials in `config.json`**: Storing sensitive credentials (API keys, OAuth passwords/secrets) directly in `config.json` is not recommended for production. Consider using environment variables or a dedicated secrets management system.
* **Debug Mode**: `app.run(debug=True)` should **never** be used in a production environment as it can expose sensitive information and allow arbitrary code execution.
