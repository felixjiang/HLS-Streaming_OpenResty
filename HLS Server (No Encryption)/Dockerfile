# Use the OpenResty Bullseye base image suitable for Raspberry Pi 4
FROM openresty/openresty:bullseye-fat

# Install necessary build dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    libpcre3-dev \
    libssl-dev \
    zlib1g-dev \
    wget \
    git \
    ca-certificates

# Set the OpenResty version
ENV OPENRESTY_VERSION=1.25.3.2

# Set the working directory
WORKDIR /tmp

# Download OpenResty source code
RUN wget https://openresty.org/download/openresty-${OPENRESTY_VERSION}.tar.gz && \
    tar -zxvf openresty-${OPENRESTY_VERSION}.tar.gz

# Clone the nginx-rtmp-module repository
RUN git clone https://github.com/arut/nginx-rtmp-module.git

# Configure and compile OpenResty with the nginx-rtmp-module
RUN cd openresty-${OPENRESTY_VERSION} && \
    ./configure --prefix=/usr/local/openresty \
                --add-module=../nginx-rtmp-module \
                --with-pcre-jit \
                --with-ipv6 \
                --with-http_ssl_module \
                --with-http_realip_module \
                --with-http_addition_module \
                --with-http_sub_module \
                --with-http_dav_module \
                --with-http_flv_module \
                --with-http_mp4_module \
                --with-http_gunzip_module \
                --with-http_gzip_static_module \
                --with-http_random_index_module \
                --with-http_secure_link_module \
                --with-http_stub_status_module && \
    make && \
    make install

# Clean up temporary files
RUN rm -rf /tmp/*

# Copy the custom nginx configuration file
COPY nginx.conf /usr/local/openresty/nginx/conf/nginx.conf

# Expose ports for HTTP, HTTPS, and RTMP
EXPOSE 80 443 1935

# Start NGINX
CMD ["/usr/local/openresty/bin/openresty", "-g", "daemon off;"]
