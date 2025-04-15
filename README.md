# Task-1 & 2
Minimalist Application Development / Docker / Kubernetes


#Step to run on cloud

1) Create a VM for practice, Install the docker from official documentation.

  https://docs.docker.com/engine/install/ubuntu/

2) Now Make Nord.js project as per requirement..

Phase 1: Develop SimpleTimeService App (Node.js)

✅ Step 1: Set up project folder

mkdir SimpleTimeService
cd SimpleTimeService
npm init -y

✅ Step 2: Install dependencies

npm install express

✅ Step 3: Create index.js file

const express = require('express');
const app = express();

app.get('/', (req, res) => {
    const timestamp = new Date().toISOString();
    const ip = req.headers['x-forwarded-for'] || req.connection.remoteAddress;
    res.json({ timestamp, ip });
});

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
    console.log(`SimpleTimeService running on port ${PORT}`);
});

  
 
📦 Phase 2: Dockerize the Application

✅ Step 4: Create a Dockerfile
Dockerfile

# Use minimal Node.js base image
FROM node:20-alpine

# Create app directory
WORKDIR /usr/src/app

# Copy package files and install
COPY package*.json ./
RUN npm install

# Copy the app code
COPY . .

# Create a non-root user and use it
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
USER appuser

# Expose the app port
EXPOSE 3000

# Run the app
CMD ["node", "index.js"]

✅ Step 5: Create .dockerignore

dockerignore

node_modules
npm-debug.log

🐳 Phase 3: Build & Run Docker Image

✅ Step 6: Build the image

docker build -t yourdockerhubusername/simpletimeservice .

✅ Step 7: Run the container

docker run -p 3000:3000 yourdockerhubusername/simpletimeservice

For Easy access you can use my final image.

docker pull dhruvchovatiya63907/simpletimeservice


#Task-2

You can run the 2 command once you are in the Terraform file.

1) terraform init
2) terraform plan
3) terraform apply
4) terraform destory
