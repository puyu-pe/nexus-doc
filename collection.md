# Collection Endpoint
Lista de comprobantes según la **fecha inicio** y la **fecha final**

**URL** : `/api/v1/collection`

**Method** : `POST`

**Auth required** : SI

**Campos**

```js
{
	"ruc" : "[`Alphanumeric` según corresponda a `tipoDoc` y al Catálogo No. 06]",
	"start_date" : "[`date` formato (YY-mm-dd) para la fecha de inicio]",
	"end_date" : "[`date` formato (YY-mm-dd) para la fecha final]"
}
```

**Ejemplo**

```js
{
    "ruc" : "12345678910",
    "start_date" : "2019-07-16",
    "end_date" : "2019-07-16"
}
```
# Success Response


**HTTP Code** : `200 OK`

**Ejemplo**

```js
[
    {
        "id": 2,
        "code_sunat": "3000",
        "message_sunat": "La Factura número F001-200, se encuentra en proceso de envío.",
        "tipoDoc": "01",
        "fechaEmision": "2019-07-16",
        "serie": "F001",
        "correlativo": 200,
        "mtoImpVenta": "15.82",
        "cpeJSON": "{json}",
        "hashCpe": "NfqMSI+9+tdtcnzBkNr2woRqU8M="
    }
]
```

# Error Response

**Ejemplo**

**HTTP Code** : `400 BAD REQUEST`

```js
{
    "code": 400,
    "message": "BAD REQUEST"
}
```
