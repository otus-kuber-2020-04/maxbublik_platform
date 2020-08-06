FROM nginx/unit:1.18.0-minimal

# Чтобы увидеть запущенные процессы, выполнить команду `kubectl exec web -- busybox ps`
COPY --from=busybox:1.28 /bin/busybox /bin/busybox

ADD unit.conf.json /var/lib/unit/conf.json

RUN mkdir /app \
    && echo "Hello from Dockerfile (index.html)" > /app/index.html

RUN useradd --no-create-home --no-log-init --uid 1001 appuser \
    && mkdir -p /var/lib/unit/certs     && chown -R appuser /var/lib/unit \
    && mkdir -p /var/run/unit           && chown -R appuser /var/run/unit

USER appuser

EXPOSE 8000

STOPSIGNAL SIGTERM

CMD ["unitd", \
    "--no-daemon", \
    "--log",        "/dev/stdout", \
    "--pid",        "/var/run/unit/unit.pid", \
    "--control",    "unix:/var/run/unit/control.unit.sock" \
]
