FROM node:16-alpine as builder 

WORKDIR '/app'
COPY ./package.json .

RUN npm isntall 
COPY . .

RUN nmp run build

# second phase:
FROM nginx 
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html

