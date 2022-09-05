# Límite de pedido restante

`LimitOrderProtocolFacade.remaining()`

De forma predeterminada, una orden de límite se crea sin completar.
Hasta el primer llenado, el método 'restante' arrojará un error 'LOP: Orden desconocido'.
Después del primer llenado, el método devolverá la cantidad restante.

> Nota: una orden limitada puede ejecutarse parcialmente
## Ejemplo:

```typescript
import Web3 from 'web3';
import {
    LimitOrderProtocolFacade,
    LimitOrderHash,
    Web3ProviderConnector,
} from '@1inch/limit-order-protocol';
import {BigNumber} from 'ethers/utils';
const orderMakerAmount = '400000000000'; // initial amount of the limit order
const orderHash: LimitOrderHash = '0x5fa31604fc5dcebfcac2481f9fa59d174126e5e6';
const contractAddress = '0x5fa31604fc5dcebfcac2481f9fa59d174126e5e6';
const connector = new Web3ProviderConnector(new Web3('...'));
const limitOrderProtocolFacade = new LimitOrderProtocolFacade(
    contractAddress,
    connector
);
const remaining = await getRemaining(orderHash);
async function getRemaining(orderHash: string): string {
    try {
        const remaining: BigNumber = limitOrderProtocolFacade.remaining(
            orderHash
        );
        return remaining.toString();
    } catch (error) {
        const errorMessage = typeof error === 'string' ? error : error.message;
        if (errorMessage.includes('LOP: Unknown order')) {
            return orderMakerAmount;
        }
        throw error;
    }
}
```
