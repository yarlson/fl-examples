# Flask + FTL Example

This example demonstrates how to deploy a Flask application with PostgreSQL using FTL.

## Project Structure

```
.
├── Dockerfile         # Container configuration
├── README.md          # This file
├── app.py             # Flask application
├── ftl.yaml           # FTL deployment configuration
├── gunicorn.conf.py   # Gunicorn configuration
├── pyproject.toml     # Python project metadata
└── requirements.txt   # Python dependencies
```

## Configuration

The example uses the following environment variables:

```bash
# Required
SECRET_KEY=your-secret-key

# Optional (with defaults)
POSTGRES_USER=postgres
POSTGRES_PASSWORD=your-password
POSTGRES_DB=ftl_db
FLASK_ENV=production
```

## Local Development

1. Create `.env` file with required environment variables:

   ```bash
   SECRET_KEY=your-development-secret-key
   POSTGRES_PASSWORD=your-development-password
   ```

2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Run the application:
   ```bash
   flask run
   ```

## Deployment

1. Set up environment variables:

   ```bash
   export SECRET_KEY=your-production-secret-key
   export POSTGRES_PASSWORD=your-production-password
   ```

2. Update `project` and `servers` sections in `ftl.yaml`

3. Set up your server:

   ```bash
   ftl setup
   ```

4. Build Docker images:

   ```bash
   ftl build
   ```

5. Deploy:
   ```bash
   ftl deploy
   ```

## Features

- Flask web application with tasks API endpoint
- PostgreSQL database with secure authentication (SCRAM-SHA-256)
- Health check endpoint (/tasks)
- Environment variable configuration for all components
- Zero-downtime deployment with health checks
- Persistent PostgreSQL data using Docker volumes

## Configuration Details

### PostgreSQL

- Uses PostgreSQL 16 Alpine image
- Configured with SCRAM-SHA-256 authentication
