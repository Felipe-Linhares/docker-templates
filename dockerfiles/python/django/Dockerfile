# Pull base image
FROM python:latest

# Set environment variables
ENV PIP_DISABLE_PIP_VERSION_CHECK=1
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# Install dependencies, including Xvfb for a virtual display
RUN apt-get update && apt-get install -y

# Set work directory
WORKDIR /app

# Copy requirements.txt
COPY ./requirements.txt .

# Install Python dependencies
RUN pip install -r requirements.txt

# Copy the rest of the project
COPY . .

# Run migrations, load fixtures and start the server with Xvfb
CMD sh -c "python manage.py migrate && python manage.py loadfixtures && python manage.py runserver 0.0.0.0:8001"