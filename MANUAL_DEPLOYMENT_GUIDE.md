# Veltis Platform Manual Deployment Guide

This guide provides step-by-step instructions for deploying the Veltis platform to Vercel. It covers both the backend and frontend deployment processes.

## Prerequisites

Before you begin, ensure you have:

- A Vercel account (sign up at [vercel.com](https://vercel.com))
- Access to the Veltis GitHub repositories:
  - Backend: [https://github.com/Veltiscapital/veltis-backend](https://github.com/Veltiscapital/veltis-backend)
  - Frontend: [https://github.com/Veltiscapital/veltis-frontend](https://github.com/Veltiscapital/veltis-frontend)
- An Alchemy API key for Polygon Amoy testnet
- A MetaMask wallet with testnet MATIC
- Node.js and npm installed locally

## Step 1: Deploy the Backend

### Option 1: Deploy from the `vercel-deployment` Branch

We've created a special branch in the backend repository that's optimized for Vercel deployment:

1. Go to [Vercel Dashboard](https://vercel.com/dashboard)
2. Click "Add New" → "Project"
3. Import the `veltis-backend` repository
4. In the configuration screen:
   - Select the `vercel-deployment` branch
   - Framework Preset: Next.js
   - Root Directory: ./
   - Build Command: (leave as default)
   - Output Directory: (leave as default)

5. Configure the following environment variables:
   ```
   NODE_ENV=production
   NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
   CLERK_SECRET_KEY=your_clerk_secret_key
   NEXT_PUBLIC_BLOCKCHAIN_NETWORK=polygon-amoy
   NEXT_PUBLIC_IP_NFT_REGISTRY_CONTRACT=0x...
   NEXT_PUBLIC_SIMPLE_IP_NFT_REGISTRY_CONTRACT=0x...
   NEXT_PUBLIC_POLYGON_AMOY_RPC_URL=https://polygon-amoy.g.alchemy.com/v2/your_alchemy_key
   NEXT_PUBLIC_CHAIN_ID=80002
   NEXT_PUBLIC_NETWORK_NAME=Polygon Amoy
   NEXT_PUBLIC_FRACTIONALIZATION_FACTORY_CONTRACT=0x...
   ```

6. Click "Deploy"

### Option 2: Deploy from Main Branch

If you prefer to deploy from the main branch:

1. Follow steps 1-3 from Option 1
2. In the configuration screen:
   - Select the `main` branch
   - Framework Preset: Next.js
   - Root Directory: ./
   - Build Command: `npm run build`
   - Output Directory: `.next`

3. Configure the environment variables as in Option 1
4. Click "Deploy"

### Troubleshooting Backend Deployment

If you encounter issues:

- Check the Vercel deployment logs for specific errors
- Ensure all environment variables are correctly set
- If you see build errors related to dependencies, try adding the following to your project settings:
  - Install Command: `npm install --legacy-peer-deps`

## Step 2: Deploy the Frontend

1. Go to [Vercel Dashboard](https://vercel.com/dashboard)
2. Click "Add New" → "Project"
3. Import the `veltis-frontend` repository
4. In the configuration screen:
   - Framework Preset: Vite
   - Root Directory: ./
   - Build Command: `npm run build:vercel`
   - Output Directory: `dist`

5. Configure the following environment variables:
   ```
   VITE_NODE_ENV=production
   NODE_ENV=production
   VITE_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
   VITE_NFT_STORAGE_API_KEY=your_nft_storage_api_key
   VITE_BLOCKCHAIN_NETWORK=polygon-amoy
   VITE_IP_NFT_REGISTRY_CONTRACT=0x...
   VITE_SIMPLE_IP_NFT_REGISTRY_CONTRACT=0x...
   VITE_POLYGON_AMOY_RPC_URL=https://polygon-amoy.g.alchemy.com/v2/your_alchemy_key
   VITE_CHAIN_ID=80002
   VITE_NETWORK_NAME=Polygon Amoy
   VITE_FRACTIONALIZATION_FACTORY_CONTRACT=0x...
   ```

6. Click "Deploy"

### Troubleshooting Frontend Deployment

If you encounter issues:

- Check that the `vercel-build.js` file is present in your repository
- Verify that the `build:vercel` script is defined in your `package.json`
- Ensure all environment variables are correctly set
- Check the Vercel deployment logs for specific errors

## Step 3: Connect Frontend to Backend

After both deployments are successful:

1. Get the URL of your deployed backend (e.g., `https://veltis-backend.vercel.app`)
2. Add it as an environment variable to your frontend project:
   ```
   VITE_API_URL=https://veltis-backend.vercel.app
   ```

3. Redeploy the frontend to apply the changes

## Step 4: Verify Deployment

1. Visit your deployed frontend URL
2. Test the following functionality:
   - User authentication with Clerk
   - Creating and viewing IP NFTs
   - Connecting to MetaMask
   - Interacting with smart contracts

## Conclusion

You have successfully deployed the Veltis platform to Vercel. If you encounter any issues or need further assistance, please refer to the troubleshooting sections or contact the development team.

## Additional Resources

- [Vercel Documentation](https://vercel.com/docs)
- [Next.js Deployment Guide](https://nextjs.org/docs/deployment)
- [Vite Deployment Guide](https://vitejs.dev/guide/static-deploy.html)
- [Clerk Documentation](https://clerk.com/docs) 