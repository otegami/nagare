FROM fluent/fluentd:v1.16.2-debian-arm64-1.0
USER root
RUN ["gem", "install", "fluent-plugin-s3", "--no-document", "--version", "1.7.2"]
USER fluent
