FROM rabbitmq:4.0.2-management

COPY ./rabbitmq.conf /etc/rabbitmq/rabbitmq.conf
COPY ./definitions.json /etc/rabbitmq/definitions.json
COPY ./enabled_plugins /etc/rabbitmq/enabled_plugins
COPY ./rabbitmq_delayed_message_exchange-3.13.0.ez /plugins/rabbitmq_delayed_message_exchange-3.13.0.ez
