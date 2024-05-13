# Despatch Endpoint API
## Transporte publico y privado

Registra una **guia remision** para la empresa en la que el usuario está registrado con transporte publico y privado

> Nota: La API no valida los cálculos de los montos o pesos, por lo tanto debe de calcularlos bién antes de enviarlos.

**URL** : `/api/v1/despatch`

**Method** : `POST`

**Auth required** : SI

## Transporte Público
al ser publico se trabaja con un transportista
**Ejemplo**

```json
{
  "company": {
    "ruc": "20123456789",
    "razonSocial": "EMPRESA DE PRUEBAS SAC",
    "nombreComercial": "EMPRESA DE PRUEBAS SAC",
    "address": {
      "ubigueo": "04001",
      "codigoPais": "PE",
      "departamento": "Lima",
      "provincia": "Chorrillos",
      "distrito": "Chorrillos",
      "urbanizacion": "Urb. Chor",
      "direccion": "Av campina mz e",
      "codLocal": "0001"
    },
    "email": "demo@demo.com",
    "telephone": "983780014"
  },
  "tipoDoc": "09",
  "serie": "T001",
  "correlativo": "704",
  "fechaEmision": "2023-04-03",
  "observation": null,
  "destinatario": {
    "tipoDoc": "6",
    "numDoc": "20123456789",
    "rznSocial": "GREENTER S.A.C."
  },
  "envio": {
    "modTraslado": "01",
    "codTraslado": "01",
    "desTraslado": "VENTA",
    "fecTraslado": "2023-04-03",
    "pesoTotal": "3999.60",
    "undPesoTotal": "KGM",
    "transportista": {
      "tipoDoc": "6",
      "numDoc": "20000000002",
      "rznSocial": "TRANSPORTES S.A.C'",
      "nroMtc": "0001"
    },
    "partida": {
      "ubigeo": "030102",
      "direccion": "URB SAN JAVIER MZ B LT 16 ABANCAY"
    },
    "llegada": {
      "ubigeo": "150101",
      "direccion": "AV LIMA"
    }
  },
  "addDocs": [ // documentos relacionados
    {
      "tipoDesc": "Factura",
      "tipo": "01",
      "nro": "F001-562",
      "emisor": "20161515648"
    }
  ],
  "details": [
    {
      "codigo": "47",
      "descripcion": "KR Y ORO 1L CJAx12",
      "unidad": "NIU",
      "cantidad": "10.00"
    }
  ]
}
```


## Transporte Privado
al ser  publico se debe registrar datos del chofer y el vehiculo
**Ejemplo**

```json
{
  "tipoDoc": "09",
  "serie": "T001",
  "correlativo": "704",
  "fechaEmision": "2023-04-03",
  "observation": null,
  "destinatario": {
    "tipoDoc": "6",
    "numDoc": "20123456789",
    "rznSocial": "GREENTER S.A.C."
  },
  "envio": {
    "modTraslado": "02",
    "codTraslado": "01",
    "desTraslado": "VENTA",
    "fecTraslado": "2023-04-03",
    "pesoTotal": "3999.60",
    "undPesoTotal": "KGM",
    "choferes": [
      {
        "tipo": "Principal",
        "tipoDoc": "1",
        "nroDoc": "44004400",
        "nombres": "ROBERTO",
        "apellidos": "RODRIGUEZ VALENCIA",
        "licencia": "0001122020"
      }
    ],
    "vehiculo": {
      "placa": "ABC123",
      "codEmisor": "string",//opcional
      "nroAutorizacion": "dfgdfg",//opcional
      "secundarios": [ //opcional
        {
          "placa": "EDF988"
        }
      ]
    },
    "partida": {
      "ubigeo": "030102",
      "direccion": "URB SAN JAVIER MZ B LT 16 ABANCAY"
    },
    "llegada": {
      "ubigeo": "150101",
      "direccion": "AV LIMA"
    }
  },
  "details": [
    {
      "codigo": "47",
      "descripcion": "KR Y ORO 1L CJAx12",
      "unidad": "NIU",
      "cantidad": "10.00"
    }
  ]
}
```
