# Nonce

`LimitOrderProtocolFacade.nonce()` - devuelve el nonce de la dirección de la billetera actual  
`LimitOrderProtocolFacade.advanceNonce(count: number)` - aumenta el nonce por el orden
`LimitOrderProtocolFacade.increaseNonce()` - aumenta el nonce por 1

**Nonce**: esta es una ejecución llamada "serie" de órdenes limitadas.
El nonce es útil cuando necesita crear un montón de órdenes limitadas con la capacidad de cancelarlas todas más tarde.

## Ejemplo:

```typescript
import Web3 from 'web3';
import {
    LimitOrderProtocolFacade,
    LimitOrderPredicateBuilder,
    Web3ProviderConnector
} from '@1inch/limit-order-protocol';
const walletAddress = '0xhhh...';
const contractAddress = '0x5fa31604fc5dcebfcac2481f9fa59d174126e5e6';
const chainId = 1;
const connector = new Web3ProviderConnector(new Web3('...'));
const limitOrderProtocolFacade = new LimitOrderProtocolFacade(contractAddress, connector);
const limitOrderPredicateBuilder = new LimitOrderPredicateBuilder(
    limitOrderProtocolFacade
);
const limitOrderBuilder = new LimitOrderBuilder(
    contractAddress,
    chainId,
    connector
);
// Get the current nonce
const nonce = await limitOrderProtocolFacade.nonce(contractAddress);
// Create a limit order with nonceEquals predicate
const predicate = limitOrderPredicateBuilder.nonceEquals(walletAddress, nonce);
const limitOrder = limitOrderBuilder.buildLimitOrder({
    ...,
    predicate
});
// Cancel all orders by advance nonce
const cancelAllOrdersCallData = limitOrderProtocolFacade.advanceNonce();
sendTransaction({
    from: walletAddress,
    gas: 210_000, // Set your gas limit
    gasPrice: 40000, // Set your gas price
    to: contractAddress,
    data: cancelAllOrdersCallData,
});
```
