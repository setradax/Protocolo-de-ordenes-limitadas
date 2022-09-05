# ERC721ProxySafe






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


### func_60iHVgK
```solidity
function func_60iHVgK(
  address from,
  address to,
  uint256 ,
  uint256 tokenId,
  contract IERC721 token
) external
```
Método de transferencia de proxy para `IERC721.transferFrom`. Selector debe coincidir con `IERC20.transferFrom`.
Tenga en cuenta que `amount` no se utiliza por razones de seguridad para evitar la venta no deseada del token ERC-721 a través del relleno parcial

#### Parámetros:
| Nombre | Tipo | Descripción                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`from` | dirección | 
|`to` | dirección | 
|`` | uint256 | 
|`tokenId` | uint256 | 
|`token` | contract IERC721 | 
