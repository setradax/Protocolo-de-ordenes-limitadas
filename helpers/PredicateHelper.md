# PredicateHelper


Un contrato de ayuda para ejecutar funciones booleanas en resultados de llamadas destino arbitrarios




## Funciones
### o
```solidity
function or(
  address[] targets,
  bytes[] data
) external returns (bool)
```
Llama a cada objetivo con los datos correspondientes


#### Parámetros:
| Nombre | Tipo | Descripción                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`targets` | dirección[] | 
|`data` | bytes[] | 

#### Return Values:
| Nombre                           | Tipo          | Descripción                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`Result`| bool | Verdadero si la llamada a cualquier destino devolvió Verdadero. De lo contrario, falso

### y
```solidity
function and(
  address[] targets,
  bytes[] data
) external returns (bool)
```
Calls every target with corresponding data


#### Parámetros:
| Nombre | Tipo | Descripción                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`targets` | dirección[] | 
|`data` | bytes[] | 

#### Return Values:
| Nombre                           | Tipo          | Descripción                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`Result`| bool | True si las llamadas a todos los objetivos devolvieron True. De lo contrario, falso

### eq
```solidity
function eq(
  uint256 value,
  address target,
  bytes data
) external returns (bool)
```
Llama al objetivo con datos específicos y prueba si es igual al valor


#### Parámetros:
| Nombre | Tipo | Descripción                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`value` | uint256 | Valor a probar  
|`target` | dirección | 
|`data` | bytes | 

#### Return Values:
| Name                           | Tipo          | Descripción                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`Result`| bool | Verdadero si la llamada al objetivo devuelve el mismo valor que `value`. De lo contrario, falso

### lt
```solidity
function lt(
  uint256 value,
  address target,
  bytes data
) external returns (bool)
```
Llama al objetivo con datos específicos y prueba si es inferior al valor


#### Parámetros:
| Nombre | Tipo | Descripción                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`value` | uint256 | Valor a probar  
|`target` | dirección | 
|`data` | bytes | 

#### Return Values:
| Nombre                           | Tipo          | Descripción                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`Result`| bool | Verdadero si la llamada al objetivo devuelve un valor que es menor que `value`. De lo contrario, falso

### gt
```solidity
function gt(
  uint256 value,
  address target,
  bytes data
) external returns (bool)
```
Llama al objetivo con datos específicos y prueba si es mayor que el valor


#### Parámetros:
| Nombre | Tipo | Descripción                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`value` | uint256 | Valor a probar 
|`target` | dirección | 
|`data` | bytes | 

#### Return Values:
| Nombre                           | Tipo          | Descripción                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`Result`| bool | Verdadero si la llamada al objetivo devuelve un valor mayor que `value`. De lo contrario, falso

### marcaDeTiempoContinuación
```solidity
function timestampBelow(
  uint256 time
) external returns (bool)
```
Comprueba el tiempo transcurrido contra la marca de tiempo del bloque

#### Parámetros:
| Nombre | Tipo | Descripción                                                          |
| :--- | :--- | :------------------------------------------------------------------- |
|`time` | uint256 | 

#### Valores devueltos:
| Nombre                           | Tipo          | Descripción                                                                  |
| :----------------------------- | :------------ | :--------------------------------------------------------------------------- |
|`Result`| bool | Verdadero si la marca de tiempo del bloque actual es inferior a `time`. De lo contrario, falso
