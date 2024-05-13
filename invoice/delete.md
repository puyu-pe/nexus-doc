# Invoice DELETE EndPoint API

Elimina una **boleta**, **factura** y **Nota de credito** para la empresa en la que el usuario está registrado, siempre y cuando se encuentre pendiente de envio **HTTP** el ``code_sunat``.


**URL** : `/api/v1/delete-invoice`

**Method** : `POST`

**Auth required** : SI

**Campos**

```js
{
  "tipoDoc": "[`String` Tipo de documento. Factura: 01, Boleta: 03]",
  "serie": "[`Alphanumeric` Serie del comprobante máximo 4 dígitos]",
  "correlativo": "[`Numeric` Correlativo del comprobante máximo 8 dígitos]",
}
```

**Ejemplo**

```json
{
  "tipoDoc": "01",
  "serie": "F001",
  "correlativo": 100
}
```

## Success Response

**HTTP Code** : `200 OK`

**Ejemplo**

```json
{
    "status": "OK",
    "message": "El documento se elimino correctamente"
}
```

## Error Responses

**Condition** : Si no se encuentra con **HTTP** el ``code_sunat``.

**HTTP Code** : `400 BAD REQUEST`

**Content** :

```js
{
  "status": "ERROR",
  "message": "El documento no se encuentra pendiente de envio"
  }
}
```

**Condition** : Si no existe el documento.

**HTTP Code** : `400 BAD REQUEST`

**Content** :

```js
{
  "status": "ERROR",
  "message": "No se encontro el documento"
  }
}
```
