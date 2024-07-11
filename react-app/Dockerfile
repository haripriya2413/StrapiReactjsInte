# Use an official node image as the base image
FROM node:18 AS build 
# Set the working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json package-lock.json ./

# Install the dependencies
RUN npm install

# Copy the rest of the application code to the working directory
COPY . .

# Build the React application
RUN npm run build


FROM nginx:alpine 

COPY --from=build /app/build /usr/share/nginx/html 

EXPOSE 80 

CMD ["nginx", "-g", "daemon off;"] 