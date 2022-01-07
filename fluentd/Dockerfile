# fluentd/Dockerfile

#FROM fluent/fluentd:v1.12.0-debian-1.0
FROM fluent/fluentd:v1.14-debian-1
USER root
#RUN echo "gem version" && gem --version
RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak 
COPY sources.list /etc/apt/sources.list
RUN cat /etc/apt/sources.list
#RUN echo "ruby version" && ruby --version
RUN apt-get update && apt-get install -y make gcc g++  ruby-dev
RUN ["gem", "install", "fluent-plugin-elasticsearch", "--no-document", "--version", "5.1.4"]
RUN ["gem", "install", "fluent-plugin-multi-format-parser", "--no-document","--version","1.0.0"]
RUN ["gem", "install", "fluent-plugin-kubernetes_metadata_filter", "--no-document","--version","2.9.0"]
RUN ["gem", "install", "fluent-plugin-concat", "--no-document","--version","2.5.0"]
RUN ["gem", "install", "fluent-plugin-detect-exceptions", "--no-document","--version","0.0.14"]
RUN chmod oug+r /usr/local/bundle/gems/fluent-plugin-multi-format-parser-1.0.0/lib/fluent/plugin/*.rb && \
    chmod oug+r /usr/local/bundle/gems/fluent-plugin-kubernetes_metadata_filter-2.9.0/lib/fluent/plugin/*.rb && \
    chmod oug+r /usr/local/bundle/gems/fluent-plugin-concat-2.5.0/lib/fluent/plugin/*.rb && \
    chmod oug+r /usr/local/bundle/gems/fluent-plugin-detect-exceptions-0.0.14/lib/fluent/plugin/*.rb && \
    mkdir /var/log/fluentd-buffers && chmod 777 /var/log/fluentd-buffers
#USER fluent
