# NonceManager


Un contrato de ayuda para administrar el nonce del remitente de tx




## Funciones
### aumentarNonce
```solidity
function increaseNonce(
) external
```
Avanza nonce por uno



### avanceNonce
```solidity
function advanceNonce(
  uint8 amount
) public
```
Avanza nonce por cantidad especificada

#### Parámetros:
| Nombre | Tipo | Descripción                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`amount` | uint8 | 


### nonceIguala
```solidity
function nonceEquals(
  address makerAddress,
  uint256 makerNonce
) external returns (bool)
```
Comprueba si `makerAddress` ha especificado `makerNonce`


#### Parámetros:
| Name | Type | Descripción                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`makerAddress` | Dirección | 
|`makerNonce` | uint256 | 

#### Valores devueltos:
| Name                           | Type          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`Result`| bool | Cierto si `makerAddress` ha especificado nonce. De lo contrario, falso

## Eventos
### NonceAumentado
```solidity
event NonceIncreased(
  address maker,
  uint256 newNonce
)
```


#### Parameters:
| Nombre | Tipo | Descripción                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`maker` | Dirección | 
|`newNonce` | uint256 | 
