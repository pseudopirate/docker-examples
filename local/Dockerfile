FROM mhart/alpine-node:8.8.1

WORKDIR app
ADD package.json /app
ADD package-lock.json /app
ADD src /app/src
ADD public /app/public

RUN npm i

CMD ["npm", "start"]
