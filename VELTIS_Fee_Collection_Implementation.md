# VELTIS Fee Collection Implementation

This document outlines the implementation of the fee collection mechanism for the VELTIS platform, which enables monetization of IP-NFTs through minting and transfer fees.

## Overview

The fee collection mechanism has been implemented with the following components:

1. **Smart Contract**: A new `IPNFTRegistryWithFees` contract that extends the original `IPNFTRegistry` with fee collection functionality
2. **Frontend Integration**: Updates to the frontend code to support the new fee collection features
3. **User Interface**: Enhanced UI components to display fee information and collect user input for valuations

## Smart Contract Changes

### New Contract: IPNFTRegistryWithFees

A new contract has been created that extends the functionality of the original IPNFTRegistry contract with fee collection mechanisms:

- **Minting Fees**: 3% of the IP valuation is collected when minting a new IP-NFT
- **Transfer Fees**: 3% of the IP valuation is collected when transferring an IP-NFT, plus royalties to the original creator
- **Valuation Tracking**: The contract tracks the valuation of each IP-NFT for fee calculation

Key features of the new contract:

- **Payable Functions**: The `mintIP` and `transferWithFee` functions are now payable to accept fee payments
- **Fee Calculation**: Functions to calculate minting and transfer fees based on valuations
- **Fee Distribution**: Automatic distribution of fees to the platform and royalties to creators
- **Valuation Updates**: Authorized verifiers can update the valuation of an IP-NFT

### Deployment Script

The deployment script has been updated to deploy the new contract and set the initial fee percentages:

- Mint fee: 3%
- Transfer fee: 3%
- Default royalty percentage: 2.5%

## Frontend Integration

### blockchain.ts Library

The blockchain.ts library has been updated with new functions to support fee collection:

- **calculateMintFee**: Calculate the minting fee for a given valuation
- **calculateTransferFee**: Calculate the transfer fee for a given token
- **mintIPNFT**: Updated to handle fee payment during minting
- **transferIPNFT**: New function to transfer tokens with fee payment

### Mint.tsx Component

The Mint.tsx component has been enhanced to support valuation input and fee display:

- **Valuation Input**: Added a field for users to input the valuation of their IP
- **Fee Display**: Shows the calculated minting fee (3% of valuation)
- **Fee Payment**: Handles the payment of fees during the minting process

## User Interface Enhancements

### Valuation Input

A new input field has been added to the minting form to collect the valuation of the IP:

```jsx
<div>
  <label className="text-sm font-medium block mb-1">IP Valuation (ETH)</label>
  <div className="relative">
    <Input 
      name="valuation"
      value={formValues.valuation}
      onChange={handleInputChange}
      type="number"
      min="0.01"
      step="0.01"
      placeholder="1.0"
    />
    <div className="absolute inset-y-0 right-0 pr-3 flex items-center pointer-events-none">
      <span className="text-gray-500">ETH</span>
    </div>
  </div>
  <p className="text-xs text-gray-500 mt-1">
    The valuation determines the minting fee (3% of valuation).
  </p>
</div>
```

### Fee Display

The preview section now displays the valuation and calculated minting fee:

```jsx
<div>
  <p className="font-medium">Valuation</p>
  <p className="text-gray-600">{formValues.valuation} ETH</p>
</div>
<div>
  <p className="font-medium">Minting Fee (3%)</p>
  <p className="text-gray-600">{(parseFloat(formValues.valuation) * 0.03).toFixed(4)} ETH</p>
</div>
```

## Testing

To test the fee collection mechanism:

1. Deploy the new contract to the Polygon Amoy testnet
2. Connect your wallet to the VELTIS platform
3. Navigate to the Mint page
4. Upload IP documentation
5. Enter metadata including a valuation
6. Mint the IP-NFT and approve the transaction with the fee
7. Verify that the fee has been collected by checking the transaction on the block explorer

## Configuration

The fee percentages can be configured by the contract administrator:

- **Mint Fee**: `setMintFeePercentage(uint256 percentage)`
- **Transfer Fee**: `setTransferFeePercentage(uint256 percentage)`
- **Fee Collector**: `setFeeCollector(address collector)`

## Future Enhancements

Potential future enhancements to the fee collection mechanism:

1. **Tiered Fees**: Different fee percentages based on IP type or valuation range
2. **Fee Discounts**: Discounts for specific users or during promotional periods
3. **Fee Splitting**: Splitting platform fees among multiple stakeholders
4. **Subscription Model**: Option for users to pay a subscription fee instead of per-transaction fees
5. **Fee Analytics**: Dashboard to track fee collection and distribution

## Conclusion

The fee collection mechanism provides a sustainable revenue model for the VELTIS platform while ensuring fair compensation for IP creators. The implementation is flexible and can be adjusted as needed to meet changing business requirements.
