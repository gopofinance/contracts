# contracts
Gopo Finance Finance Public Repository
# Gopo Finance (GOPO) Contracts

### Contract Address: 0x5Ab2F9e8dA6E8f8D41A01cec2078aD374D1F5e67
### White Paper: [Gopo Finance Whitepaper](https://gopo.finance/gopo-whitepaper.pdf)

## Smart Contract
### BEP-20
Gopo Finance is an BEP-20 contract that implements the following interface:
```Solidity
interface IERC20 {
    function totalSupply() external view returns (uint256);
    function balanceOf(address account) external view returns (uint256);
    function transfer(address recipient, uint256 amount) external returns (bool);
    function allowance(address owner, address spender) external view returns (uint256);
    function approve(address spender, uint256 amount) external returns (bool);
    function transferFrom(address sender, address recipient, uint256 amount) external returns (bool);
    event Transfer(address indexed from, address indexed to, uint256 value);
    event Approval(address indexed owner, address indexed spender, uint256 value);
}
```

### UniSwap Factory and Exchange
GOPO uses the PancakeSwap contracts to enable swapping tokens:

```Solidity
// PancakeSwap Interface
interface IUniswapV2Factory {
    event PairCreated(address indexed token0, address indexed token1, address pair, uint);
    function feeTo() external view returns (address);
    function feeToSetter() external view returns (address);
    function getPair(address tokenA, address tokenB) external view returns (address pair);
    function allPairs(uint) external view returns (address pair);
    function allPairsLength() external view returns (uint);
    function createPair(address tokenA, address tokenB) external returns (address pair);
    function setFeeTo(address) external;
    function setFeeToSetter(address) external;
}
```

### Public Get Methods
The following public getters are available to query:
```Solidity
// Public Parameters
address payable public marketingAddress = payable(0xcb7af6E92479F93a49013f19600444Dc440A41ab);
address payable public foundationAddress = payable(0x591f2Da99E9f7658A76e70B03e899aB74f624f19);
address public  deadAddress = 0x000000000000000000000000000000000000dEaD;
address private wallet1 = 0xAc315647a02638FfB6a2a3A13b8A3561f69C416e;
address private wallet2 = 0x4Fa4cAFD188E3c9d4E4F9EcA22B3Dc1093CF0B88;
address private wallet3 = 0x10fa2E85ff1DAd5fDa8a2F76Bd63C8E0b52f4d8F;

// Public Get Functions
function name() external pure returns (string memory);
function symbol() external pure returns (string memory);
function decimals() external pure returns (uint8);
function totalSupply() external view returns (uint);
function balanceOf(address owner) external view returns (uint);
function allowance(address owner, address spender) external view returns (uint);
function approve(address spender, uint value) external returns (bool);
function transfer(address to, uint value) external returns (bool);
function transferFrom(address from, address to, uint value) external returns (bool);
function nonces(address owner) external view returns (uint);
function permit(address owner, address spender, uint value, uint deadline, uint8 v, bytes32 r, bytes32 s) external;
```

### Public Transactions
The following public transaction functions are available to call:
```Solidity
receive() external payable
function isExcludedFromFee(address account) public view returns(bool)
function burn(uint256 amount) external
function transfer(address recipient, uint256 amount) public override returns (bool)
function approve(address spender, uint256 amount) public override returns (bool) 
function transferFrom(address sender, address recipient, uint256 amount) public override returns (bool)
function deliver(uint256 tAmount) public
```

### Constructor
There are three constructor options:

**Mainnet**

This is the constructor deployed to mainnet:

```Solidity
//mainnet
_name = "Gopo Finance"; _symbol = "GOPO"; _decimals = 9;
MAX = ~uint256(0); _tTotal = 120000000000000000 * 10**9; _rTotal = (MAX - (MAX % _tTotal));
address payable public marketingAddress = payable(0xcb7af6E92479F93a49013f19600444Dc440A41ab);
address payable public foundationAddress = payable(0x591f2Da99E9f7658A76e70B03e899aB74f624f19);
address public  deadAddress = 0x000000000000000000000000000000000000dEaD;
IRouter _pancakeRouter = IRouter(0x10ED43C718714eb63d5aA57B78B54704E256024E);

```
