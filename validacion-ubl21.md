# Validación UBL 2.1

Con la version de Greenter 5, viene el paquete validator con validaciones para UBL 2.1, y una de las mas importante
la descripcion de los items hasta 500 caracteres y mas cosas.

- [Invoice](#invoice)
- [Sale detail](#sale-detail)
- [Credit note](#credit-note)
- [Cargos y descuentos](#cargos-y-descuentos)
- [Atributos](#atributos)

## Invoice
Todos obligatorios
```js
"company": "[*, `object`]",
"tipoDoc": "[*,`String` Tipo de documento. Factura: 01, Boleta: 03]",
"tipoOperacion": "[*,`String` Tipo operación. Venta Interna: 0101, Exportación: 0102, No Domiciliados: 0103, Venta Interna - Anticipos: 0104, Venta Itinerante: 0105, Factura Guía: 0106, Venta Arroz Pilado: 0107, Factura - Comprobante de Percepción: 0108, Factura - Guía remitente: 0110, Factura - Guía transportista 0111]",
"serie": "[*,`Alphanumeric` Serie del comprobante máximo 4 dígitos]",
"correlativo": "[*,`Numeric` Correlativo del comprobante máximo 8 dígitos]",
"fechaEmision": "[*,`Datetime`]",
"tipoMoneda": "[*,`String` Tipo de modeneda según catálogo No. 02. ejemplo: PEN]",
"totalImpuesto": "[*,`Numeric` Total inpuestos]",
"valorVenta": "[*,`Numeric` valor venta]",
"mtoImpVenta": "[*,`Numeric` Total]",
...
"client": "[*, `object`]",
...
"formaPago": "[*, `object`]"
...
```
## Sale detail

```js
"details": [ // detalle da la venta array de productos o servicios
    {
      "unidad": "[*, `String` Unidad de medida del producto o servicio]",
      "descripcion": "[*, `String` Descripción del producto o servicio, máximo 500 caracteres]",
      "cantidad": "[Not blank, `Numeric` Cantidad de la venta]",
      "codProducto": "[`String` Código del producto o servicio, máximo 30 caracteres]",
      "codProductoSunat": "[`String` Código del producto o servicio en SUNAT, máximo 8 caracteres]",
      "codProductoGS1": "[`String` Código del producto o servicio GS1, máximo 14 caracteres]",
      "mtoValorUnitario": "[*, `Numeric` Valor de venta unitario]",
      "mtoValorVenta": "[*, `Numeric` Total venta producto]",
      "totalImpuesto": "[*, `Numeric` Total impuesto]",
      "tipAfeIgv": "[Not blank, `String` Tipo de afectación. Gravado - Operación Onerosa: 10, Gravado - Retiro por premio: 11, Gravado - Retiro por donación: 12, Gravado - Retiro: 13, Gravado - Retiro por publicidad: 14, Gravado - Bonificaciones: 15, Gravado - Retiro por entrega a trabajadores: 16, Gravado - IVAP: 17, Exonerado - Operación Onerosa: 20, Exonerado - Transferencia Gratuita: 21, Inafecto - Operación Onerosa: 30, Inafecto - Retiro por Bonificación: 31, Inafecto - Retiro: 32, Inafecto - Retiro por Muestras Médicas: 33, Inafecto - Retiro por Convenio Colectivo: 34, Inafecto - Retiro por premio: 35, Inafeto - Retiro por publicidad: 36, Exportación: 40]",
      "igv": "[*, `Numeric` Monto IGV]",
      "mtoBaseIgv": "[*, `Numeric`]",
      "porcentajeIgv": "[*, `Numeric` Porcentage de IGV]",
    ...
    },
    ...
  ],
```

## Credit note
Todos obligatorios
```js
"company": "[*, `object`]",
...
"tipoDoc": "[*,`String` Tipo de documento. Factura: 01, Boleta: 03]",
"serie": "[*,`Alphanumeric` Serie del comprobante máximo 4 dígitos]",
"correlativo": "[*,`Numeric` Correlativo del comprobante máximo 8 dígitos]",
"fechaEmision": "[*,`Datetime`]",
"tipoMoneda": "[*,`String` Tipo de modeneda según catálogo No. 02. ejemplo: PEN]",
...
"codMotivo": "[Not Balnk, `String` Código de motivo. Anulación de operación: 01, Anulación por error en el RUC: 02, Corrección por error en la descripción: 03, Descuento global: 04, Descuento por ítem: 05, Devolución total: 06, Devolución por ítem: 07, Bonificación: 08, Disminución en el valor: 09, Otros Conceptos: 10]",
"tipDocAfectado": "[Not Balnk, `String` Tipo de documento. Factura: 01]",
"numDocfectado": "[Not Balnk, `Alphanumeric` Serie mas correlativo",
"desMotivo": "[Not Balnk, `String` Descripción del motivo, máximo 30 caracteres]",
...
"totalImpuesto": "[*,`Numeric` Total inpuestos]",
"mtoImpVenta": "[*,`Numeric` Total]",
...
"client": "[*, `object`]",
...
```


## Cargos y descuentos

```js
"cargos": [
   {
     "codTipo": "[`string` Código de cargo según Catálogo No.53, OTROS CARGOS: '50', Notblank]",
     "factor": "[`Numeric`, *]",
     "monto": "[`Numeric`, *]",
     "montoBase": "[`Numeric`, *]"
   }
 ]
```

## Atributos

```js
"atributos": [
    {
      "code": "[`string`, Notblank]",
      "name": "[`string`, Notblank]",
      "value": "[`string`]",
      "fecInicio": "2023-09-01T22:06:33.902Z",
      "fecFin": "2023-09-01T22:06:33.902Z",
      "duracion": 0
    }
  ]
```

