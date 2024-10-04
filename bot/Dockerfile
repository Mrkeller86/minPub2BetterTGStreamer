# Use an official Python runtime as a parent image
FROM python:3.10

# Install FFmpeg and FFprobe
RUN apt-get update -qq && apt-get install -y ffmpeg

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt
RUN playwright install chromium --with-deps

# Set the working directory for the web app
WORKDIR /webapp

# Copy the web app's contents into the container at /webapp
COPY ./db /webapp

EXPOSE 8080
EXPOSE 5000

# Run your Python script
#CMD ["python", "main.py"]
#try this ny ai which is already running the bot and webapp
CMD ["sh", "-c", "python3 /app/main.py & gunicorn --bind 0.0.0.0:5000 main:app"]
#CMD python3 main.py & gunicorn main:app
