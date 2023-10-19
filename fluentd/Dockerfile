FROM fluent/fluentd:v1.16.2-debian-arm64-1.0

# Switch to root to install required libraries and gems
USER root

# Install necessary utilities and set up Apache Arrow and Apache Parquet repositories
RUN apt update && \
    apt install -y -V ca-certificates lsb-release wget build-essential libglib2.0-dev && \
    wget https://apache.jfrog.io/artifactory/arrow/$(lsb_release --id --short | tr 'A-Z' 'a-z')/apache-arrow-apt-source-latest-$(lsb_release --codename --short).deb && \
    apt install -y -V ./apache-arrow-apt-source-latest-$(lsb_release --codename --short).deb && \
    apt update

# Install Apache Arrow GLib and Apache Parquet GLib and related packages
RUN apt install -y -V \
    libarrow-dev \
    libarrow-glib-dev \
    libparquet-dev \
    libparquet-glib-dev

# Install required Fluentd plugins
RUN gem install red-arrow --no-document && \
    gem install red-parquet --no-document && \
    gem install fluent-plugin-s3 --no-document && \
    gem install fluent-plugin-s3-arrow --no-document

# Switch back to fluent user
USER fluent
