### API Rest Nexus

En la siguiente documentación se describe el uso del API rest de la aplicación SEE.

La dirección URL del servidor es la siguiente `https://nexus.puyu.pe`.

### Endpoints Abiertos

Los endpoints abiertos no requieren autenticación.

* [Login](./login.md): `POST /api/auth/login`
* [Status document](./status-document.md): `POST /api/auth/login`

### Endpoints que requieren autenticación

Estos endpoints requieren que en la cabecera HTTP tenga un OAuth 2.0 Token válido. Se puede adquirir un Token del endpoint **Login**, ejemplo. `Authorization: Bearer <Token>`.
#### Documentos
* [Invoice](./invoice/index.md): `POST /api/v1/invoice`  
  Operaciones relacionadas con boletas y facturas.


* [CreditNote](./note/index.md): `POST /api/v1/credit-note`  
  Operaciones relacionadas con notas de crédito


* [Despatch](./despatch/index.md): `POST /api/v1/despatch`  
  Operaciones relacionadas con

#### Otras operaciones
* [Voided](./voided.md): `POST /api/v1/voided`  
  Operaciones relacionadas con comunicaciones de baja  


* [Collection](./collection.md): `POST /api/v1/collection`  
  Operaciones relacionadas con estados masivos de documentos  


### [Validaciones UBL 2.1](./validacion-ubl21.md)


