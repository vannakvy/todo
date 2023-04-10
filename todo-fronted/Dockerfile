
# FROM node:18.15.0 AS builder

# WORKDIR /app
# COPY package.json package-lock.json ./
# COPY public/ public/
# COPY src/ src/
# RUN npm ci
# RUN npm run build

# FROM nginx:latest
# COPY nginx/nginx.conf /etc/nginx/conf.d/default.conf
# COPY --from=builder /app/build /usr/share/nginx/html
# RUN touch /var/run/nginx.pid
# RUN chown -R nginx:nginx /var/run/nginx.pid /usr/share/nginx/html /var/cache/nginx /var/log/nginx /etc/nginx/conf.d
# USER nginx
# EXPOSE 3000
# CMD ["nginx", "-g", "daemon off;"]


FROM node:alpine as build
WORKDIR /app
COPY package*.json /app/
RUN npm install
COPY src/ src/
RUN npm run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx.html
RUN rm /etc/nginx/conf.d/default.conf
COPY nginx/nginx.conf /etc/nginx/conf.d
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]