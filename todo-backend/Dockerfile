FROM node:18.15-alpine
# Create App Directory
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app
# Install Dependencies
COPY package*.json ./
RUN npm install --silent
# Copy app source code
COPY . .
# Exports
EXPOSE 5000
# in case mongodb need credentials
ENV MONGODB_USERNAME=root
ENV MONGODB_PASSWORD=secret
# execute npm start to start application when the docker container runs
CMD ["npm","start"]


