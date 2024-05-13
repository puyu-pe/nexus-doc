# Despatch Endpoint API
## Transporte Emisor Itinerante (privado)

Registra una **guia remision** para la empresa en la que el usuario está registrado como emisor itinerante

> Nota: La API no valida los cálculos de los montos o pesos, por lo tanto debe de calcularlos bién antes de enviarlos.

**URL** : `/api/v1/despatch`

**Method** : `POST`

**Auth required** : SI

## Emisor Itinerante

no tiene punto de llegada, al ser itinerante

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
    "tipoDoc": "0",
    "numDoc": "-",
    "rznSocial": "Clientes varios"
  },
  "envio": {
    "modTraslado": "02",
    "codTraslado": "18",
    "desTraslado": "VENTA ITINERANTE",
    "fecTraslado": "2023-04-03",
    "pesoTotal": "3999.60",
    "undPesoTotal": "KGM",
    "vehiculo": {
      "placa": "ABI456",
      "codEmisor": "string", //opcional
      "nroAutorizacion": "string"
    },
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
    "partida": {
      "ubigeo": "030101",
      "direccion": "URB SAN JAVIER MZ B LT 16 ABANCAY"
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
### Citerios
Los criterio para la elaboracion de ese JSON es segun la sunat en
- RESOLUCION DE SUPERINTENDENCIA Nº 007-99-SUNAT
```
b) Móviles, cuando se trate de emisiones efectuadas por emisores itinerantes, tales
como distribuidores a través de vehículos, vendedores puerta a puerta, que emitan
comprobantes de pago y mantengan relación de dependencia con algún establecimiento
declarado ante la SUNAT.  
...
En el caso de traslado de bienes efectuado por emisores itinerantes de comprobantes
de pago, en las guías de remisión se podrán omitir los datos de identificación del destinatario
...

La Guía de Remisión Electrónica Remitente – GRE Remitente con motivo "traslado por emisor itinerante
de comprobantes de pago" se emite para trasladar bienes cuya venta se realizará en el trayecto,
en este caso no se conoce a los posibles clientes ni el punto fijo de llegada de los bienes vendidos,
por eso en esta guía no se consigna la información del destinatario ni la del punto de llegada.
```  

### Informacion obtenida de :
- https://cpe.sunat.gob.pe/node/122
- https://www.sunat.gob.pe/legislacion/oficios/2011/informe-oficios/i014-2011.pdf
- http://www.oas.org/juridico/PDFs/mesicic3_per_007.pdf
- https://www.perucontable.com/tributaria/traslado-de-bienes-realizados-por-emisores-itinerantes/
### Guia para la estructura de JSON
- https://github.com/thegreenter/demo/tree/master/examples
