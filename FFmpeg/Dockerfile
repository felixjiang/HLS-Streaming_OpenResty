# Use an ARM64 Debian base image suitable for Raspberry Pi
FROM arm64v8/debian:bullseye-slim

# Set environment variables to avoid interactive prompts during package installation
ENV DEBIAN_FRONTEND=noninteractive

# Update package lists and install FFmpeg
RUN apt-get update && \
    apt-get install -y ffmpeg wget && \
    rm -rf /var/lib/apt/lists/*

# Set the working directory
WORKDIR /workspace

# Download the MP4 file using wget
RUN wget https://raw.githubusercontent.com/felixjiang/FFmpeg/main/file_example_MP4_1280_10MG.mp4

# Set the entrypoint to bash (optional)
ENTRYPOINT ["/bin/bash"]
