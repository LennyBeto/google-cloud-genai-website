# Google Cloud GenAI Website

A web application built with Python that leverages Google Cloud's Generative AI capabilities. This project demonstrates the integration of Google Cloud's GenAI services with a modern web framework to create an AI-powered website.


## Overview

This application showcases the implementation of Google Cloud's Generative AI models (Gemini) in a web application context. It provides a foundation for building AI-powered features such as content generation, intelligent chatbots, or other GenAI capabilities using Google's state-of-the-art language models.

## Features

- **GenAI Integration**: Built-in support for Google Cloud's Generative AI services
- **Web Framework**: Python-based web application architecture
- **Modular Design**: Organized codebase with separate modules for models, routers, views, and utilities
- **Containerized**: Docker support for easy deployment
- **Static Assets**: Integrated static file serving for frontend resources
- **Template System**: Dynamic HTML rendering with template support

## Project Structure

```
google-cloud-genai-website/
├── models/              # Data models and schemas
├── routers/             # API route handlers and endpoints
├── static/              # Static files (CSS, JavaScript, images)
├── templates/           # HTML templates
├── utils/               # Utility functions and helpers
├── views/               # View controllers and business logic
├── main.py              # Application entry point
├── config.toml          # Configuration file
├── requirements.txt     # Python dependencies
├── Dockerfile           # Docker container configuration
└── README-cloudshell.txt # Google Cloud Shell instructions
```

### Directory Details

- **models/**: Contains data model definitions, database schemas, and data validation logic
- **routers/**: HTTP route definitions and request handling
- **static/**: Client-side assets including stylesheets, JavaScript files, and media
- **templates/**: Jinja2 or similar template files for dynamic HTML rendering
- **utils/**: Helper functions, decorators, and shared utilities
- **views/**: View logic that connects routers to business logic
- **main.py**: The main application file that initializes and runs the web server

## Prerequisites

Before you begin, ensure you have the following installed:

- **Python 3.8+**: The application is built with Python
- **Google Cloud Account**: Required for GenAI API access
- **Google Cloud Project**: Set up a GCP project with billing enabled
- **Docker** (optional): For containerized deployment
- **Git**: For version control

### Google Cloud Setup

1. Create a Google Cloud project
2. Enable the Vertex AI API
3. Set up authentication credentials
4. Configure billing (required for GenAI APIs)

## Installation

### Local Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/LennyBeto/google-cloud-genai-website.git
   cd google-cloud-genai-website
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

### Docker Installation

```bash
docker build -t genai-website .
docker run -p 8080:8080 genai-website
```

## Configuration

### Environment Variables

Set the following environment variables for Google Cloud authentication:

```bash
export GOOGLE_CLOUD_PROJECT="your-project-id"
export GOOGLE_CLOUD_LOCATION="us-central1"  # or your preferred region
export GOOGLE_APPLICATION_CREDENTIALS="path/to/service-account-key.json"
```

### Configuration File

Edit `config.toml` to customize application settings:

```toml
[app]
name = "GenAI Website"
host = "0.0.0.0"
port = 8080

[genai]
model = "gemini-2.0-flash"
temperature = 0.7
max_tokens = 1024

[security]
cors_enabled = true
allowed_origins = ["*"]
```

### Google Cloud Shell Setup

If deploying to Google Cloud Shell, refer to `README-cloudshell.txt` for specific instructions.

##  Deployment

### Local Development Server

```bash
python main.py
```

The application will be available at `http://localhost:8080`

### Google Cloud Run

1. **Build the container**
   ```bash
   gcloud builds submit --tag gcr.io/PROJECT_ID/genai-website
   ```

2. **Deploy to Cloud Run**
   ```bash
   gcloud run deploy genai-website \
     --image gcr.io/PROJECT_ID/genai-website \
     --platform managed \
     --region us-central1 \
     --allow-unauthenticated
   ```

### Google App Engine

```bash
gcloud app deploy
```

### Google Compute Engine

1. Create a VM instance
2. SSH into the instance
3. Clone the repository
4. Run the Docker container or install dependencies locally

## Usage

### Basic Example

Once the application is running, you can interact with the GenAI features through the web interface or API endpoints.

### API Endpoints

The application likely exposes the following types of endpoints:

- `GET /` - Home page
- `POST /api/generate` - Generate AI content
- `POST /api/chat` - Chat with AI model
- `GET /api/health` - Health check endpoint

### Making Requests

```python
import requests

# Example: Generate content
response = requests.post(
    'http://localhost:8080/api/generate',
    json={
        'prompt': 'Write a short poem about AI',
        'max_tokens': 100
    }
)
print(response.json())
```

## Development

### Project Dependencies

Key dependencies likely include:

- **FastAPI** or **Flask**: Web framework
- **google-genai**: Google's GenAI SDK
- **google-cloud-aiplatform**: Vertex AI client library
- **Jinja2**: Template engine
- **uvicorn** or **gunicorn**: ASGI/WSGI server
- **pydantic**: Data validation

### Running Tests

```bash
pytest tests/
```

### Code Quality

```bash
# Format code
black .

# Lint code
pylint **/*.py

# Type checking
mypy .
```

### Adding New Features

1. Create models in `models/`
2. Define routes in `routers/`
3. Implement business logic in `views/`
4. Add utility functions to `utils/`
5. Create templates in `templates/`
6. Add static assets to `static/`

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Contribution Guidelines

- Follow PEP 8 style guidelines
- Add tests for new features
- Update documentation as needed
- Ensure all tests pass before submitting PR

##  License

This project is provided as-is for educational and demonstration purposes. Please check the repository for specific license information.

## Security

- Never commit API keys or credentials
- Use environment variables for sensitive data
- Follow Google Cloud security best practices
- Regularly update dependencies

## Support

For issues, questions, or contributions:

- Open an issue on GitHub
- Check Google Cloud documentation for GenAI
- Review Vertex AI best practices

## Acknowledgments

- Google Cloud Platform for GenAI services
- The Gemini AI model team
- Open source community contributors

## Additional Resources

- [Google GenAI SDK Documentation](https://googleapis.github.io/python-genai/)
- [Vertex AI Documentation](https://cloud.google.com/vertex-ai/docs)
- [Gemini API Guide](https://ai.google.dev/docs)
- [Google Cloud Run Documentation](https://cloud.google.com/run/docs)

---

**Note**: This project demonstrates GenAI integration with Google Cloud. Ensure you understand the pricing and usage limits of Google Cloud services before deploying to production.

For detailed deployment instructions specific to Google Cloud Shell, see `README-cloudshell.txt`.
