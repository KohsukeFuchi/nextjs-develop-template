
FROM node:21-alpine

# Configure pnpm global

# ------- 環境変数設定 -------------
# ルートディレクトリの設定
ENV rootdir /home/web

WORKDIR ${rootdir}

RUN apk add bash

COPY ./container/package*.json ./
RUN npm install
