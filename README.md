# Belajar Penerapan Machine Learning dengan Google Cloud

Branch ini digunakan untuk modul Studi Kasus: Membangun Aplikasi Machine
Learning Dengan Google Cloud.

# API SPESIFICATION DOCUMENTATION

### Host

https://bangkit-capstone-425206.et.r.appspot.com/

## Register

Endpoint : POST /register

#### Request Body :

```json
{
    "email": "johndoe@mail.com",
    "name": "John Doe",
    "password": "secret",
    "role": "USER" // Optional
}
```

#### Response Body (Success) :

200

```json
{
    "message": "user created",
    "status": "success"
}
```

#### Response Body (Failed) :

400

```json
{
    "status": "fail",
    "message": "Email already exists"
}
```

```json
{
    "status": "fail",
    "message": "\"password\" is required"
}
```

```json
{
    "statusCode": 400,
    "message": "Something went wrong"
}
```

## Login

Endpoint : POST /login

#### Request Body :

```json
{
    "email": "johndoe@mail.com",
    "password": "secret"
}
```

#### Response Body (Success) :

200

##### header :

authorization: Bearer token

```json
{
    "message": "logged in",
    "status": "success"
}
```

400

```json
{
    "status": "fail",
    "message": "Invalid email or password. Please try again."
}
```

```json
{
    "status": "fail",
    "message": "\"password\" is required"
}
```

## Logout

Endpoint : DELETE /logout

#### Request Body :

##### header :

authorization: Bearer token

```json
{}
```

#### Response Body (Success) :

204

```json
{}
```

#### Response Body (Failed) :

401

```json
{
    "status": "fail",
    "message": "Access denied. Please provide valid authentication credentials."
}
```

```json
{
    "status": "fail",
    "message": "Token is expired"
}
```

## Predict

Endpoint : POST /predict

#### Request Body :

##### header :

authorization: Bearer token

```json
{
    "image": image
}
```

#### Response Body (Success) :

200

```json
{
    "status": "success",
    "message": "gambar dapat diproses",
    "data": {
        "id": "17f99fd6-e371-4d7b-94e0-b97e760d8b79",
        "result": "Kering",
        "nama": "Cetaphil Moisturizing Cream",
        "bahan": "Water, Glycerin, Petrolatum, Dimethicone",
        "benefit": "Melembapkan kulit kering secara intensif, Membantu memperbaiki penghalang kelembapan alami kulit, Menenangkan kulit yang iritasi dan pecah-pecah",
        "usage": "Oleskan krim pada kulit yang bersih. Pijat lembut hingga meresap sempurna. Gunakan dua kali sehari, pagi dan malam, atau sesuai kebutuhan."
    }
}
```

#### Response Body (Failed) :

400

```json
{
    "status": "fail",
    "message": "Terjadi kesalahan dalam melakukan prediksi"
}
```

401

```json
{
    "status": "fail",
    "message": "Token is expired"
}
```

```json
{
    "status": "fail",
    "message": "Access denied. Please provide valid authentication credentials."
}
```

413

```json
{
    "status": "fail",
    "message": "Payload content length greater than maximum allowed: 1048576"
}
```

415

```json
{
    "status": "fail",
    "message": "Unsupported Media Type"
}
```
