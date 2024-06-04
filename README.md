# ToolsToken
Tools Token Smart contract with Tax and Auto Liquidity
https://repo.sourcify.dev/contracts/full_match/1/0xc14B4d4CA66f40F352d7a50fd230EF8b2Fb3b8d4/sources/

Go ahead and fork the Tools Token Smart Contract for your Projects or for Testing purposes! 

**Constructor Arguments** you will need at the time of Deployment: 

Arg [0] : name (string): YOUR PROJECT NAME

Arg [1] : symbol (string): YOUR TOKEN NAME

Arg [2] : _rescueAddress (address): 0x123456789 // replace this with the Address that rescues tokens from the CA

Arg [3] : _liquifyProtocolAddress (address): 0x123456789 // for Blocktools this our Liquifier CA however you can provide any valid wallet address 

Arg [4] : totalSupply (uint256): INPUT NUMBER HERE FOR YOUR TOTAL SUPPLY in uint256 // example 10000000000000000000

Arg [5] : _buyProtocolFee (uint256): INPUT NUMBER HERE FOR YOUR BUY FEE // example 1,2,3

Arg [6] : _sellProtocolFee (uint256): INPUT NUMBER HERE FOR YOUR SELL FEE // example 1,2,3

Arg [7] : _quickSellProtocolFee (uint256): INPUT NUMBER HERE FOR YOUR QUICK SELL FEE // this is the fee that will apply if holders sell within 1 month, example 1,2,3

Arg [8] : _buyLiquidityFee (uint256): INPUT NUMBER HERE FOR YOUR BUY AUTO LIQUIDITY FEE // example 1,2,3 

Arg [9] : _sellLiquidityFee (uint256): INPUT NUMBER HERE FOR YOUR SELL AUTO LIQUIDITY FEE // example 1,2,3 

Arg [10] : _quickSellLiquidityFee (uint256): INPUT NUMBER HERE FOR YOUR QUICK SELL AUTO LIQUIDITY FEE // this is the fee that will apply if holders sell within 1 month example 1,2,3 


To change the QuickSell block.timestamp duration, look for the below code and change the number from 730 to a number of your choice (TOOLS TOKEN is 730 hours, or 1 month) depending on your project. 

(_traderFirstSwapTimestamp[from] + (**730** hours) >= block.timestamp)

**How to use post deployment**: 
- After you have added liquidity to Uniswap set QuickSell to **TRUE**
- You can update Buy and Sell Fees via Update Quick Buy Fee and Update Exit Fee
- Tax cannot be set higher than 30% in this contract although Projects may change that, it is not recommended!
- You can remove limits
- You must write the startTrading function for token to be swappable
- You can renounce the CA

**Limits**: 
- Default limits of 2% has been set for maxTrade (for Swaps) and maxHolding (in wallet)
- You can change that here:
  
i. maxTradeAmount = totalSupply * 20 / 1000; // 20 = 2%, if you want 1% use 10

ii. maxHolding = totalSupply * 20 / 1000; // 20 = 2%, if you want 1% use 10
  
- Remove Limits has been added to remove all restrictions once stable!

**Trade Activation** is done via StartTrading function (without calling this the token will not be swappable!)

**Renounce Ownership** renounces the CA permanently with only the Rescue address being able to retrieve stuck tokens (if any) from the CA.
If you don't want a rescue address, simply add the dead address as the Rescue address, or remove it  from the constructor and code!

**Disclaimer**: 
Please note Blocktools is not responsible for how anyone uses it, why anyone uses it, or the outcome of anyone using it! 
