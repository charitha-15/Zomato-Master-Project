FROM node:alpine

WORKDIR ~/app

COPY package*.json ./
RUN npm install
COPY . ./

RUN npm run build

FROM ngnix
EXPOSE 3000

COPY ./ngnix/default.conf /etc/ngnix/conf.d/default.conf

COPY --from=0 /app/build/ usr/share/ngnix/html