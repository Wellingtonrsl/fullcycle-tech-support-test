FROM node:18-slim

USER node

RUN mysql -uroot -proot \
    CREATE TABLE IF NOT EXISTS `people`(`id` int NOT NULL AUTO_INCREMENT, `name` varchar(255) NOT NULL, PRIMARY KEY(`id`));

WORKDIR /usr/src/app

EXPOSE 3000