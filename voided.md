# Anulaciones
## Voided Endpoint
Cambia a anullado para generar **comunicacion de baja**

**URL** : `/api/v1/voided`

**Method** : `POST`

**Auth required** : YES

**Campos**

```js
{
    "type" : "[`Alphanumeric` según corresponda a `tipoDoc` y al Catálogo No. 06]",
    "serie" : "[`Alphanumeric` Serie del comprobante máximo 4 dígitos]",
    "correlative" : "[`Numeric` Correlativo del comprobante máximo 8 dígitos]"
    "reason" : "[`Alphanumeric` Motivo de anulacion]"
}
```

**Ejemplo**

```js
{
    "type" : "01",
    "serie" : "F001",
    "correlative" : "20"
    "reason" : "ERROR RUC"
}
```
### Success Response

**Ejemplo**

**HTTP Code** : `200 OK`

```js
{
    "message": "El comprobante F001 - 19 esta en proceso de comunicación de baja"
}
```

### Error Response

**Ejemplo**

**HTTP Code** : `400 BAD REQUEST`


```js
{
    "message": "No se encontro el documento"
}
```
