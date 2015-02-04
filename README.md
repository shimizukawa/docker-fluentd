# Docker fluentd

Docker image with:

- [fluentd](http://www.fluentd.org/)
- fluent-plugin-elasticsearch
- fluent-plugin-record-modifier
- fluent-plugin-exclude-filter

which do nothing by default.

Elasticsearch info is controlled by `ES_HOST` and `ES_PORT` variables which will be overwritten if you link `elastic` search container.

Fluentd config is created using `/app/config/fluentd.conf.erb` template and could be easily overwritten in custom Dockerfile:

`ADD my-custom-fluentd-template.erb /app/config/fluentd.conf.erb`

If you want to override it dynamicaly, you can use volume for it.

`-v /path/to/fluentdconfdir:/etc/fluentd`

# Simple usage

`docker run -d -v /path/to/fluentdconfdir:/etc/fluentd shimizukawa/td-agent`

