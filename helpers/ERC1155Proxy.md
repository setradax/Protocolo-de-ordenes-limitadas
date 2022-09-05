# ERC1155Proxy






## Deriva
- [ImmutableOwner](helpers/ImmutableOwner.md)

## Funciones
### constructor
```solidity
function constructor(
  address _immutableOwner
) public
```


#### Parámetros:
| Nombre | Tipo | Descripción                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`_immutableOwner` | dirección | 


### func_301JL5R
```solidity
function func_301JL5R(
  address from,
  address to,
  uint256 amount,
  contract IERC1155 token,
  uint256 tokenId,
  bytes data
) external
```
Método de transferencia de proxy para `IERC1155.safeTransferFrom`. selector debe coincidir con `IERC20.transferFrom`

#### Parámetros:
| Nombre | Tipo | Descripción                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`from` | address | 
|`to` | address | 
|`amount` | uint256 | 
|`token` | contract IERC1155 | 
|`tokenId` | uint256 | 
|`data` | bytes | 
