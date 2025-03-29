# LinkedIn Post Idea Generator (using Gemini Flash/Pro)

A Python script leveraging Google's Gemini AI (attempting Gemini 1.5 Flash with fallback to Gemini Pro) and the LangGraph framework to generate creative and actionable LinkedIn post ideas focused on professional networking.

![image](https://img.shields.io/badge/Python-3.8%2B-blue)
![image](https://img.shields.io/badge/AI_Model-Google_Gemini-orange)
![image](https://img.shields.io/badge/Framework-LangGraph-green)

## Overview

Coming up with fresh content for LinkedIn can be challenging. This tool aims to assist professionals by automatically generating a list of post ideas centered around networking. It takes optional user input as context (e.g., "tech conferences", "career change", "mentorship") or generates general ideas if no context is provided. The output is structured as a numbered list for easy use.

The project utilizes:
*   **Google Gemini:** Taps into Google's powerful generative AI models (specifically trying the efficient `gemini-1.5-flash-latest` model, falling back to `gemini-pro` if needed) to brainstorm creative ideas.
*   **LangGraph:** A library for building stateful, multi-actor applications with LLMs. Here, it manages the simple workflow: receive input -> call LLM -> output result.

## Features

*   **AI-Powered Ideas:** Generates 5 creative LinkedIn post ideas per run.
*   **Networking Focus:** Tailored specifically for professional networking themes.
*   **Context-Aware (Optional):** Accepts user input to guide idea generation.
*   **Structured Output:** Presents ideas in a clear, enumerated list (`Suggestion 1: ...`).
*   **Gemini Integration:** Uses the official `google-generativeai` Python library.
*   **LangGraph Framework:** Demonstrates a basic LangGraph application structure for managing state (conversation history) and node execution.
*   **Simple CLI:** Easy-to-use command-line interface.
*   **Robust Error Handling:** Includes `try...except` blocks for model initialization, API calls, and graph execution to prevent crashes and provide feedback.

## Technology Stack

*   Python 3.8+
*   `google-generativeai`: Google AI Python SDK
*   `langgraph`: Library for building stateful LLM applications
*   `langchain-core`: Core abstractions for messages (used by LangGraph)
*   `typing_extensions`: For advanced type hinting (`TypedDict`, `Annotated`)

## Prerequisites

1.  **Python:** Ensure you have Python 3.8 or later installed.
2.  **Pip:** Python's package installer (usually comes with Python).
3.  **Google Cloud Project:** You need a Google Cloud project with the "Generative AI API" (also sometimes referred to as Vertex AI or similar, check Google Cloud documentation) enabled.
4.  **Google API Key:** Generate an API key associated with your enabled Google Cloud project. See [Google Cloud API Key Documentation](https://cloud.google.com/docs/authentication/api-keys).

## Installation

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/your-username/Linkedin_Post_Idea_Generator_with_Gemini2.0Flash.git
    cd Linkedin_Post_Idea_Generator_with_Gemini2.0Flash
    ```
    (Replace `your-username` with your actual GitHub username)

2.  **Install Dependencies:**
    ```bash
    pip install google-generativeai langgraph langchain-core typing_extensions
    ```
    *Optional but recommended:* Create a virtual environment first:
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    pip install google-generativeai langgraph langchain-core typing_extensions
    ```

## Configuration: Setting Your API Key

You need to provide your Google API key to the script.

**Option 1: Directly in the Code (Less Secure)**

*   Open the main Python script (e.g., `main.py` or the script name you use).
*   Find the line:
    ```python
    GOOGLE_API_KEY = "YOUR_GOOGLE_API_KEY" # <<< --- REPLACE WITH YOUR KEY ---
    ```
*   Replace `"YOUR_GOOGLE_API_KEY"` with your actual API key.

**Option 2: Environment Variable (Recommended)**

*   Set an environment variable named `GOOGLE_API_KEY` with your key value.
    *   **Linux/macOS:**
        ```bash
        export GOOGLE_API_KEY='YOUR_ACTUAL_API_KEY'
        ```
    *   **Windows (Command Prompt):**
        ```bash
        set GOOGLE_API_KEY=YOUR_ACTUAL_API_KEY
        ```
    *   **Windows (PowerShell):**
        ```bash
        $env:GOOGLE_API_KEY='YOUR_ACTUAL_API_KEY'
        ```
*   In the Python script, ensure the code to read the environment variable is active (uncomment the `os.getenv` line and comment out the direct assignment):
    ```python
    import os
    # GOOGLE_API_KEY = os.getenv("GOOGLE_API_KEY") # Use this line
    # GOOGLE_API_KEY = "YOUR_GOOGLE_API_KEY"      # Comment out or remove this line

    if not GOOGLE_API_KEY:
        raise ValueError("GOOGLE_API_KEY environment variable not set or key is missing.")
    ```

## Usage

1.  Navigate to the project directory in your terminal.
2.  Run the script:
    ```bash
    python your_script_name.py
    ```
    (Replace `your_script_name.py` with the actual filename of the script).
3.  The script will prompt you: `Enter some context for networking ideas (or leave blank):`
4.  Type a topic (e.g., `remote work challenges`, `finding mentors`, `attending industry events`) and press Enter, or just press Enter for general ideas.
5.  The script will interact with the Gemini API and print the generated post ideas.
6.  To exit, type `quit` or `q` and press Enter.

## Future Improvements

*   Allow users to specify the *number* of ideas to generate.
*   Add options for different *types* of posts (e.g., polls, questions, stories).
*   Implement more sophisticated context handling or memory.
*   Explore more complex LangGraph structures (e.g., conditional routing based on context).
*   Add options to refine or iterate on the generated ideas.
*   (Advanced) Explore integration with the LinkedIn API for direct posting (Note: LinkedIn's API for posting has limitations).
*   Develop a web interface using Flask or Streamlit.

## License

This project is licensed under the MIT License. 
