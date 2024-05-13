# Invoice Cancel EndPoint API

Anula una **boleta** o **factura** con una **Nota de credito** para la empresa en la que el usuario está registrado.

> Nota: La API no valida los cálculos de los montos, por lo tanto debe de calcularlos bién antes de enviarlos.

**URL** : `/api/v1/cancel-invoice`

**Method** : `POST`

**Auth required** : SI

**Campos**

```js
{
  "tipoDoc": "[`String` Tipo de documento. Factura: 01, Boleta: 03]",
  "serie": "[`Alphanumeric` Serie del comprobante máximo 4 dígitos]",
  "correlativo": "[`Numeric` Correlativo del comprobante máximo 8 dígitos]",
  "codMotivo?": "[`String` Código de motivo. Anulación de operación: 01, Anulación por error en el RUC: 02, Corrección por error en la descripción: 03, Descuento global: 04, Descuento por ítem: 05, Devolución total: 06, Devolución por ítem: 07, Bonificación: 08, Disminución en el valor: 09, Otros Conceptos: 10]",
  "desMotivo?": "[`String` Descripción del motivo]",
  "forced?": "[`Boolean` Forzar envio evitando número máximo de días]"

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
    "code": "HTTP",
    "message": "La nota de credito F001-100 esta en proceso de envio",
    "pdf": "https://nexus.fastworkx.com/12345678910/01/F001/100"
}
```

## Error Responses

**Condition** : Si alguno de los campos requeridos está vacío o contiene datos incorrectos.

**HTTP Code** : `400 BAD REQUEST`

**Content** :

```js
{
  "status": "ERROR",
  "code": "-1",
  "message": "El documento [Serie]-[Correlativo] tiene una nota de crédito asociada"
  }
}
```
