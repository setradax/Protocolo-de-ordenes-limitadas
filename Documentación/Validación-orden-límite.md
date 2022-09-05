# Validar una orden de límite

`LimitOrderProtocolFacade.simulateCalls()`

Existe la posibilidad de comprobar la validez de la orden límite.
Por ejemplo, puede verificar que una orden limitada sea válida por afirmación.

> **Bajo del capó:**  
> En un `simulateCalls()` llamada, el contrato devuelve la cadena como `CALL_RESULTS_01101`  
> Si esa cadena contiene al menos un símbolo `0` entonces una orden limitada no es válida, de lo contrario - es válida
## Ejemplo:

```typescript
import Web3 from 'web3';
import {
    LimitOrderProtocolFacade,
    LimitOrder,
    Web3ProviderConnector
} from '@1inch/limit-order-protocol';
const contractAddress = '0x5fa31604fc5dcebfcac2481f9fa59d174126e5e6';
const order: LimitOrder = {...};
const connector = new Web3ProviderConnector(new Web3('...'));
const limitOrderProtocolFacade = new LimitOrderProtocolFacade(contractAddress, connector);
const addresses = [contractAddress];
const callDatas = [order.predicate];
try {
    const result: boolean = await limitOrderProtocolFacade.simulateCalls(addresses, callDatas);
    console.log('Order validity: ', result);
} catch (error) {
    console.error(error);
}
```
