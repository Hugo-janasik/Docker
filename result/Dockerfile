FROM node:10.0-alpine

RUN mkdir /app/
ADD . /app/
WORKDIR /app/

COPY package*.json /app/

RUN npm config set package-lock false
RUN npm install

ENV PORT=80
ENV HOST=db

CMD [ "npm", "start" ]