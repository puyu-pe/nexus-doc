# Credit Note Endpoint API

Registra una **nota de crédito** para la empresa en la que el usuario está registrado.

> Nota: La API no valida los cálculos de los montos, por lo tanto debe de calcularlos bién antes de enviarlos.

**URL** : `/api/v1/credit-note` se recomienda `/api/v1/note`

**Method** : `POST`

**Auth required** : SI

**Campos**

```js
{
  "tipDocAfectado": "[`String` Tipo de documento. Factura: 01]",
  "numDocfectado": "[`Alphanumeric` Serie mas correlativo",
  "codMotivo": "[`String` Código de motivo. Anulación de operación: 01, Anulación por error en el RUC: 02, Corrección por error en la descripción: 03, Descuento global: 04, Descuento por ítem: 05, Devolución total: 06, Devolución por ítem: 07, Bonificación: 08, Disminución en el valor: 09, Otros Conceptos: 10]",
  "desMotivo": "[`String` Descripción del motivo]",
  "tipoDoc": "[`String` Tipo de documento. Nota de crédito: 07]",
  "serie": "[`Alphanumeric` Serie del comprobante máximo 4 dígitos]",
  "correlativo": "[`Numeric` Correlativo del comprobante máximo 8 dígitos]",
  "fechaEmision": "[`Datetime`]",
  "tipoMoneda": "[`String` Tipo de modeneda según catálogo No. 02. ejemplo: PEN]",
  "monedaTipoCambio": "[`Numeric` Sin tipoMoneda = PEN campo opcional, si es USD es obligatorio]",
  "mtoOperGravadas": "[`Numeric` Total gravadas]",
  "mtoOperExoneradas": "[`Numeric` Total exoneradas]",
  "mtoOperInafectas": "[`Numeric` Total inafectas]",
  "mtoIGV": "[`Numeric` Total IGV]",
  "totalImpuesto": "[`Numeric` Total inpuestos]",
  "mtoImpVenta": "[`Numeric` Total]",
  "forced?": "[`Boolean` Forzar envio evitando número máximo de días]",
  "client": {
    "tipoDoc": "[`String` Tipo de documento. DNI: 1, Carnet de extrangería: 4, RUC: 6, Pasaporte: 7]",
    "numDoc": "[`Alphanumeric` según corresponda a `tipoDoc` y al Catálogo No. 06]",
    "rznSocial": "[`String` Razón social del cliente]",
    "address": { // opcional
      "ubigueo": "[`String` Código ubigeo]",
      "codigoPais": "[`String` Código del pais ejemplo. Perú: PE]", // opcional
      "departamento": "[`String` Departamento]", // opcional
      "provincia": "[`String` Provincia]", // opcional
      "distrito": "[`String` Distrito]", // opcional
      "direccion": "[`String` Dirección]" // opcional
   }
  },
  "details": [ // detalle da la venta array de productos o servicios
    {
      "unidad": "[`String` Unidad de medida del producto o servicio]",
      "cantidad": "[`Numeric` Cantidad de la venta]",
      "codProducto": "[`String` Código del producto o servicio]",
      "descripcion": "[`String` Descripción del producto o servicio]",
      "mtoValorUnitario": "[`Numeric` Valor de venta unitario]",
      "mtoBaseIgv": "[`Numeric`]",
      "porcentajeIgv": "[`Numeric` Porcentage de IGV]",
      "igv": "[`Numeric` Monto IGV]",
      "totalImpuesto": "[`Numeric` Total impuesto]",
      "tipAfeIgv": "[`String` Tipo de afectación. Gravado - Operación Onerosa: 10, Gravado - Retiro por premio: 11, Gravado - Retiro por donación: 12, Gravado - Retiro: 13, Gravado - Retiro por publicidad: 14, Gravado - Bonificaciones: 15, Gravado - Retiro por entrega a trabajadores: 16, Gravado - IVAP: 17, Exonerado - Operación Onerosa: 20, Exonerado - Transferencia Gratuita: 21, Inafecto - Operación Onerosa: 30, Inafecto - Retiro por Bonificación: 31, Inafecto - Retiro: 32, Inafecto - Retiro por Muestras Médicas: 33, Inafecto - Retiro por Convenio Colectivo: 34, Inafecto - Retiro por premio: 35, Inafeto - Retiro por publicidad: 36, Exportación: 40]",
      "mtoPrecioUnitario": "[`Numeric` Precio unitario del producto]",
      "mtoValorVenta": "[`Numeric` Total venta producto]"
    },
    ...
  ],
 "legends": [
   {
     "code": "[`string` Código de leyenda ejemplo: 1000]",
     "value": "[`string` Monto de la venta en letras según codigo de leyenda]"
   }
 ]
}
```

**Ejemplo**

```json
{
  "tipDocAfectado": "01",
  "numDocfectado": "F001-100",
  "codMotivo": "01",
  "desMotivo": "ERROR EN DIGITACIÓN",
  "tipoDoc": "07",
  "serie": "FA01",
  "correlativo": 100,
  "fechaEmision": "2019-05-10T00:00:00-05:00",
  "tipoMoneda": "PEN",
  "mtoOperGravadas": 182.00,
  "mtoOperExoneradas": 0.00,
  "mtoOperInafectas": 0.00,
  "mtoIGV": 18.32,
  "totalImpuesto": 18.32,
  "mtoImpVenta": 200.32,
  "client": {
    "tipoDoc": "6",
    "numDoc": "20384203133",
    "rznSocial": "UNICAUCHO E.I.R.L.",
    "address": {
      "ubigueo": "150117",
      "codigoPais": "PE",
      "departamento": "LIMA",
      "provincia": "LIMA",
      "distrito": "LOS OLIVOS",
      "direccion": "AV. SANTIAGO ANTUNEZ DE MAYOL NRO. 1060"
   }
 },
 "details": [
   {
     "unidad": "NIU",
     "cantidad": 2,
     "codProducto": "0202",
     "descripcion": "Gaseosa KR. mediana",
     "mtoValorUnitario": 1.00,
     "mtoBaseIgv": 1.00,
     "porcentajeIgv": 18,
     "igv": 0.18,
     "totalImpuesto": 0.18,
     "tipAfeIgv": "10",
     "mtoPrecioUnitario": 1.18,
     "mtoValorVenta": 2.32
   },
   {
      "unidad": "NIU",
      "cantidad": 1,
      "codProducto": "0209",
      "descripcion": "Frescomar",
      "mtoValorUnitario": 100.00,
      "mtoBaseIgv": 100,
      "porcentajeIgv": 18,
      "igv": 18.00,
      "totalImpuesto": 18,
      "tipAfeIgv": "10",
      "mtoPrecioUnitario": 118.00,
      "mtoValorVenta": 118.00
    }
  ],
  "legends": [
    {
      "code": "1000",
      "value": "SON CIENTO VEINTE CON 32/100 SOLES"
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
    "message": "La Nota de Credito numero FA01-100, ha sido aceptada",
    "pdf": "http://fast-see.fastworkx.com/10732197970/FA01/100/200.32/pdf"
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
    "pdf": "http://fast-see.fastworkx.com/10732197970/FA01/100/200.32/pdf"
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
## Credit Note Format

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
