# Use Ubuntu base image
FROM ubuntu:latest
RUN useradd -ms /bin/bash docker && echo "docker:docker" | chpasswd && adduser docker sudo


# Install Python 3.10 and pip
RUN apt-get update && \
    apt-get install -y python3.10 curl && \
    curl -sS https://bootstrap.pypa.io/get-pip.py | python3.10

# Install Node.js and npm
RUN curl -sL https://deb.nodesource.com/setup_16.x | bash - && \
    apt-get install -y nodejs
RUN apt-get update && apt-get install -y pkg-config libcairo2-dev libgdk-pixbuf2.0-dev libpango1.0-dev

RUN apt-get update && apt-get install -y gcc python3-dev pkg-config libpangocairo-1.0-0
# Copy the project files to the container
ENV PKG_CONFIG_PATH=/usr/lib/pkgconfig:/usr/local/lib/pkgconfig

WORKDIR /app
COPY . .

# Install Python dependencies
RUN pip3.10 install -r requirements.txt

# Define a command to run the application
CMD [ "python3.10", "main.py" ]
