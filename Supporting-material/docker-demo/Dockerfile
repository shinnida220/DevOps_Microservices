FROM python:3.7.3-stretch

## Complete Step 1:
# Create a Working Directory
WORKDIR /app

## Complete Step 2:
# Copy source code to working directory
COPY . app.py /app/

## Complete Step 3:
# Install packages from requirements.txt
# hadolint ignore=DL3013
RUN pip install --upgrade --no-cache-dir pip && \
    pip install --no-cache-dir --trusted-host pypi.python.org -r requirements.txt

## Complete Step 4:
# Expose port 80

## Complete Step 5:
# Run app.py at container launch

# https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes#remove-all-images
# docker build -f Dockerfile -t ei-udacity:latest .
# docker rmi $(docker images -a -q) -> delete all docker images

# Pushing to ECR Ubuntu error
# docker login -u AWS -p $(aws ecr get-login-password --region the-region-you-are-in) xxxxxxxxx.dkr.ecr.the-region-you-are-in.amazonaws.com

# aws ecr get-login-password --region us-east-1 | docker login --username AWS -p $(aws ecr get-login-password --region us-east-1) 045643545213.dkr.ecr.us-east-1.amazonaws.com