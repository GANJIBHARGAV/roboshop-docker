FROM node:20-alpine3.21 AS builder
WORKDIR /opt/server
COPY package.json .
COPY *.server.js .
RUN npm install

FROM node:20-alpine3.21
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop 
ENV MONGO="true"\
    MONGO_URL="mongodb://mongodb:27017/catalogue"
WORKDIR /opt/server
USER roboshop
COPY --from=builder  /opt/server /opt/server/
CMD ["node" , "server.js"]  



# RUN addgroup -S roboshop && adduser -S roboshop -G roboshop 
# #We are creating system user with name roboshop and system group name with roboshop
# WORKDIR /opt/server
# RUN chown -R roboshop:roboshop /opt/server
# # we are changing our ownership and giving ownership to roboshop from /opt/server
# COPY package.json .
# COPY *.js .
# RUN npm install
# ENV MONGO="true"\
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["node" , "server.js"]    
