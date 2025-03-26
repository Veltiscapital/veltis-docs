# Veltis Platform Deployment Options

This document provides an overview of all the available deployment options for the Veltis platform.

## Option 1: Automated Deployment (Recommended for Local Testing)

Use the provided scripts to automatically configure and deploy the Veltis platform:

1. Run the environment check script to verify your setup:
   ```bash
   ./check-environment.sh
   ```

2. Fix Hardhat compatibility issues if you're using Node.js v20+:
   ```bash
   ./fix-hardhat.sh
   ```

3. Run the automatic deployment script to configure all components:
   ```bash
   ./deploy-auto.sh
   ```

4. Follow the instructions provided by the script to deploy to Vercel.

## Option 2: Manual Deployment via Web Interface (Recommended for Production)

Follow the detailed instructions in the `MANUAL_DEPLOYMENT_GUIDE.md` file to deploy the Veltis platform through the Vercel web interface:

1. Configure smart contracts with default addresses
2. Deploy the backend to Vercel through the web interface
3. Deploy the frontend to Vercel through the web interface
4. Verify the deployment

This option provides more control over the deployment process and is recommended for production environments.

## Option 3: Component-by-Component Deployment

Deploy each component separately using the provided scripts:

1. Deploy the backend:
   ```bash
   ./deploy-backend-fixed.sh
   ```

2. Deploy the frontend:
   ```bash
   ./deploy-frontend-fixed.sh
   ```

This option allows you to deploy components independently and is useful for updating specific parts of the application.

## Environment Variables

Regardless of the deployment option you choose, you'll need to configure the following environment variables:

### Backend Environment Variables

```
NODE_ENV=production
ALCHEMY_API_KEY=mJNGWubj_qQYGnXn1mFLcHhiyBftWps7
POLYGON_AMOY_RPC_URL=https://polygon-amoy.g.alchemy.com/v2/mJNGWubj_qQYGnXn1mFLcHhiyBftWps7
IP_NFT_REGISTRY_CONTRACT=0x0C0cE3CA0d5d21E2f58a7505Afc7856a36fd1363
SIMPLE_IP_NFT_REGISTRY_CONTRACT=0x0C0cE3CA0d5d21E2f58a7505Afc7856a36fd1363
FRACTIONALIZATION_FACTORY_CONTRACT=0xabcdef123456789abcdef123456789abcdef1234
MARKETPLACE_CONTRACT=0x456789abcdef123456789abcdef123456789abcde
NFT_STORAGE_API_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJkaWQ6ZXRocjoweEZFMTI3RDI3MzlhNzJCNDM3RjM3N2M1ODFjMTI5NjY4QjcwMDRFMzAiLCJpc3MiOiJuZnQtc3RvcmFnZSIsImlhdCI6MTY5MzQyMDI5MzI3MCwibmFtZSI6IlZlbHRpcyJ9.Nh7D7oRPHEWmA9jKrULG0d7DQZnXYi_bBwQpKQkXNwA
```

### Frontend Environment Variables

```
VITE_API_BASE_URL=https://your-backend-url.vercel.app/api
VITE_BLOCKCHAIN_NETWORK=polygon-amoy
VITE_IP_NFT_REGISTRY_CONTRACT=0x0C0cE3CA0d5d21E2f58a7505Afc7856a36fd1363
VITE_SIMPLE_IP_NFT_REGISTRY_CONTRACT=0x0C0cE3CA0d5d21E2f58a7505Afc7856a36fd1363
VITE_FRACTIONALIZATION_FACTORY_CONTRACT=0xabcdef123456789abcdef123456789abcdef1234
VITE_MARKETPLACE_CONTRACT=0x456789abcdef123456789abcdef123456789abcde
VITE_POLYGON_AMOY_RPC_URL=https://polygon-amoy.g.alchemy.com/v2/mJNGWubj_qQYGnXn1mFLcHhiyBftWps7
VITE_KYC_REQUIRED=false
VITE_MARKETPLACE_ENABLED=true
VITE_CONSULTING_ENABLED=true
VITE_FRACTIONALIZATION_ENABLED=true
VITE_CLERK_PUBLISHABLE_KEY=pk_test_ZmFpci10YWhyLTM1LmNsZXJrLmFjY291bnRzLmRldiQ
VITE_NFT_STORAGE_API_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJkaWQ6ZXRocjoweEZFMTI3RDI3MzlhNzJCNDM3RjM3N2M1ODFjMTI5NjY4QjcwMDRFMzAiLCJpc3MiOiJuZnQtc3RvcmFnZSIsImlhdCI6MTY5MzQyMDI5MzI3MCwibmFtZSI6IlZlbHRpcyJ9.Nh7D7oRPHEWmA9jKrULG0d7DQZnXYi_bBwQpKQkXNwA
VITE_ALCHEMY_API_KEY=mJNGWubj_qQYGnXn1mFLcHhiyBftWps7
```

## Troubleshooting

If you encounter issues during deployment, refer to the troubleshooting sections in the respective deployment guides:

- For automated deployment issues, check the console output and logs
- For manual deployment issues, refer to the troubleshooting sections in `MANUAL_DEPLOYMENT_GUIDE.md`
- For component-specific issues, check the Vercel deployment logs

## Additional Resources

- [Vercel Documentation](https://vercel.com/docs)
- [Next.js Deployment](https://nextjs.org/docs/deployment)
- [Vite Deployment](https://vitejs.dev/guide/static-deploy.html)
- [Hardhat Documentation](https://hardhat.org/hardhat-runner/docs/getting-started)

## Conclusion

Choose the deployment option that best suits your needs and follow the corresponding instructions. If you encounter any issues, refer to the troubleshooting sections or contact the Veltis support team for assistance. 