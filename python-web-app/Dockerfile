# FROM ubuntu

# WORKDIR /app

# COPY requirements.txt /app
# COPY devops /app

# RUN apt-get update && \
#     apt-get install -y python3 python3-pip && \
#     pip install -r requirements.txt && \
#     cd devops

# ENTRYPOINT ["python3"]
# CMD ["manage.py", "runserver", "0.0.0.0:8000"]


FROM ubuntu

# Set the working directory
WORKDIR /app

# Copy the requirements and application files
COPY requirements.txt /app
COPY devops /app

# Install Python and the necessary tools to create a virtual environment
RUN apt-get update && \
    apt-get install -y python3 python3-venv python3-pip

# Create and activate a virtual environment
RUN python3 -m venv venv
ENV PATH="/app/venv/bin:$PATH"

# Install the Python dependencies within the virtual environment
RUN pip install --no-cache-dir -r requirements.txt

# Ensure the working directory is set to /app/devops
WORKDIR /app/devops

# Set the entry point and command to run the application
ENTRYPOINT ["python3"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]


