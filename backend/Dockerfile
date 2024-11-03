FROM node

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 80

ENV MONGODB_USERNAME=neeraj
ENV MONGODB_PASSWORD=raviteja

CMD [ "npm", "start" ]