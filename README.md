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

`docker run -d -v /path/to/fluentdconfdir:/etc/fluentd shimizukawa/fluentd`


# settings

PATH

- `/app/bin/start`: fluentd bootstrapping bash script
- `/app/config/fluentd.conf.erb`: template for /etc/fluentd/fluentd.conf
- `/etc/fluentd/fluentd.conf`: fluentd config file that will be genrated by /app/bin/start
- `/var/log/fluentd/`: fluentd log directory

ENVIRONMENT

- `ES_HOST`: elasticsearch host
- `ES_PORT`: elasticsearch port
- `ELASTICSEARCH_PORT_9200_TCP_ADDR`: will be assinged to `ES_HOST` if `ES_HOST` is not provided.
- `ELASTICSEARCH_PORT_9200_TCP_PORT`: will be assigned to `ES_PORT` if `ES_PORT` is not provided.

fluentd.conf.erb

- see: [fluentd.conf.erb](https://github.com/shimizukawa/docker-fluentd/blob/master/config/fluentd.conf.erb)

