# Veltis Project Structure

This document outlines the organization of the Veltis project, explaining how the various repositories are structured and where specific components should be placed.

## Repository Organization

The Veltis project is divided into several repositories, each with a specific purpose:

1. **veltis-project** - The main project repository containing overall documentation and project information
2. **veltis-frontend** - The React/TypeScript frontend application
3. **veltis-backend** - The backend API service
4. **veltis-contracts** - Smart contracts for tokenization and fractionalization
5. **veltis-docs** - Comprehensive documentation for all parts of the system

## Component Placement Guidelines

When developing for Veltis, please follow these guidelines for where to place your code:

### Frontend Components

- **UI Components**: `veltis-frontend/src/components/ui/`
- **Page Components**: `veltis-frontend/src/pages/`
- **Layouts**: `veltis-frontend/src/layouts/`
- **Hooks**: `veltis-frontend/src/hooks/`
- **Context Providers**: `veltis-frontend/src/contexts/`
- **Utility Functions**: `veltis-frontend/src/lib/`
- **API Integration**: `veltis-frontend/src/lib/api.ts`
- **Blockchain Integration**: `veltis-frontend/src/lib/blockchain.ts`

### Backend Components

- **API Routes**: `veltis-backend/src/routes/`
- **Controllers**: `veltis-backend/src/controllers/`
- **Database Models**: `veltis-backend/src/models/`
- **Services**: `veltis-backend/src/services/`
- **Middleware**: `veltis-backend/src/middleware/`
- **Utility Functions**: `veltis-backend/src/utils/`

### Smart Contracts

- **NFT Contracts**: `veltis-contracts/contracts/nft/`
- **Fractionalization Contracts**: `veltis-contracts/contracts/fractionalization/`
- **Marketplace Contracts**: `veltis-contracts/contracts/marketplace/`
- **Libraries**: `veltis-contracts/contracts/libraries/`
- **Test Scripts**: `veltis-contracts/test/`
- **Deployment Scripts**: `veltis-contracts/scripts/`

## Development Workflow

1. Use the `temp_veltis-*` directories for development and testing
2. Use the organization scripts (`organize-and-push.sh`) to sync changes to the appropriate repositories
3. Push changes to GitHub using the `push-to-github.sh` script

## Maintaining Repository Organization

To keep the repositories organized:

1. Never commit code to the wrong repository
2. Use the provided scripts for organizing and pushing changes
3. Update documentation when making structural changes
4. Maintain clear separation of concerns between repositories

## Next Steps for Development

1. Complete the tokenization engine implementation
2. Finalize the fractionalization functionality
3. Implement the marketplace features
4. Add analytics and reporting capabilities
5. Set up continuous integration and deployment (CI/CD)
