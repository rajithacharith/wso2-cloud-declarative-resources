# WSO2 Cloud Immutable Resources - Thunder Setup Guide

This guide walks you through setting up and running the Thunder WSO2 Cloud use case with immutable resources.

## Prerequisites

- macOS/Linux environment
- Git installed
- Node.js and npm installed (for React sample app)

## Setup Instructions

### Step 01: Download Thunder

Download the latest Thunder release (v0.18.0):

```bash
cd ~/Downloads
curl -LO https://github.com/asgardeo/thunder/releases/download/v0.18.0/thunder-0.18.0-macos-arm64.zip
```

### Step 02: Download Sample App React SDK

Download the React SDK sample application:

```bash
curl -LO https://github.com/asgardeo/thunder/releases/download/v0.18.0/sample-app-react-sdk-0.18.0-macos-arm64.zip
```

### Step 03: Extract Thunder

Extract the Thunder zip file:

```bash
unzip thunder-0.18.0-macos-arm64.zip
cd thunder-0.18.0-macos-arm64
```

### Step 04: Clone Immutable Resources

Clone this repository content to Thunder's resources directory:

```bash
git clone https://github.com/rajithacharith/wso2-cloud-immutable-resources.git temp-repo
cp -r temp-repo/* repository/resources/
rm -rf temp-repo
```

Alternatively, if you already have this repository locally:

```bash
cp -r /path/to/this/repo/* repository/resources/
```

### Step 05: Configure Deployment

Add the following configuration to `repository/conf/deployment.yaml`:

```yaml
immutable_resources:
  enabled: true

organization_unit:
  store: "composite"
```

**Command to append to deployment.yaml:**

```bash
cat >> repository/conf/deployment.yaml << 'EOF'

immutable_resources:
  enabled: true

organization_unit:
  store: "composite"
EOF
```

### Step 06: Export Environment Variables

Contact **@rajithacharith** for the exact environment variable values, then export them:

```bash
export ENV_VAR_NAME_1="value1"
export ENV_VAR_NAME_2="value2"
# Add all required environment variables as provided
```

Or if you have an `.env` file:

```bash
source /path/to/your/.env
```

### Step 07: Start Thunder

Run Thunder:

```bash
./start.sh
```

Wait for Thunder to start completely. You should see logs indicating the server is ready.

### Step 08: Setup React Sample App

In a new terminal window, extract and setup the React sample app:

```bash
cd ~/Downloads
unzip sample-app-react-sdk-0.18.0-macos-arm64.zip
cd sample-app-react-sdk-0.18.0-macos-arm64
```

### Step 09: Run Sample App

Start the React application:

```bash
./start.sh
```

Or if using npm directly:

```bash
npm install
npm start
```

### Step 10: Access the Application

Open your browser and visit:

```
https://localhost:3000
```

## Quick Command Reference

```bash
# Complete setup (one-liner style)
cd ~/Downloads && \
curl -LO https://github.com/asgardeo/thunder/releases/download/v0.18.0/thunder-0.18.0-macos-arm64.zip && \
curl -LO https://github.com/asgardeo/thunder/releases/download/v0.18.0/sample-app-react-sdk-0.18.0-macos-arm64.zip && \
unzip thunder-0.18.0-macos-arm64.zip && \
cd thunder-0.18.0-macos-arm64 && \
git clone https://github.com/rajithacharith/wso2-cloud-immutable-resources.git temp-repo && \
cp -r temp-repo/* repository/resources/ && \
rm -rf temp-repo && \
cat >> repository/conf/deployment.yaml << 'EOF'

immutable_resources:
  enabled: true

organization_unit:
  store: "composite"
EOF
```

Then in separate terminals:

```bash
# Terminal 1: Start Thunder
cd ~/Downloads/thunder-0.18.0-macos-arm64
source /path/to/your/.env  # Set your environment variables
./start.sh
```

```bash
# Terminal 2: Start React App
cd ~/Downloads
unzip sample-app-react-sdk-0.18.0-macos-arm64.zip
cd sample-app-react-sdk-0.18.0-macos-arm64
./start.sh
```

## Troubleshooting

- **Port conflicts**: Ensure ports 3000 (React app) and Thunder's default ports are available
- **Environment variables**: Double-check all required env vars are set before starting Thunder
- **Permissions**: If you encounter permission issues, run `chmod +x start.sh` in the respective directories

## Repository Structure

This repository contains immutable resources for WSO2 Cloud:

- `applications/` - Application configurations
- `flows/` - Authentication flows
- `identity_providers/` - Identity provider configurations
- `organization_units/` - Organization unit definitions
- `user_schemas/` - User schema definitions

## Contact

For environment variable values or additional support, contact **@rajithacharith**.
