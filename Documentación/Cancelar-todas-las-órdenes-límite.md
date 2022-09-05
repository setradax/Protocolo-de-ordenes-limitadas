# Cancelar todas las órdenes limitadas

`LimitOrderProtocolFacade.advanceNonce(count)`  
or  
`LimitOrderProtocolFacade.increaseNonce()`

## En primer lugar, lea sobre [Nonce](#nonce)

`advanceNonce(count) or increaseNonce()` incrementa el nonce y todas las órdenes de límite con un predicado al valor de nonce anterior se vuelven inválidas

> **Aviso!**  
> El enfoque solo funciona cuando todas las órdenes tienen el `nonceEquals` predicado
## Example:

```typescript
import Web3 from 'web3';
import {
    LimitOrderProtocolFacade,
    Web3ProviderConnector,
} from '@1inch/limit-order-protocol';
const walletAddress = '0xhhh...';
const contractAddress = '0x5fa31604fc5dcebfcac2481f9fa59d174126e5e6';
const connector = new Web3ProviderConnector(new Web3('...'));
const limitOrderProtocolFacade = new LimitOrderProtocolFacade(
    contractAddress,
    connector
);
const callData = limitOrderProtocolFacade.increaseNonce();
sendTransaction({
    from: walletAddress,
    gas: 210_000, // Set your gas limit
    gasPrice: 40000, // Set your gas price
    to: contractAddress,
    data: callData,
});
```
