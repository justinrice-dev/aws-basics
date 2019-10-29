FROM mhart/alpine-node:10
EXPOSE 4000

RUN apk add --no-cache curl

WORKDIR /app

ARG YARNRC
ARG NPMRC

RUN echo "$YARNRC" >.yarnrc
RUN echo "$NPMRC" >.npmrc

COPY package.json yarn.lock ./
RUN yarn install --use-yarnrc .yarnrc --frozen-lockfile

RUN rm -f .yarnrc .npmrc

COPY . .

VOLUME ["/conf.d", "/mnt/logs"]

CMD ["./start.sh"]