# SeriesNonceManager


Un contrato de ayuda para administrar nonce con la serie.




## Functions
### aumentarNonce
```solidity
function increaseNonce(
  uint8 series
) external
```
Avanza nonce por uno

#### Parámetros:
| Nombre | Tipo | Descripción                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`series` | uint8 | 


### avanceNonce
```solidity
function advanceNonce(
  uint8 series,
  uint8 amount
) public
```
Avanza nonce por cantidad especificada

#### Parámetros:
| Nombre | Tipo | Descripción                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`series` | uint8 | 
|`amount` | uint8 | 


### nonceEquals
```solidity
function nonceEquals(
  uint8 series,
  address makerAddress,
  uint256 makerNonce
) external returns (bool)
```
Comprueba si `makerAddress` ha especificado `makerNonce` por `series`


#### Parámetros:
| Name | Tipo | Descripción                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`series` | uint8 | 
|`makerAddress` | dirección | 
|`makerNonce` | uint256 | 

#### Return Values:
| Nombre                           | Tipo          | Descripción                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`Result`| bool | Cierto si `makerAddress` ha especificado nonce. De lo contrario, falso

## Eventos
### NonceAumentado
```solidity
event NonceIncreased(
  address maker,
  uint8 series,
  uint256 newNonce
)
```


#### Parámetros:
| Nombre | Tipo | Descripción                                                        |
| :--- | :--- | :------------------------------------------------------------------- |
|`maker` | dirección | 
|`series` | uint8 | 
|`newNonce` | uint256 | 
