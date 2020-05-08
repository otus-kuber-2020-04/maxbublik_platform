FROM nginx/unit:1.17.0-minimal

RUN printf '\
        {                                                           \n\
            "listeners": {                                          \n\
                "*:8000": {                                         \n\
                    "pass": "routes"                                \n\
                }                                                   \n\
            },                                                      \n\
            "routes": [                                             \n\
                {                                                   \n\
                    "action": {                                     \n\
                        "share": "/app"                             \n\
                    }                                               \n\
                }                                                   \n\
            ]                                                       \n\
        }                                                           \n\
    ' > /var/lib/unit/conf.json \
    && mkdir -p /var/lib/unit/certs \
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
