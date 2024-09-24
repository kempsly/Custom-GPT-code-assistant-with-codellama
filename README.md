---

# CodeGuru - AI Code Assistant

CodeGuru is an AI-powered code assistant designed to help users by answering code-related questions. The application uses a model called `codeguru` and provides responses to user prompts via a simple web-based interface powered by Gradio.

## Features

- **Interactive Interface:** Provides an interactive interface where users can enter prompts related to coding or development.
- **Model Integration:** Integrates with the `codeguru` model hosted locally to generate responses based on user input.
- **History Tracking:** Maintains a history of user prompts during the session to provide context-aware responses.

## Requirements

To run this application, you will need:

- Python 3.x
- The following Python packages:
  - `requests`
  - `gradio`
  - `json`

You can install the necessary dependencies by running:

```bash
pip install requests gradio
```

## How to Run

1. Clone the repository and navigate to the project directory.
2. Start the model server for `codeguru` at `http://localhost:11434/api/generate` (the server hosting the model should already be running for the app to work).
3. Run the `app.py` script to start the Gradio interface.

```bash
python app.py
```

Once the application is running, you will see a Gradio interface in your web browser where you can input your prompts. The system will use the `codeguru` model to generate responses based on the input prompt.

## Model Configuration

The model configuration is set up in the model file as follows:

```bash
FROM codellama

## Set the Temperature
PARAMETER temperature 1

## Set the system prompt
SYSTEM """
You are a code teaching assistant named CodeGuru created by Kempsly. Answer all the code-related questions being asked.
"""
```

- **Temperature**: The temperature parameter is set to `1`, controlling the randomness of the model’s output.
- **System Prompt**: The system prompt initializes the model as a code teaching assistant.

## API Details

The application sends a POST request to the `codeguru` model API:

- **URL**: `http://localhost:11434/api/generate`
- **Headers**: `Content-Type: application/json`
- **Request Body**: 
  ```json
  {
    "model": "codeguru",
    "prompt": "<user input + history>",
    "stream": false
  }
  ```

The response from the model is displayed as text on the Gradio interface.

## Troubleshooting

- Ensure the `codeguru` model server is running on `localhost:11434`.
- If you encounter an error, check the terminal for any error messages. Common issues may include:
  - Incorrect API URL.
  - Model server not running.
  - Missing dependencies.

## License

This project is licensed under the MIT License.

---