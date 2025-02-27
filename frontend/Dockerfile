# Use the official Node.js 14 image as the base image
FROM node:14

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code to the working directory
COPY . .

# Install dotenv package to load environment variables
RUN npm install dotenv

# Expose the port the application will run on
EXPOSE 8080

# Set environment variables (these can be overridden at runtime)
ENV PORT=8080
ENV AUTH_API_ADDRESS=${AUTH_API_ADDRESS}
ENV TODOS_API_ADDRESS=${TODOS_API_ADDRESS}

# Build the application
RUN npm run build

# Command to run the application
CMD ["npm", "run", "dev"]