# LLM Chat Backend

A FastAPI-based backend service designed for AI and machine learning applications, providing RESTful APIs for chat and prediction functionalities.

## Features

- **FastAPI Framework**: High-performance, async-ready web framework
- **AI-Ready Architecture**: Structured for easy integration with ML models
- **Automatic API Documentation**: Interactive Swagger UI and ReDoc
- **Type Safety**: Full type hints with Pydantic models
- **Modular Design**: Clean separation of concerns with organized directory structure

## Project Structure

```
llm-chat-backend/
├── app/
│   ├── __init__.py
│   ├── main.py              # FastAPI application entry point
│   ├── models/              # Database models and Pydantic schemas
│   ├── routes/              # API route handlers
│   ├── services/            # Business logic and AI model integrations
│   └── utils/               # Utility functions and helpers
├── venv/                    # Virtual environment
├── requirements.txt         # Python dependencies
├── Dockerfile              # Docker configuration
├── .gitignore              # Git ignore rules
└── README.md               # This file
```

## Prerequisites

- Python 3.8+
- pip (Python package installer)
- Docker (optional, for containerized deployment)

## Installation

### Local Development

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd llm-chat-backend
   ```

2. **Create and activate virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the application**
   ```bash
   uvicorn app.main:app --reload
   ```

### Docker Deployment

1. **Build the Docker image**
   ```bash
   docker build -t llm-chat-backend .
   ```

2. **Run the container**
   ```bash
   docker run -p 8000:8000 llm-chat-backend
   ```

## Usage

Once the server is running, you can access:

- **API Endpoint**: http://localhost:8000
- **Interactive API Documentation**: http://localhost:8000/docs
- **Alternative API Documentation**: http://localhost:8000/redoc

### Example API Calls

**Basic Health Check**
```bash
curl http://localhost:8000/
```

**Response:**
```json
{
  "message": "Hello World"
}
```

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET    | `/`      | Health check endpoint |
| POST   | `/predict` | AI prediction endpoint (to be implemented) |

## Development

### Adding New Features

1. **Routes**: Add new API endpoints in `app/routes/`
2. **Models**: Define data models in `app/models/`
3. **Services**: Implement business logic in `app/services/`
4. **Utils**: Add utility functions in `app/utils/`

### Code Style

- Follow PEP 8 guidelines
- Use type hints for all functions
- Document functions with docstrings
- Keep functions focused and modular

### Testing

```bash
# Install test dependencies
pip install pytest pytest-asyncio httpx

# Run tests
pytest tests/
```

## Environment Variables

Create a `.env` file in the root directory:

```env
# Database
DATABASE_URL=postgresql://username:password@localhost/dbname

# Security
SECRET_KEY=your-secret-key-here

# Application
DEBUG=True
HOST=0.0.0.0
PORT=8000

# AI Models
MODEL_PATH=/path/to/your/models
```

## Deployment

### Production Considerations

1. **Environment Variables**: Set production environment variables
2. **Database**: Configure production database connection
3. **Security**: Use HTTPS and proper authentication
4. **Logging**: Implement comprehensive logging
5. **Monitoring**: Set up health checks and monitoring

### Docker Compose (Optional)

```yaml
version: '3.8'
services:
  app:
    build: .
    ports:
      - "8000:8000"
    environment:
      - DATABASE_URL=postgresql://user:pass@db:5432/dbname
    depends_on:
      - db
  
  db:
    image: postgres:13
    environment:
      - POSTGRES_USER=user
      - POSTGRES_PASSWORD=pass
      - POSTGRES_DB=dbname
```

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For support and questions:
- Create an issue in the GitHub repository
- Contact the development team

## Changelog

### v1.0.0
- Initial FastAPI setup
- Basic project structure
- Docker support
- API documentation