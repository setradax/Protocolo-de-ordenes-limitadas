# Llenar orden de limite

`LimitOrderProtocolFacade.fillLimitOrder()`

## Parametros:

| Campo             | Tipo                  | Descripción                                                                      |
| ----------------- | --------------------- | -------------------------------------------------------------------------------- |
| `order`           | `LimitOrder`          | una estructura de orden límite. Ver [Estructura de órdenes limitadas](./limit-order-structure.md) |
| `signature`       | `LimitOrderSignature` | firma de una orden limitada                                                       |
| `makerAmount`     | `String`              | cantidad de activo del creador (en unidades de token)                                          |
| `takerAmount`     | `String`              | cantidad de activos del tomador (en unidades de token)                                          |
| `thresholdAmount` | `String`              | el umbral para la cantidad de activos recibidos (en unidades de activos recibidos)       |

> Nota: para ejecutar una orden límite, solo se debe especificar una de las cantidades
> El segundo debe establecerse en `0`
## Ejemplo

```typescript
import Web3 from 'web3';
import {
    LimitOrderProtocolFacade,
    LimitOrder,
    LimitOrderSignature,
    Web3ProviderConnector
} from '@1inch/limit-order-protocol';
const walletAddress = '0xhhh...';
const contractAddress = '0x5fa31604fc5dcebfcac2481f9fa59d174126e5e6';
const order: LimitOrder = {...};
const signature: LimitOrderSignature = '...';
const makerAmount = '400000000';
const takerAmount = '0';
const thresholdAmount = '600000000';
const connector = new Web3ProviderConnector(new Web3('...'));
const limitOrderProtocolFacade = new LimitOrderProtocolFacade(contractAddress, connector);
const callData = limitOrderProtocolFacade.fillLimitOrder(
    order,
    signature,
    makerAmount,
    takerAmount,
    thresholdAmount
);
sendTransaction({
    from: walletAddress,
    gas: 210_000, // Set your gas limit
    gasPrice: 40000, // Set your gas price
    to: contractAddress,
    data: callData,
});
```
