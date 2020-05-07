FROM php:7.2-cli

RUN mkdir /app \
    && echo "Hello from Dockerfile (index.html)" > /app/index.html

CMD ["php", "-S", "0.0.0.0:8000", "-t", "/app"]
