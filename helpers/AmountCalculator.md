# AmountCalculator/ImporteCalculadora


Un contrato auxiliar para los cálculos relacionados con los importes de los pedidos



## Funciones
### getMakingAmount
```solidity
function getMakingAmount(
  uint256 orderMakerAmount,
  uint256 orderTakerAmount,
  uint256 swapTakerAmount
) public returns (uint256)
```
Calcula la cantidad del creador

#### Parámetros:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`orderMakerAmount` | uint256 | 
|`orderTakerAmount` | uint256 | 
|`swapTakerAmount` | uint256 | 

#### Valores devueltos:
| Nombre                           | Tipo          | Descripción                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`Result`| uint256 | Floored maker amount

### getTakingAmount
```solidity
function getTakingAmount(
  uint256 orderMakerAmount,
  uint256 orderTakerAmount,
  uint256 swapMakerAmount
) public returns (uint256)
```
Calcula la cantidad del tomador

#### Parámetros:
| Nombre | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`orderMakerAmount` | uint256 | 
|`orderTakerAmount` | uint256 | 
|`swapMakerAmount` | uint256 | 

#### Valores devueltos:
| Name                           | Tipo          | Descripción                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`Result`| uint256 | Ceiled taker amount

### arbitraryStaticCall
```solidity
function arbitraryStaticCall(
  address target,
  bytes data
) external returns (uint256)
```
Performs an arbitrary call to target with data


#### Parámetros:
| Name | Type | Description                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`target` | address | 
|`data` | bytes | 

#### Valores devueltos:
| Nombre                           | Tipo          | Descripción                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`Result`| uint256 | Bytes transmuted to uint256
