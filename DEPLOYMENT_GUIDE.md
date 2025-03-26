# Veltis Platform Deployment Guide

This guide provides detailed instructions for deploying the Veltis platform, including smart contracts, backend, and frontend components.

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Repository Structure](#repository-structure)
3. [Smart Contract Deployment](#smart-contract-deployment)
4. [Backend Deployment](#backend-deployment)
5. [Frontend Deployment](#frontend-deployment)
6. [Troubleshooting](#troubleshooting)

## Prerequisites

Before starting the deployment process, ensure you have the following:

- Node.js (v16 or v18 recommended, v20+ requires compatibility fix)
- npm (v8 or higher)
- Git
- Vercel account
- Alchemy account (for Polygon Amoy RPC access)
- MetaMask wallet with Polygon Amoy testnet MATIC
- PolygonScan API key (for contract verification)

## Repository Structure

The Veltis platform consists of three main components:

```
organized/
├── veltis-contracts/    # Smart contracts
├── veltis-backend/      # Next.js backend API
└── veltis-frontend/     # Vite React frontend
```

## Smart Contract Deployment

### 1. Node.js Compatibility

If you're using Node.js v20+, you may encounter compatibility issues with Hardhat. Run the provided fix script before proceeding:

```bash
./fix-hardhat.sh
```

This script will fix the `Cannot find module './is-node-version-to-warn-on'` error that occurs with newer Node.js versions.

### 2. Configure Environment Variables

Create a `.env` file in the `veltis-contracts` directory with the following variables:

```
ALCHEMY_API_KEY=your_alchemy_api_key
PRIVATE_KEY=your_wallet_private_key
POLYGONSCAN_API_KEY=your_polygonscan_api_key
```

### 3. Compile and Deploy Contracts

Run the following commands to compile and deploy the smart contracts:

```bash
cd organized/veltis-contracts
npm install
node compile-contracts.js
node deploy-contracts.js
```

The deployment script will:
- Deploy the IPNFTRegistry, SimpleIPNFTRegistry, FractionalizationFactory, and Marketplace contracts
- Save deployment information to `deployment-info.json`
- Create a `.env.vercel` file with contract addresses for Vercel deployment

## Backend Deployment

### 1. Deploy to Vercel

Use the provided deployment script to deploy the backend to Vercel:

```bash
./deploy-backend-fixed.sh
```

This script will:
- Install the Vercel CLI if not already installed
- Configure the backend for deployment
- Create necessary configuration files
- Deploy the backend to Vercel

### 2. Note the Backend URL

After deployment, note the backend URL (e.g., `https://veltis-backend.vercel.app`). You'll need this for the frontend deployment.

## Frontend Deployment

### 1. Deploy to Vercel

Use the provided deployment script to deploy the frontend to Vercel:

```bash
./deploy-frontend-fixed.sh
```

When prompted, enter the backend URL from the previous step.

This script will:
- Install the Vercel CLI if not already installed
- Configure the frontend with the correct API URL and environment variables
- Create necessary configuration files
- Deploy the frontend to Vercel

## Troubleshooting

### Common Issues and Solutions

#### 1. Hardhat Compatibility with Node.js v20+

If you encounter the error `Cannot find module './is-node-version-to-warn-on'` when running Hardhat commands, use the provided fix script:

```bash
./fix-hardhat.sh
```

Alternatively, you can use nvm to switch to Node.js v18:

```bash
nvm install 18
nvm use 18
```

#### 2. Dependency Conflicts

If you encounter dependency conflicts during deployment, try the following:

```bash
# For backend
cd organized/veltis-backend
npm install --legacy-peer-deps

# For frontend
cd organized/veltis-frontend
npm install --force
```

#### 3. Build Errors

If you encounter build errors, check the following:

- Ensure all environment variables are correctly set
- Check for syntax errors in your code
- Verify that all dependencies are installed

#### 4. Smart Contract Deployment Failures

If smart contract deployment fails:

- Ensure your wallet has sufficient MATIC for gas fees
- Verify that your private key is correct
- Check the Hardhat configuration for any issues

#### 5. Vercel Deployment Issues

If Vercel deployment fails:

- Check the Vercel logs for specific error messages
- Ensure your Vercel account has the necessary permissions
- Verify that all environment variables are correctly set in Vercel

### Getting Help

If you continue to experience issues, please:

1. Check the error logs for specific error messages
2. Consult the documentation for each component
3. Reach out to the Veltis support team for assistance

## Complete Deployment

For a streamlined deployment process that handles all components at once, use the master deployment script:

```bash
./deploy-all.sh
```

This script will:
1. Deploy smart contracts to the Polygon Amoy testnet
2. Deploy the backend to Vercel
3. Deploy the frontend to Vercel
4. Configure all necessary environment variables

## Conclusion

By following this guide, you should have successfully deployed the Veltis platform, including smart contracts, backend, and frontend components. If you encounter any issues not covered in the troubleshooting section, please refer to the specific documentation for each component or contact support.

Happy deploying! 