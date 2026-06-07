# JaneShop OpenAPI Specification

## Overview

This repository contains an OpenAPI 3.0.3 specification for the JaneShop Product APIs.


## API Information

| Field | Value |
|---------|---------|
| OpenAPI Version | 3.0.3 |
| API Title | JaneShop Products APIs Definition |
| API Version | 0.0.1 |

### About JaneShop

JaneShop is described as an open marketplace product-selling platform where third-party websites can list products through APIs. JaneShop manages shipping and logistics while affiliates earn commissions on sales.

### Supported Categories

- Mobiles
  - Apple
  - Samsung
  - OnePlus
- Laptops
- Televisions
- Headphones

## Metadata

### Custom Vendor Extension

```yaml
x-custom-info:
  comment: Some comments
  developers:
    - John Doe
    - Jane Doe
```

### Contact Information

- Name: API Support
- Email: support@janeshop.com
- Support URL: https://www.janeshop.com/support

### Terms & License

- Terms of Service: https://janeshop.com/terms/
- License: JaneShop License

### External Documentation

https://example.com/docs

## Server

### Development Server

```text
https://development.janeshop-server.com/v1
```

## Tags

- Categories
- Products
- Orders

## Security Schemes Used

Global security requirements include:

- Basic Authentication
- Bearer Authentication
- API Key Authentication
- OAuth2 Authorization Code Flow

OAuth scopes:

- read
- write
- admin

---

# API Endpoints

## Categories

### GET /categories

Returns the list of categories supported by JaneShop.

#### Query Parameters

| Name | Type | Description |
|------|------|-------------|
| categoryId | integer | Category identifier (100–1000) |

#### Example Values

- 101 = Mobiles
- 102 = Laptops
- 103 = Headphones
- 104 = Televisions

#### Responses

- 200 OK → Array of Category objects
- 500 Internal Server Error

---

### GET /categories/{categoryId}

Returns details for a single category.

#### Path Parameters

| Name | Type |
|------|------|
| categoryId | integer |

#### Responses

- 200 OK → Category object
- 500 Internal Server Error

---

## Products

### GET /products

Returns all products.

#### Query Parameters

| Name | Type |
|------|------|
| categoryId | integer |

#### Responses

- 200 OK → Array of Product objects
- 500 Internal Server Error

#### Example Products

- Apple iPhone 13 Pro
- Samsung S22 Ultra
- OnePlus 10 Pro 5G

---

### GET /products/{productId}

Returns details for a single product.

#### Path Parameters

| Name | Type |
|------|------|
| productId | integer |

#### Responses

- 200 OK → Product object
- 500 Internal Server Error

---

## Orders

### POST /orders

Creates a new order.

#### Request Body

```json
{
  "products": [],
  "address": {}
}
```

#### Success Response

```json
{
  "orderId": 123
}
```

Returns:

- 201 Created
- 500 Internal Server Error

The specification defines a link named:

```yaml
GetOrderByOrderId
```

---

### PUT /orders

Updates an existing order.

#### Request Body

```json
{
  "orderId": 123,
  "products": [],
  "address": {}
}
```

Used to update an existing order.

---

# Schemas Referenced

The specification references the following reusable schemas:

- Category
- Product
- Address

Additional reusable OpenAPI components are also referenced:

- InternalServerError response
- GetOrderByOrderId link
- Authentication security schemes

## Example Category Object

```json
{
  "categoryId": 101,
  "name": "Mobiles"
}
```

## Example Product Object

```json
{
  "productId": 101,
  "name": "Apple iPhone 13 Pro",
  "price": 999.88,
  "categoryName": "Mobiles",
  "quantity": 96
}