# syntax=docker/dockerfile:1
FROM python:3.8
ENV CRYPTOGRAPHY_DONT_BUILD_RUST=1

# DEBUG, INFO, WARNING, ERROR
ENV LOGGING_LEVEL='INFO'
# PKI server and port in ATOS premises
ENV PKI_SERVER_HOST='http://37.48.101.249'
ENV PKI_SERVER_PORT='8880'

# MQTT broker and port
ENV MQTT_BROKER_HOST='broker'
ENV MQTT_BROKER_PORT='1883'

RUN mkdir /in
COPY dist.tar.gz /in/
RUN cd /in && tar -xzvf dist.tar.gz && mv /in/build/dist/* /run/

WORKDIR /run
RUN pip3 install --upgrade pip
RUN pip3 install -r requirements.txt

CMD [ "python3", "/run/main_mqtt.py"]
