ARG BUILD_FROM
FROM ${BUILD_FROM}

# Install additional dependencies if needed
RUN apk add --no-cache \
    bash \
    curl \
    docker-cli \
    docker-cli-compose \
    nodejs \
    npm \
    php82 \
    php82-phar \
    php82-mbstring \
    php82-openssl \
    php82-curl \
    php82-json \
    php82-pdo \
    php82-pdo_pgsql \
    php82-session \
    php82-tokenizer \
    php82-xml \
    php82-dom \
    php82-fileinfo \
    php82-ctype \
    php82-bcmath \
    postgresql \
    redis

# Copy root filesystem
COPY rootfs /

# Set permissions
RUN chmod a+x /etc/services.d/coolify/run \
    && chmod a+x /etc/services.d/coolify/finish

# Expose ports
EXPOSE 8000 6001 6002

# Labels
LABEL \
    io.hass.name="Coolify" \
    io.hass.description="Self-hosting with superpowers" \
    io.hass.arch="aarch64|amd64" \
    io.hass.type="addon" \
    io.hass.version="4.0.0"
