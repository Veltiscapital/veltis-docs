# Veltis Deployment Guide

This guide provides comprehensive instructions for deploying the Veltis platform, including smart contracts, backend, and frontend.

## Prerequisites

1. **Node.js and npm**: Make sure you have Node.js (v16+) and npm installed.
2. **Vercel Account**: Create an account at [vercel.com](https://vercel.com) for deploying the frontend and backend.
3. **Supabase Account**: Create an account at [supabase.com](https://supabase.com) for the database.
4. **Alchemy Account**: Create an account at [alchemy.com](https://alchemy.com) for blockchain API access.
5. **MetaMask Wallet**: Install the [MetaMask](https://metamask.io) browser extension and create a wallet.
6. **Polygon Amoy Testnet**: Add the Polygon Amoy testnet to your MetaMask wallet.
7. **Test MATIC**: Get test MATIC from the [Polygon faucet](https://faucet.polygon.technology/).

## Project Structure

The Veltis project is organized into the following repositories:

1. **veltis-contracts**: Smart contracts for IP-NFTs, fractionalization, and marketplace.
2. **veltis-backend**: Next.js backend API for the platform.
3. **veltis-frontend**: React/Vite frontend application.

## Deployment Steps

### Step 1: Deploy Smart Contracts

1. **Set up environment variables**:
   ```
   node create-env.js
   ```
   This will create a `.env` file with the necessary configuration for smart contract deployment.

2. **Create missing contracts**:
   ```
   node create-missing-contracts.js
   ```
   This will create any missing smart contract files.

3. **Compile smart contracts**:
   ```
   node compile-contracts.js
   ```
   This will compile the smart contracts using Hardhat.

4. **Deploy smart contracts**:
   ```
   node deploy-contracts.js
   ```
   This will deploy the smart contracts to the Polygon Amoy testnet and save the deployment information to `deployment-info.json`.

### Step 2: Deploy Backend

1. **Prepare backend for deployment**:
   ```
   node deploy-backend.js
   ```
   This will create the necessary configuration files for deploying the backend to Vercel.

2. **Deploy backend to Vercel**:
   ```
   cd organized/veltis-backend
   vercel --prod
   ```
   When prompted, provide the following environment variables:
   - `NODE_ENV`: production
   - `SUPABASE_URL`: Your Supabase project URL
   - `SUPABASE_ANON_KEY`: Your Supabase anonymous key
   - `SUPABASE_SERVICE_ROLE_KEY`: Your Supabase service role key
   - `JWT_SECRET`: A secure random string for JWT signing
   - `ALCHEMY_API_KEY`: Your Alchemy API key
   - `NFT_STORAGE_API_KEY`: Your NFT.Storage API key
   - `IP_NFT_REGISTRY_CONTRACT`: The address of the deployed IPNFTRegistry contract
   - `SIMPLE_IP_NFT_REGISTRY_CONTRACT`: The address of the deployed SimpleIPNFTRegistry contract
   - `FRACTIONALIZATION_FACTORY_CONTRACT`: The address of the deployed FractionalizationFactory contract
   - `MARKETPLACE_CONTRACT`: The address of the deployed Marketplace contract
   - `POLYGON_AMOY_RPC_URL`: The RPC URL for the Polygon Amoy testnet

### Step 3: Update Frontend Environment Variables

1. **Update frontend environment variables**:
   ```
   node update-frontend-env.js
   ```
   This will prompt you for the deployed backend URL and other configuration values, and update the frontend environment variables accordingly.

### Step 4: Deploy Frontend

1. **Deploy frontend to Vercel**:
   ```
   cd organized/veltis-frontend
   vercel --prod
   ```
   When prompted, provide the environment variables that were set in the previous step.

## Testing the Deployment

1. **Test the backend**:
   ```
   curl https://your-backend-url.vercel.app/api/test
   ```
   You should receive a JSON response indicating that the backend is working.

2. **Test the frontend**:
   Visit your deployed frontend URL in a browser. Make sure to:
   - Connect your MetaMask wallet to the Polygon Amoy testnet
   - Test the connection to the backend by attempting to view or create IP-NFTs
   - Verify that smart contract interactions work correctly

## Troubleshooting

### Smart Contract Deployment Issues

- **Error: Insufficient funds**: Make sure your wallet has enough test MATIC for deployment.
- **Error: Nonce too high**: Reset your MetaMask account in Settings > Advanced > Reset Account.
- **Error: Gas price too low**: Increase the gas price in the deployment script.

### Backend Deployment Issues

- **Error: Build failed**: Check the Vercel build logs for specific errors.
- **Error: API routes not working**: Ensure the CORS configuration is correct in `next.config.js`.
- **Error: Database connection failed**: Verify your Supabase credentials.

### Frontend Deployment Issues

- **Error: API connection failed**: Check that the `VITE_API_BASE_URL` is set correctly.
- **Error: Smart contract interaction failed**: Verify that the contract addresses are correct and that your wallet is connected to the Polygon Amoy testnet.

## Additional Resources

- [Veltis Documentation](https://github.com/veltiscapital/docs)
- [Polygon Amoy Testnet Documentation](https://wiki.polygon.technology/docs/amoy/)
- [Vercel Documentation](https://vercel.com/docs)
- [Supabase Documentation](https://supabase.com/docs)
- [Alchemy Documentation](https://docs.alchemy.com/)

## Support

If you encounter any issues during deployment, please contact the Veltis team at support@veltiscapital.com or open an issue on the GitHub repository. 