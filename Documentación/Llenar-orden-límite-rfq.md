# Completar un pedido de RFQ:

Una orden RFQ se puede completar en su totalidad o en parte.

> ¡Importante! ¡Puede completar un pedido RFQ solo una vez!
## Parametros:

| Campo         | Descripción                                                                                                           |
| ------------- | ----------------------------------------------------------------------------------------------------------------------- |
| `order`       | estructura de la orden de RFQ (ver [Estructura de la orden de RFQ] ( ./docs/limit-order-rfq-structure.md))                           |
| `signature`   | firma de la fecha mecanografiada de la orden de RFQ (signTypedData_v4)                                                         |
| `makerAmount` | la cantidad de tokens de activos de creadores que desea completar (en unidades de token). Por ejemplo: 5 DAI = 5000000000000000000 unidades |
| `takerAmount` | la cantidad de tokens de activos del tomador que desea completar (en unidades de token). Por ejemplo: 5 DAI = 5000000000000000000 unidades |

> importante! Solo uno de los importes de los activos puede ser distinto de cero.
> Por ejemplo, si especificó el monto del creador, entonces el monto del tomador debe ser cero y viceversa.
## Rellenar con typescript/javascript:

```typescript
import Web3 from 'web3';
import {
    LimitOrderBuilder,
    LimitOrderProtocolFacade,
    RFQOrder,
    Web3ProviderConnector
} from '@1inch/limit-order-protocol';
const contractAddress = '0x7643b8c2457c1f36dc6e3b8f8e112fdf6da7698a';
const walletAddress = '0xd337163ef588f2ee7cdd30a3387660019be415c9';
const web3 = new Web3('...');
// You can create and use a custom provider connector (for example: ethers)
const connector = new Web3ProviderConnector(web3);
const limitOrderBuilder = new LimitOrderBuilder(
    contractAddress,
    chainId,
    connector
);
const limitOrderProtocolFacade = new LimitOrderProtocolFacade(
    contractAddress,
    connector
);
const RFQorder: RFQOrder = {...};
const typedData = limitOrderBuilder.buildRFQOrderTypedData(RFQorder);
const signature = await limitOrderBuilder.buildOrderSignature(
    walletAddress,
    typedData
);
const makerAmount = '1000000000000000000';
const takerAmount = '0';
const callData = limitOrderProtocolFacade.fillRFQOrder(
    order,
    signature,
    makerAmount,
    takerAmount
);
// Send transaction for the order RFQ filling
// Must be implemented
sendTransaction({
    from: walletAddress,
    gas: 150_000, // Set your gas limit
    gasPrice: 600000000, // Set your gas price
    to: contractAddress,
    data: callData,
});
```

## Rellenar a través de CLI (Con argumentos):

`gasPrice` - en unidades de GWEI

```shell
npx limit-order-rfq-utils --\
--operation=fill \
--chainId=56 \
--privateKey={xxx} \
--gasPrice=6 \
--order="{ \
    \"info\": \"29941961886664662336741887180811\", \
    \"makerAsset\": \"0x111111111117dc0aa78b770fa6a738034120c302\", \
    \"takerAsset\": \"0x1af3f329e8be154074d8769d1ffa4ee058b1dbc3\", \
    \"makerAssetData\": \"0x23b872dd00...000\", \
    \"takerAssetData\": \"0x23b872dd00...000\" \
}" \
--makerAmount=1000000000000000000 \
--takerAmount=0
```

## Rellenar a través de CLI  (a través de aviso):

```shell
npx limit-order-rfq-utils
```

Como resultado, recibirá un enlace al hash de la transacción.
