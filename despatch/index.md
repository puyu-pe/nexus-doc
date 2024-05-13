# Despatch Endpoint API (Descontinuado)
- [Uso básico](#uso-básico)
- [Formatos](#formatos)
- Uso avanzado
    - [Transporte publico](./transporte-publico.md)
    - [Transporte privado](./transporte-privado-itinerante.md)


## Uso básico
Registra una **guia remision** para la empresa en la que el usuario está registrado.

> Nota: La API no valida los cálculos de los montos o pesos, por lo tanto debe de calcularlos bién antes de enviarlos.

**URL** : `/api/v1/despatch`

**Method** : `POST`

**Auth required** : SI

**Campos**

```js
{
  "tipoDoc": "[`String` Tipo de documento. Guía de Remisión: 09] - [Catálogo No. 01]",
  "serie": "[`Alphanumeric` Serie del comprobante máximo 4 dígitos]",
  "correlativo": "[`Numeric` Correlativo del comprobante máximo 8 dígitos]",
  "fechaEmision": "[`Datetime`]",
  "destinatario": { //
    "tipoDoc": "[`String` Tipo de documento de identidad. DNI: 1, RUC: 6] - [Catálogo No. 06]",
    "numDoc": "[`Alphanumeric` según corresponda a `tipoDoc` y al Catálogo No. 06]",
    "rznSocial": "[`String` Razón social del cliente]"
  },
  "tercero": {
    "tipoDoc": "[`String` Tipo de documento de identidad. DNI: 1, RUC: 6] - [Catálogo No. 06]",
    "numDoc": "[`Alphanumeric` según corresponda a `tipoDoc` y al Catálogo No. 06]",
    "rznSocial": "[`String` Razón social del cliente]"
  },
  "observation": "[`String` observación]",
  "documentBaja": {
    "tipoDoc": "[`String` Tipo de documento. Guía de Remisión: 09] - [Catálogo No. 01]",
    "nroDoc": "[`String` Numero de documento]",
  },
  "documentRel": {
    "tipoDoc": "[`String` Tipo de documento. Guía de Remisión: 09] - [Catálogo No. 01]",
    "nroDoc": "[`String` Numero de documento]",
  },
  "envio": {
    "modTraslado": "[`String` Modalidad de traslado. Transporte público: 01, Transporte privado: 02] - [Catálogo No. 18]",
    "codTraslado": "[`String` Motivo del traslado. Ventas: 01, Compra: 02, ... ] - [Catálogo No. 20]",
    "desTraslado": "[`String` Descripción de motivo de traslado ]",
    "fecTraslado": "[`Datetime`]",
    "codPuerto": "[`String` Código de puerto o aeropuerto de embarque/desembarque ]",
    "indTransbordo": "[`Bool` Indicador de Transbordo Programado ]",
    "pesoTotal": "[`Numeric` Peso bruto total de los bienes  ]",
    "undPesoTotal": "[`String` Unidad de medida del peso bruto = KGM ] - [Catálogo N° 03]",
    "numBultos": "[`Numeric` Numero de Bultos o Pallets ]",
    "numContenedor": "[`String` Datos del contenedor. Numero de Contenedor]",
    "llegada": {
      "ubigeo": "[`String` Ubigeo] - [Catálogo N° 13]",
      "direccion": "[`String` Direccion completa y detallada]"
    },
    "partida": {
      "ubigeo": "[`String` Ubigeo] - [Catálogo N° 13]",
      "direccion": "[`String` Direccion completa y detallada]"
    }
  },
  "transportista": {
    "tipoDoc": "[`String` Tipo de documento de identidad. DNI: 1, RUC: 6] - [Catálogo No. 06]",
    "numDoc": "[`Alphanumeric` según corresponda a `tipoDoc` y al Catálogo No. 06]",
    "rznSocial": "[`String` Razón social del cliente]",
    "placa": "[`String` Numero de placa del vehiculo]",
    "choferTipoDoc": "[`String` Tipo de documento de identidad. DNI: 1, RUC: 6] - [Catálogo No. 06]",
    "choferDoc": "[`Alphanumeric` según corresponda a `tipoDoc` y al Catálogo No. 06]"
  },
  "details": [
    {
      "unidad": "[`String` Unidad de medida del producto]",
      "cantidad": "[`Numeric` Cantidad de la venta]",
      "codigo": "[`String` Código del producto]",
      "codProdSunat": "[`String` Código del producto. No nescesario por ahora]",
      "descripcion": "[`String` Descripción del producto o servicio]"
    },
    ...
  ]
}
```

**Ejemplo**

```json
{
  "tipoDoc": "09",
  "serie": "T001",
  "correlativo": 4,
  "fechaEmision": "2020-05-10T00:00:00-05:00",
  "destinatario": {
    "tipoDoc": "6",
    "numDoc": "20000000002",
    "rznSocial": "EMPRESA01 SA"
  },
  "tercero": {
    "tipoDoc": "6",
    "numDoc": "20000000003",
    "rznSocial": "EMPRESA02 SA"
  },
  "observation": "Transporto bolsas para basura",
  "documentBaja": {
    "tipoDoc": "09",
    "nroDoc": "T001-00001"
  },
  "documentRel": {
    "tipoDoc": "02",
    "nroDoc": "213123"
  },
  "envio": {
    "modTraslado": "01",
    "codTraslado": "01",
    "desTraslado": "VENTA",
    "fecTraslado": "2020-05-10T00:00:00-05:00",
    "codPuerto": "123",
    "indTransbordo": 0,
    "pesoTotal": 12.5,
    "undPesoTotal": "KGM",
    "numBultos": 2,
    "numContenedor": "XD-2232",
    "llegada": {
      "ubigeo": "150101",
      "direccion": "AV LIMA"
    },
    "partida": {
      "ubigeo": "150203",
      "direccion": "AV ITALIA"
    }
  },
  "transportista": {
    "tipoDoc": "6",
    "numDoc": "20000000004",
    "rznSocial": "TRANSPORTES S.A.C",
    "placa": "ABI-453",
    "choferTipoDoc": "1",
    "choferDoc": "40003344"
  },
  "details": [
    {
      "unidad": "NIU",
      "cantidad": 2,
      "codigo": "PROD1",
      "codProdSunat": "P001",
      "descripcion": "Gaseosa KR. mediana"
    },
    {
      "unidad": "NIU",
      "cantidad": 4,
      "codigo": "PROD2",
      "codProdSunat": "P002",
      "descripcion": "Galleta Soda caja"
    }
  ]
}
```

## Success Response

**HTTP Code** : `200 OK`

**Ejemplo**

```json
{
    "status": "OK",
    "code": "0",
    "message": "La guia remision numero G001-100, ha sido aceptada",
    "pdf": "http://fast-see.fastworkx.com/20000000001/G001/100/200.32/pdf"
}
```

## Error Responses

**Condition** : Si alguno de los campos requeridos está vacío.

**HTTP Code** : `400 BAD REQUEST`

**Content** :

```js
{
  "status": "ERROR",
  "code": "-1",
  "message": "Uno o más campos necesitan ser corregidos.",
  "erros": {
    "serie": "This value should not be blank.",
    "client.tipoDoc": "This value should not be blank.",
    ...
  }
}
```


**Condition** : Si el servidor sunat se encuentra caido o el tiempo de espera se ha agotado.

**HTTP Code** : `400 BAD REQUEST`

**Content** :

```json
{
    "status": "ERROR",
    "code": "HTTP",
    "message": "Bad Gateway",
    "pdf": "http://fast-see.fastworkx.com/20000000001/G001/100/200.32/pdf"
}
```


**Condition** : Si el comprobante ya fué registrado previamente.

**HTTP Code** : `400 BAD REQUEST`

**Content** :

```json
{
    "status": "ERROR",
    "code": "2109",
    "message": "El comprobante fue registrado previamente con otros datos."
}
```
## Formatos

Permite incluir en el json del comprobante el formato en el cual se desea **mostrar**.

*  **a4**     : Comprobante en formato A4.

*  **ticket** : Comprobante en formato ticket.

*  **a5v**    : Comprobante en formato A5 en sentido **vertical**.

*  **a5h**    : Comprobante en formato A5 en sentido **horizontal**.

**Ejemplo**
```json
{
    ...
    "formato": "a5h",
    ...
}
```

<hr/>

[Volver a menu del API](../api.md)
