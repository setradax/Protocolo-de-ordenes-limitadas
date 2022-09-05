# ChainlinkCalculator


Un contrato helper para las interacciones con oráculo de precios en el Protocolo ChainLink




## Funciones
### precioÚnico
```solidity
function singlePrice(
  contract AggregatorV3Interface oracle,
  uint256 inverseAndSpread,
  uint256 amount
) external returns (uint256)
```
Calcula el precio del token en relación con la unidad de Oracle (ETH o USD)


#### Parámetros:
| Nombre | Tipo | Descripción                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`oracle` | contract AggregatorV3Interface | bandera inversa concatenada y propagación. Los 254 bits más bajos especifican la cantidad distribuida. La propagación está escalada por 1e9, i.e. 101% = 1.01e9, 99% = 0.99e9. El bit más alto se establece cuando el precio del oráculo debe invertirse, p. para oráculo de DAI-ETH , inverse=false means that we request DAI price in ETH and inverse=true significa que solicitamos el precio de DAI en ETH e inverse=true significa que solicitamos el precio de ETH en DAI  
|`inverseAndSpread` | uint256 | 
|`amount` | uint256 | 

#### Valores devueltos:
| Name                           | Type          | Descripción                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`Amount`| uint256 | * untado * precio del oráculo

### doblePrecio
```solidity
function doublePrice(
  contract AggregatorV3Interface oracle1,
  contract AggregatorV3Interface oracle2,
  uint256 spread,
  int256 decimalsScale,
  uint256 amount
) external returns (uint256)
```
Calcula el precio del token A en relación con el token B. Tenga en cuenta que el orden es importante


#### Parámetros:
| Nombre | Tipo | Descripción                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`oracle1` | contract AggregatorV3Interface | 
|`oracle2` | contract AggregatorV3Interface | 
|`spread` | uint256 | 
|`decimalsScale` | int256 | 
|`amount` | uint256 | 

#### Valores devueltos:
| Nombre                           | Tipo          | Description                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`Result`| uint256 | Token Un precio relativo multiplicado por la cantidad
