# Afirmaciones

`LimitOrderPredicateBuilder`

Una orden limitada puede contener uno o más afirmación que indiquen la lógica de su validez.
**Hay dos tipos de operadores afirmados:**

## Operadores condicionales:

| Nombre    | Descripción                                                               |
| ------- | ------------------------------------------------------------------------- |
| **and** | combinar varios afirmaciones, volver `true` cuando todos los afirmaciones son válidos   |
| **or**  | combinar varios afirmaciones, volver `true` cuando uno de los afirmaciones es válido |

## Operadores comparativos:

> Todos los operadores comparativos tienen tres argumentos: 
> (**value**: string, **address**: string, **callData**: string)

> **Cómo funcionan las operadoras:** 
> En una llamada de operador, el contrato ejecuta el `callData` para el `address` y compara _**a result**_ con el `value`

| Nombre   | Descripción                                     |
| ------ | ----------------------------------------------- |
| **eq** | _**a result**_ debe ser igual a la `value`     |
| **lt** | _**a result**_ Debe ser menor que la `value`    |
| **gt** | _**a result**_ Debe ser mayor que la `value` |

## Operadores integrados:

> `nonceEquals(makerAddress: string, makerNonce: number)`

La afirmación verifica que el `makerNonce` es igual al nonce de `makerAddress`

---

> `timestampBelow(timestamp: number)`

La afirmación comprueba que `timestamp` es mayor que la tiempo actual

## Ejemplo:

```typescript
import Web3 from 'web3';
import {
    LimitOrderProtocolFacade,
    LimitOrderPredicateBuilder,
    LimitOrderPredicateCallData,
    Web3ProviderConnector,
} from '@1inch/limit-order-protocol';
const makerAddress = '0x5fa31604fc5dcebfcac2481f9fa59d174126e5e6';
const tokenAddress = '0xcc83bc1050244c98ac562f9faff408f069a137d7';
const balanceOfCallData = '0x000...000';
const contractAddress = '0x5fa31604fc5dcebfcac2481f9fa59d174126e5e6';
const connector = new Web3ProviderConnector(new Web3('...'));
const limitOrderProtocolFacade = new LimitOrderProtocolFacade(
    contractAddress,
    connector
);
const limitOrderPredicateBuilder = new LimitOrderPredicateBuilder(
    limitOrderProtocolFacade
);
const {
    or,
    and,
    timestampBelow,
    nonceEquals,
    gt,
    lt,
    eq,
} = limitOrderPredicateBuilder;
const simplePredicate: LimitOrderPredicateCallData = and(
    timestampBelow(Math.round(Date.now() / 1000) + 60), // a limit order is valid only for 1 minute
    nonceEquals(makerAddress, 4) // a limit order is valid until the nonce of makerAddress is equal to 4
);
const complexPredicate: LimitOrderPredicateCallData = or(
    and(
        timestampBelow(Math.round(Date.now() / 1000) + 60),
        nonceEquals(makerAddress, 4),
        gt('10', tokenAddress, balanceOfCallData)
    ),
    or(timestampBelow(5444440000), lt('20', tokenAddress, balanceOfCallData)),
    eq('30', tokenAddress, balanceOfCallData)
);
```
