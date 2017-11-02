FROM node:alpine

RUN \
npm install -g reveal-md && \
apk add --no-cache fontconfig bash && \
apk add --no-cache --virtual=.build-deps curl && \
curl -Ls https://github.com/fgrehm/docker-phantomjs2/releases/download/v2.0.0-20150722/dockerized-phantomjs.tar.gz | tar xz -C / && \
apk del .build-deps

ADD public/fonts/* /usr/share/fonts/truetype/sourcesanspro/

WORKDIR /slides

EXPOSE 1948
ENTRYPOINT []
CMD ["reveal-md", "slides.md"]
