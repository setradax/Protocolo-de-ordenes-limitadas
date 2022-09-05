# Cancelación de una orden limitada:

Se supone que los pedidos de RFQ se crearán con una vida corta.
Pero, si es necesario cancelar el pedido RFQ creado, esto se puede hacer de la siguiente manera:

## Parámetros:

| Parametro | Tipo     | Descripción                                                                                           |
| --------- | -------- | ----------------------------------------------------------------------------------------------------- |
| `info`    | `String` | información sobre un pedido de RFQ (ver más arriba en la sección [Estructura de RFQ](./limit-order-rfq-structure.md)) |

## Creando con typescript/javascript:

```typescript
import Web3 from 'web3';
import {
    LimitOrderProtocolFacade,
    Web3ProviderConnector,
    RFQOrder
} from '@1inch/limit-order-protocol';
const contractAddress = '0x7643b8c2457c1f36dc6e3b8f8e112fdf6da7698a';
const walletAddress = '0xd337163ef588f2ee7cdd30a3387660019be415c9';
const web3 = new Web3('...');
// You can create and use a custom provider connector (for example: ethers)
const connector = new Web3ProviderConnector(web3);
const limitOrderProtocolFacade = new LimitOrderProtocolFacade(
    contractAddress,
    connector
);
const RFQorder: RFQOrder = {...};
const callData = limitOrderProtocolFacade.cancelRFQOrder(RFQorder.info);
// Send transaction for the RFQ order canceling
// Must be implemented
sendTransaction({
    from: walletAddress,
    gas: 50_000, // Set your gas limit
    gasPrice: 600000000, // Set your gas price
    to: contractAddress,
    data: callData,
});
```

## Cancelando a través de CLI (con argumentos):

`gasPrice` - en unidades de GWEI

```shell
npx limit-order-rfq-utils --\
--operation=cancel \
--chainId=56 \
--privateKey={xxx} \
--gasPrice=6 \
--orderInfo=29941961886664662336741887180811
```

## Cancelación a través de CLI (a través de aviso):

```shell
npx limit-order-rfq-utils
```

Como resultado, recibirá un enlace al hash de la transacción.
