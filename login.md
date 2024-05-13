# Login Endpoint

Se utiliza para obtener un Token que el usuario utilizará en sus consultas.

**URL** : `/api/auth/login`

**Method** : `POST`

**Auth required** : NO

**Campos**

```json
{
    "email": "[Una dirección email válida]",
    "password": "[La contraseña en texto plano]",
    "remenber_me": "[Valor booleano opcional]"
}
```

**Ejemplo**

```json
{
    "email": "example@example.com",
    "password": "secret",
    "remenber_me": false
}
```

## Success Response

**HTTP Code** : `200 OK`

**Ejemplo**

```json
{
    "access_token": "eyJ0eXAiOiJKV1hbGc...ko1lSM5j7jdDuw",
    "token_type": "Bearer",
    "expires_at": "2020-05-14 10:38:38"
}
```

## Error Response

**Condición** : Si 'email' y 'password' son incorrectos.

**HTTP Code** : `400 BAD REQUEST`


