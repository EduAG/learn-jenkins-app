FROM mcr.microsoft.com/playwright:v1.39.0-jammy


LABEL maintainer="jesus.e.alvarez@gmail.com"
LABEL version="1.0"
LABEL description="Docker image for Playwright tests with Netlify CLI, node-jq, and serve"


# Install global npm packages
RUN npm install -g netlify-cli node-jq serve
RUN apt update && apt install jq -y

# Verify installation
RUN netlify --version && node-jq --version && serve --version
