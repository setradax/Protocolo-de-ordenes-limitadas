# Estructura de pedidos RFQ:

| Campo            | Tipo     | Descripción                                                                         |
| ---------------- | -------- | ----------------------------------------------------------------------------------- |
| `info`           | `String` | información sobre una RFQ de orden límitado, codificada como un número decimal.     |
| `makerAsset`     | `String` | la dirección del activo que desea vender (dirección de un contrato de token)             |
| `takerAsset`     | `String` | la dirección del activo que desea comprar (dirección de un contrato de token)             |
| `makerAssetData` | `String` | la información técnica sobre un activo del fabricante y su cantidad                              |
| `takerAssetData` | `String` | la información técnica sobre un activo tomador y su cantidad                               |

`info` - una clave compuesta que consta de:

- el id de la orden de límite
- la marca de tiempo de su vencimiento

Ejemplo de generación de información de RFQ de orden límite:

```javascript
const id = 1;
const expiresInTimestamp = 1623166102;
const info = ((BigInt(expiresInTimestamp) << BigInt(64)) | BigInt(id)).toString(
    10
);
```
