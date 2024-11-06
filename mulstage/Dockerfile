# First Stage: Build
FROM ubuntu:latest as build

# Set the working directory in the image
WORKDIR /app

# Copy the files from the host file system to the image file system
COPY . /app

# Install the necessary packages
RUN apt-get update && \
    apt-get install -y python3 python3-pip 
# Second Stage: Distroless
FROM gcr.io/distroless/python3-debian10

# Set the working directory
WORKDIR /app

# Copy the necessary files from the build stage
COPY --from=build /app /app

# Set environment variables
ENV NAME World

# Expose port if required by the app
#EXPOSE 8080  # Replace with actual port if needed

# Run the Python application
CMD ["app.py"]

