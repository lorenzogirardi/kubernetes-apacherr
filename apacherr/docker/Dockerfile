FROM httpd:2.4.66
COPY ./index.html /usr/local/apache2/htdocs/
RUN mkdir -p /usr/local/apache2/conf/custom/
COPY ./httpd.conf /usr/local/apache2/conf/httpd.conf
RUN chmod +r /usr/local/apache2/htdocs/index.html

# Install mod_datadog for APM tracing (x86_64 only, skip on arm64)
ARG TARGETARCH
RUN if [ "$TARGETARCH" = "amd64" ]; then \
      apt-get update && apt-get install -y --no-install-recommends \
        curl unzip ca-certificates \
      && curl -L -o /tmp/mod_datadog.zip \
         https://github.com/DataDog/httpd-datadog/releases/download/v1.0.3/mod_datadog_artifact.zip \
      && unzip /tmp/mod_datadog.zip -d /tmp/mod_datadog \
      && cp /tmp/mod_datadog/mod_datadog.so /usr/local/apache2/modules/mod_datadog.so \
      && chmod 755 /usr/local/apache2/modules/mod_datadog.so \
      && rm -rf /tmp/mod_datadog /tmp/mod_datadog.zip \
      && apt-get purge -y curl unzip \
      && apt-get autoremove -y \
      && rm -rf /var/lib/apt/lists/* ; \
    else \
      echo "mod_datadog not available for $TARGETARCH, skipping" \
      && sed -i 's/^LoadModule datadog_module/#LoadModule datadog_module/' \
         /usr/local/apache2/conf/httpd.conf ; \
    fi
