FROM %%BASE_IMAGE%%

ENV LANG C.UTF-8

RUN apk add --no-cache jq nodejs nodejs-npm \ 
	&& npm config set unsafe-perm true \
	&& npm install -g smartthings-mqtt-bridge@2.1.0 mustache \
	&& npm config set unsafe-perm false

COPY template.yml /templates/
COPY run.sh /
RUN chmod a+x /run.sh

# We need to percist state, so using data
ENV CONFIG_DIR=/data

CMD [ "/run.sh" ]
