<div align="center">
    <img src="https://github.com/setradax/XDEX/blob/main/Images/logo-text1.png">
</div>

# Biblioteca de utilidades para el protocolo de órdenes de límite de 1inch V2

Este es el paquete de utilidades para trabajar con el `1inch Limit Orders Protocol`

Puede encontrar una descripción general y documentos sobre el protocolo de órdenes de límite de 1inch Dex Exchange [here](https://docs.1inch.io/limit-order-protocol/).

#### Smart contract addresses

-   Ethereum mainnet: `0x119c71d3bbac22029622cbaec24854d3d32d2828`
-   BSC mainnet: `0x1e38eff998df9d3669e32f4ff400031385bf6362`
-   Polygon mainnet: `0x94bc2a1c732bcad7343b25af48385fe76e08734f`
-   El repositorio de código fuente de contratos inteligentes está disponible [aquí](https://github.com/setradax/0xPAGE/tree/main/Smart-Contract-Structure/Protocolo-de-orden-limitada)

---

## Cobertura de prueba

| Declaraciones                                                               | Ramas                                                                   | Funciones                                                               | Líneas                                                               |
| ------------------------------------------------------------------------ | --------------------------------------------------------------------------- | ----------------------------------------------------------------------- | ------------------------------------------------------------------- |
| ![Declaraciones](https://img.shields.io/badge/Coverage-81.42%25-yellow.svg) | !Ramas](https://img.shields.io/badge/Coverage-92.23%25-brightgreen.svg) | ![Funciones](https://img.shields.io/badge/Coverage-81.54%25-yellow.svg) | ![Líneas](https://img.shields.io/badge/Coverage-81.42%25-yellow.svg) |

## Instalación

### Node

```
npm install @1inch/limit-order-protocol
```

### Yarn

```
yarn add @1inch/limit-order-protocol
```

---


## Sobre

El contrato permite a los usuarios realizar pedidos limitados, que luego podrían completarse en la cadena. La orden limitada en sí es una estructura de datos creada fuera de la cadena y firmada de acuerdo con EIP-712.

Lo más probable es que necesite usar las siguientes clases:

[LimitOrderBuilder](https://github.com/1inch/limit-order-protocol-utils/blob/master/src/limit-order.builder.ts) - para crear una orden limitada
[LimitOrderPredicateBuilder](https://github.com/1inch/limit-order-protocol-utils/blob/master/src/limit-order-predicate.builder.ts) - para crear un predicado para orden de límite  
[LimitOrderProtocolFacade](https://github.com/1inch/limit-order-protocol-utils/blob/master/src/limit-order-protocol.facade.ts) - para interactuar con el protocolo en la cadena de bloques

Las características clave del protocolo son la extrema flexibilidad y la alta eficiencia de gas que se logra mediante el uso de los siguientes tipos de órdenes.

## I. orden limitada

Una orden limitada es un instrumento financiero con el que puede poner a la venta un token ERC-20 a un precio fijo.
Por ejemplo, puedes poner a la venta 2 tokens WBTC al precio de 82415 tokens DAI.

El protocolo de órdenes limitadas tiene muchas herramientas para una gestión comercial flexible:

- Relleno parcial
- Predicados
- Cancelación única
- Cancelación de racimo
- Comprobación de plenitud
- Validación

> **Nota:** Puede crear una orden limitada incluso si su saldo es insuficiente para ejecutar la orden limitada en este momento. Sin embargo, debe tener una asignación para el activo del creador.
Para la creación de mercado, existen **órdenes RFQ** que tienen una optimización especial que no requiere una gran cantidad de gas para su ejecución.

### Límite de órdenes en el protocolo de agregación 1inch

[**Protocolo de agregación de 1inch **](https://1inch.io/aggregation-protocol/): el protocolo obtiene liquidez de varios intercambios y es capaz de dividir una sola transacción comercial en varios DEX para garantizar las mejores tarifas.
Puede enviar sus pedidos limitados a la base de datos de 1 pulgada y luego su pedido participará en el protocolo de agregación de 1inch.

### REST API (swagger):

-   [Ethereum Endpoint](https://limit-orders.1inch.io/swagger/ethereum/)
-   [Binance Smart Chain Endpoint](https://limit-orders.1inch.io/swagger/binance/)
-   [Polygon Endpoint](https://limit-orders.1inch.io/swagger/polygon/)


### Docs

1. [Inicio rápido](https://github.com/1inch/limit-order-protocol-utils/blob/master/docs/quick-start.md)
2. [Crear una orden de límite](https://github.com/1inch/limit-order-protocol-utils/blob/master/docs/create-limit-order.md)
3. [Estructura de órdenes limitadas](https://github.com/1inch/limit-order-protocol-utils/blob/master/docs/limit-order-structure.md)
4. [Límite de pedido restante](https://github.com/1inch/limit-order-protocol-utils/blob/master/docs/remaining.md)
5. [Nonce](https://github.com/1inch/limit-order-protocol-utils/blob/master/docs/nonce.md)
6. [Validar una orden de límite](https://github.com/1inch/limit-order-protocol-utils/blob/master/docs/validate-limit-order.md)
7. [Afirmación](https://github.com/1inch/limit-order-protocol-utils/blob/master/docs/predicate.md)
8. [Completar una orden de límite](https://github.com/1inch/limit-order-protocol-utils/blob/master/docs/fill-limit-order.md)
9. [Cancelar una orden limitada](https://github.com/1inch/limit-order-protocol-utils/blob/master/docs/cancel-limit-order.md)
10. [Cancelar todas las órdenes limitadas](https://github.com/1inch/limit-order-protocol-utils/blob/master/docs/cancel-all-limit-orders.md)
11. [Separador de dominio](https://github.com/1inch/limit-order-protocol-utils/blob/master/docs/domain-separator.md)

---

## II. Orden de RFQ (cotización)

**Una solicitud de cotización (RFQ)** es un proceso comercial en el que un cliente solicita una cotización a un proveedor (creador de mercado) para la compra de algunos tokens.

> Técnicamente, las órdenes RFQ son una versión reducida de las órdenes estándar, que contienen menos datos y herramientas para administrar, lo que a su vez permite gastar significativamente menos gas para su ejecución.

### Documentación:

1. [Creación de un pedido de RFQ](https://github.com/1inch/limit-order-protocol-utils/blob/master/docs/create-limit-order-rfq.md)
2. [Estructura de pedido de RFQ](https://github.com/1inch/limit-order-protocol-utils/blob/master/docs/limit-order-rfq-structure.md)
3. [Cancelación de un pedido de RFQ](https://github.com/1inch/limit-order-protocol-utils/blob/master/docs/cancel-limit-order-rfq.md)
4. [Completar un pedido de RFQ](https://github.com/1inch/limit-order-protocol-utils/blob/master/docs/fill-limit-order-rfq.md)
