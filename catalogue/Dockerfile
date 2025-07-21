FROM node:20-alpine3.21
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
WORKDIR /opt/server
COPY package.json .
COPY *.js .
RUN chown -R roboshop:roboshop /opt/server
RUN npm install
ENV MONGO_URL="mongodb://mongodb:27017/catalogue" \
    MONGO=true
USER roboshop
CMD ["node", "server.js"]
