
# Telegram AI Bot

This is a Telegram bot built with Python that integrates Groq's AI models for natural language processing, image analysis, and audio transcription. The bot can analyze images, answer questions, transcribe voice messages, and respond to general queries.


![Image Description](./image.png)
## Features

- **Text Queries**: Ask the bot any educational question, and it will provide a response based on Groq's AI model.
- **Image Analysis**: Send an image, and the bot will analyze and describe it, and answer questions about the image.
- **Audio Transcription**: Send a voice message, and the bot will transcribe the audio and provide a response.
- **Integration with Groq API**: The bot uses Groq's AI models for text completions, image analysis, and audio transcription.

## Prerequisites

- Python 3.11+
- Docker (optional, for containerized deployment)
- Telegram Bot Token
- Groq API Key

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/achuajays/telegram_multi_fuction_chatbot.git
cd telegram-ai-bot
```

### 2. Create a `.env` file

Create a `.env` file in the root directory of the project with the following content:

```plaintext
TELEGRAM_BOT_TOKEN=your_telegram_bot_token
GROQ_API_KEY=your_groq_api_key
```

Replace `your_telegram_bot_token` and `your_groq_api_key` with your actual API keys.

### 3. Install dependencies

If you're running the bot locally, create a virtual environment and install the required dependencies:

```bash
python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
pip install -r requirements.txt
```

### 4. Run the bot locally

You can run the bot locally using the following command:

```bash
python telegram_aibot.py
```

### 5. Docker Deployment (Optional)

Alternatively, you can deploy the bot inside a Docker container. Ensure you have Docker installed and follow these steps:

1. **Build the Docker image**:

   ```bash
   docker build -t telegram-ai-bot .
   ```

2. **Run the Docker container**:

   ```bash
   docker run --env-file .env -p 8080:8080 telegram-ai-bot
   ```

   This will start the bot inside a Docker container, using the environment variables from the `.env` file.

### 6. Testing the Bot

Once the bot is running, open Telegram, search for your bot (using the bot's username), and interact with it. The bot should respond to:

- Text queries
- Image analysis requests (send an image)
- Voice messages (send a voice message for transcription)

## Dockerfile

If you want to build the Docker image for deployment, the provided `Dockerfile` will handle the installation of dependencies and configuration for running the bot in a container.

### Example Dockerfile

```dockerfile
FROM python:3.11-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 8080

CMD ["python", "telegram_aibot.py"]
```

### 7. Accessing Logs

To view the logs of the bot container (if running in Docker), you can use:

```bash
docker logs -f <container_id>
```

Replace `<container_id>` with the actual container ID, which you can find by running `docker ps`.

## Troubleshooting

If you encounter issues, ensure that:

- Your `.env` file is correctly configured with the right API keys.
- All dependencies are installed correctly.
- The Telegram bot token and Groq API key are valid.
- The Docker container has internet access and can reach Groq's API and Telegram servers.

## Contributing

If you'd like to contribute to this project, feel free to fork the repository and create a pull request. Please ensure that your code is properly tested and follows best practices.

