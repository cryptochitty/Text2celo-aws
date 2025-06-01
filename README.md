# Text2celo-aws
# Use Node.js LTS as the base image
FROM node:18-slim

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install --production

# Copy the rest of the code
COPY . .

# Expose port (change if your app uses a different port)
EXPOSE 3000

# Environment variables for AWS region and KMS key can be set at runtime
# Example:
# ENV AWS_REGION=us-east-1
# ENV KMS_KEY_ID=arn:aws:kms:us-east-1:123456789012:key/abcd-1234-efgh-5678-ijkl

# Start the Node.js server
CMD ["node", "server.js"]
