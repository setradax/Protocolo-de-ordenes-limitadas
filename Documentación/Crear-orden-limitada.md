# Crear una orden de límite

`LimitOrderBuilder.buildLimitOrder()`

## Parámetros:

| Campo               | Tipo      | Descripción                                                                                                                                                                                    |
| ------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `makerAssetAddress` | `String`  | la dirección del activo que desea vender (dirección de un contrato de token)                                                                                                                        |
| `takerAssetAddress` | `String`  | la dirección del activo que desea comprar (dirección de un contrato de token)                                                                                                                       |
| `makerAddress`      | `String`  | una dirección del creador (dirección de la billetera)                                                                                                                                                       |
| `takerAddress`      | `String?` | la dirección del tomador para quien se crea la orden limitada. _Este es un parámetro opcional_, si no se especifica, la orden límite estará disponible para su ejecución para todos |
| `makerAmount`       | `String`  | la cantidad de tokens de activos de fabricante que desea vender (en unidades de token). Por ejemplo: 5 DAI = 5000000000000000000 unidades                                                                        |
| `takerAmount`       | `String`  | la cantidad de tokens de activos del tomador que desea recibir por vender el activo del creador (en unidades de token). Por ejemplo: 5 DAI = 5000000000000000000 unidades                                         |
| `predicate`         | `String?` | datos de una llamada predicada. Predeterminado: `0x`. Consulte [Documentos predicados](./predicate.md)                                                                                                                     |
| `permit`            | `String?` | datos de una llamada de permiso. Opción por defecto: `0x`                                                                                                                                                              |
| `interaction`       | `String?` | datos de una llamada de interacción.  Opción por defecto: `0x`                                                                                                                                                        |

## Ejemplo:

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

// ...

const limitOrder = limitOrderBuilder.buildLimitOrder({
    makerAssetAddress: '0xbb4cdb9cbd36b01bd1cbaebf2de08d9173bc095c',
    takerAssetAddress: '0x111111111117dc0aa78b770fa6a738034120c302',
    makerAddress: '0xfb3c7ebccccAA12B5A884d612393969Adddddddd',
    makerAmount: '100',
    takerAmount: '200',
    predicate: '0x0',
    permit: '0x0',
    interaction: '0x0',
});
const limitOrderTypedData = limitOrderBuilder.buildLimitOrderTypedData(
    limitOrder
);
const limitOrderSignature = limitOrderBuilder.buildOrderSignature(
    walletAddress,
    limitOrderTypedData
);
const limitOrderHash = limitOrderBuilder.buildLimitOrderHash(
    limitOrderTypedData
);
```

Como resultado recibirá una estructura de [orden límite](./limit-order-structure.md).. Ejemplo:

```json
{
    "salt": "1",
    "makerAsset": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
    "takerAsset": "0x6b175474e89094c44da98b954eedeac495271d0f",
    "getMakerAmount": "0xf4a215c300000...0000",
    "getTakerAmount": "0x296637bf00000...0000",
    "makerAssetData": "0x23b872dd00000...0000",
    "takerAssetData": "0x23b872dd00000...0000",
    "predicate": "0x961d5b1e0000000000...0000",
    "permit": "0x",
    "interaction": "0x"
}
```

## Firma de orden limitada

Para completar una orden de límite, necesita una firma de estructura de datos escrita.
Puede crear una firma siguiendo el ejemplo anterior.

Pero el ejemplo usa `Web3ProviderConnector` que está diseñado para funcionar con una billetera.
Si necesita obtener la firma del lado del servidor, puede usar `PrivateKeyProviderConnector` y obtener la firma usando la clave privada.

```typescript
const walletAddress = '0xd337163ef588f2ee7cdd30a3387660019be415c9';

const privateKey =
    'd8d1f95deb28949ea0ecc4e9a0decf89e98422c2d76ab6e5f736792a388c56c7';
const limitOrderTypedData: EIP712TypedData = {
    // ...
};

const web3Provider = new Web3('...');
const privateKeyProviderConnector = new PrivateKeyProviderConnector(
    privateKey,
    web3Provider
);

const signature = await privateKeyProviderConnector.signTypedData(
    walletAddress,
    limitOrderTypedData
);
```
