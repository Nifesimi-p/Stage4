# Use an official Python image as the base
FROM python:3.9-slim

# Set the working directory inside the container
WORKDIR /app

# Copy requirements file and install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the application code into the container
COPY . .

# Expose any required ports (if applicable)
EXPOSE 5000  # Change this if your app uses a different port

# Define the default command to run the application
CMD ["python", "main.py"]
