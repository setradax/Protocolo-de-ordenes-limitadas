# Creación de un orden de RFQ:

## Parámetros:

| Field                | Type      | Description                                                                                                                                                                                    |
| -------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                 | `Number`  | es un paso a través, identificador entero que comienza en 1                                                                                                                                            |
| `expiresInTimestamp` | `Number`  | es la marca de tiempo en segundos cuando la orden límite ya no estará disponible para su ejecución. Por ejemplo: 1623166270029                                                                         |
| `makerAssetAddress`  | `String`  | la dirección del activo que desea vender (dirección de un contrato de token)                                                                                                                        |
| `takerAssetAddress`  | `String`  | la dirección del activo que desea comprar (dirección de un contrato de token)                                                                                                                         |
| `makerAddress`       | `String`  | una dirección del creador (dirección de la billetera)                                                                                                                                                       |
| `takerAddress`       | `String?` | la dirección del tomador para quien se crea la orden limitada. _Este es un parámetro opcional_, si no se especifica, la orden límite estará disponible para su ejecución para todos |
| `makerAmount`        | `String`  | la cantidad de tokens de activos de fabricante que desea vender (en unidades de token). Por ejemplo: 5 DAI = 5000000000000000000 unidades                                                                        |
| `takerAmount`        | `String`  | la cantidad de tokens de activos del tomador que desea recibir por vender el activo del fabricante (en unidades de token). Por ejemplo: 5 DAI = 5000000000000000000 unidades                                         |

### Creando con typescript/javascript:

```typescript
import Web3 from 'web3';
import {
    LimitOrderBuilder,
    Web3ProviderConnector,
} from '@1inch/limit-order-protocol';
const contractAddress = '0x7643b8c2457c1f36dc6e3b8f8e112fdf6da7698a';
const walletAddress = '0xd337163ef588f2ee7cdd30a3387660019be415c9';
const chainId = 1;
const web3 = new Web3('...');
// You can create and use a custom provider connector (for example: ethers)
const connector = new Web3ProviderConnector(web3);
const limitOrderBuilder = new LimitOrderBuilder(
    contractAddress,
    chainId,
    connector
);
const RFQorder = limitOrderBuilder.buildRFQOrder({
    id: 1,
    expiresInTimestamp: 1623166102,
    makerAssetAddress: '0x111111111117dc0aa78b770fa6a738034120c302',
    takerAssetAddress: '0xbb4cdb9cbd36b01bd1cbaebf2de08d9173bc095c',
    makerAddress: walletAddress,
    makerAmount: '1000000000000000000',
    takerAmount: '9000000000000000000',
});
```

##  Creando a través de CLI (con argumentos):

```shell
npx limit-order-rfq-utils --\
--operation=create \
--chainId=56 \
--privateKey={xxx} \
--orderId=1 \
--expiresIn=300 \
--makerAssetAddress=0x111111111117dc0aa78b770fa6a738034120c302 \
--takerAssetAddress=0x1af3f329e8be154074d8769d1ffa4ee058b1dbc3 \
--makerAmount=1000000000000000000 \
--takerAmount=4000000000000000000 \
--takerAddress=""
```

## Creando a través de CLI (a través de aviso):

```shell
npx limit-order-rfq-utils
```

Como resultado recibirá una estructura de [RFQ orden](./limit-order-rfq-structure.md). Ejemplo:

```json
{
    "info": "29941961886664662331741887180822",
    "makerAsset": "0x111111111117dc0aa78b770fa6a738034120c302",
    "takerAsset": "0x1af3f329e8be154074d8769d1ffa4ee058b1dbc3",
    "makerAssetData": "0x23b872dd00000000...0000",
    "takerAssetData": "0x23b872dd00000000...0000"
}
```
