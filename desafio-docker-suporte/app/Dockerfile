FROM node:18-slim

WORKDIR /usr/src/app

RUN mysql -uroot -proot
RUN CREATE TABLE IF NOT EXISTS `characterSW`(`id` int NOT NULL AUTO_INCREMENT, `name` varchar(255) NOT NULL, PRIMARY KEY(`id`));

EXPOSE 3000

CMD ["npm", "run", "dev"]