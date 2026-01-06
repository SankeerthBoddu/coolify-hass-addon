ARG BUILD_FROM
FROM ghcr.io/coollabsio/coolify:latest

# Install additional dependencies if needed
RUN apk add --no-cache \
    bash \
    curl \
    docker-cli \
    docker-cli-compose

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
