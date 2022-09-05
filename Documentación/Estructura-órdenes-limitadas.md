# Estructura de órdenes limitadas:

| Campo            |Tipo      | Descripción                                                                                                                        |
| ---------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `salt`           | `String` | algún valor único. Es necesario poder crear órdenes limitadas con los mismos parámetros (para que tengan un hash diferente) |
| `makerAsset`     | `String` | la dirección del activo que desea vender (dirección de un contrato de token)                                                            |
| `takerAsset`     | `String` | la dirección del activo que desea comprar (dirección de un contrato de token)                                                            |
| `makerAssetData` | `String` | la información técnica sobre un activo del creador y su cantidad                                                                             |
| `takerAssetData` | `String` | la información técnica sobre un activo tomador y su cantidad                                                                              |
| `getMakerAmount` | `String` | información técnica para obtener la cantidad del activo del creador                                                                         |
| `getTakerAmount` | `String` | información técnica para obtener la cantidad del activo del tomador                                                                         |
| `predicate`      | `String` | un dato de llamada predicado. Consulte [Documentos predicados](./predicate.md)                                                                        |
| `permit`         | `String` | un permiso para llamada de datos                                                                                                                  |
| `interaction`    | `String` | datos de una llamada de interacción                                                                                                          |
