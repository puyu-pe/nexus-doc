# Status Endpoint
Consulta del **estado del documento**

**URL** : `/api/v1/status`

**Method** : `POST`

**Auth required** : NO

**Campos**

```js
{
    "ruc" : "[`Numeric` ruc del emisior]",
    "type" : "[`Alphanumeric` según corresponda a `tipoDoc` y al Catálogo No. 06]",
    "serie" : "[`Alphanumeric` Serie del comprobante máximo 4 dígitos]",
    "correlative" : "[`Numeric` Correlativo del comprobante máximo 8 dígitos]"
}
```

**Ejemplo**

```js
{
    "ruc" : "12345678910",
    "type" : "01",
    "serie" : "F001",
    "correlative" : "200"
}
```
# Success Response

**Ejemplo**

**HTTP Code** : `200 OK`

```js
{
    "code": "3000",
    "tipoDoc": "01",
    "FechaEmision": "2019-07-16",
    "serie": "F001",
    "correlativo": 200,
    "mtoImpVenta": "15.82",
    "message": "La Factura numero F001-200, ha sido aceptada"
    "anulled": 1 // puede ser null|0|1
}
```

# Error Response

**Ejemplo**

**HTTP Code** : `400 BAD REQUEST`


```js
{
    "code": 400,
    "message": "No se encontro el documento"
}
```
