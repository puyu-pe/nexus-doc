# Examples Invoice Tax Type

## Inafecto – Retiro por Bonificación
Segun catalogo 07  
`| 31 | Inafecto – Retiro por Bonificación | 9996 |`

```json
...
details : [
   {
      "codProducto": "P001",
      "unidad": "NIU",
      "descripcion": "PROD 1  *** BONIFICACION ***",
      "cantidad": 2,
      "mtoValorUnitario": 0.00,
      "mtoValorGratuito": 100.00,
      "mtoValorVenta": 200,
      "mtoBaseIgv": 200,
      "porcentajeIgv": 0.00,
      "igv": 0,
      "tipAfeIgv": "31",
      "totalImpuestos": 0,
      "mtoPrecioUnitario" : 0.00
    }
```

y en el header con las sumatorias quedaria como...
```json
{
...
  "mtoOperGratuitas": 200,
  "valorVenta": 0,
  "mtoImpVenta": 0,
...
}
```    

## Exonerado - Operación Onerosa
Segun catalogo 07  
`| 20 | Exonerado - Operación Onerosa | 9997 |`

```json
...
details : [
   {
      "codProducto": "P001",
      "unidad": "NIU",
      "descripcion": "PROD 1  *** EXONERADA ***",
      "cantidad": 2,
      "mtoValorUnitario": 50.00,
      "mtoValorVenta": 100,
      "mtoBaseIgv": 100,
      "porcentajeIgv": 0.00,
      "igv": 0,
      "tipAfeIgv": "20",
      "totalImpuestos": 0,
      "mtoPrecioUnitario" : 50
    }
]
```  

y en el header con las sumatorias quedaria como...
```json
{
...
  "mtoOperExoneradas": 100,
  "valorVenta": 100,
  "mtoImpVenta": 100,
...
}
```  
