FROM nginx/unit:1.17.0-minimal

ADD unit.conf.json /var/lib/unit/conf.json

RUN mkdir -p /var/lib/unit/certs \
    && mkdir -p /var/run/unit && chmod go+wrX /var/run/unit \
    \
    && mkdir /app \
    && echo "Hello from Dockerfile (index.html)" > /app/index.html

EXPOSE 8000

STOPSIGNAL SIGTERM

CMD ["unitd", \
    "--no-daemon", \
    "--log",        "/dev/stdout", \
    "--pid",        "/var/run/unit/unit.pid", \
    "--control",    "unix:/var/run/unit/control.unit.sock" \
]
