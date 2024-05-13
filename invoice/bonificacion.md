# Invoice Endpoint API

Registra una **boleta** o **factura** para la empresa en la que el usuario está registrado
por monto cero debido a que tiene bonifificacion

> Nota: La API no valida los cálculos de los montos, por lo tanto debe de calcularlos bién antes de enviarlos.

**URL** : `/api/v1/invoice`

**Method** : `POST`

**Auth required** : SI

**Ejemplo**

```json
{
  "ublVersion": "2.1",
  "serie": "F001",
  "correlativo": "1",
  "fechaEmision": "2023-08-16T12:34:00-05:00",
  "fecVencimiento": "2023-08-16T12:34:00-05:00",
  "formaPago": {
    "tipo": "Contado",
    "monto": 0.00,
    "moneda" : "PEN"
  },
  "tipoOperacion": "0101",
  "tipoDoc": "01",
  "observacion": null,
  "legends": [
    {
      "code": 1000,
      "value": "CERO CON 00\/100 SOLES"
    },
    {
      "code": 1002,
      "value": "TRANSFERENCIA GRATUITA DE UN BIEN Y\/O SERVICIO PRESTADO GRATUITAMENTE"
    }
  ],
  "tipoMoneda": "PEN",
  "client": {
    "tipoDoc": 6,
    "numDoc": "10709303835",
    "rznSocial": "AHUINLLA VELASQUEZ EMERSON",
    "address": {
      "ubigueo": null,
      "direccion": "-",
      "codigoPais": null
    }
  },
  "mtoOperGratuitas": "200.00",
  "mtoIGVGratuitas": "36.00",
  "mtoOperGravadas": 0,
  "mtoOperExoneradas": 0,
  "mtoOperInafectas": 0,
  "valorVenta": "0.00",
  "subTotal": "0.00",
  "mtoImpVenta": "0.00",
  "details": [
    {
      "unidad": "NIU",
      "descripcion": "DESCRIPCI\u00d3N DEL PRODUCTO producto descripcion",
      "cantidad": "2",
      "mtoValorUnitario": "0.00",
      "mtoValorGratuito": "100.00",
      "mtoValorVenta": "200.00",
      "mtoBaseIgv": "200.00",
      "porcentajeIgv": 18.0,
      "igv": "36",
      "tipAfeIgv": "11",
      "totalImpuestos": "36.00",
      "mtoPrecioUnitario": "0"
    }
  ]
}
```
