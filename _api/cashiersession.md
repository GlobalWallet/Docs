---
title: /payment-session
position_number: 1
type: post
description: To create a payments page (cashier) session

content_markdown: |-

    {: .info }
    **Note**: The `Content-Type` header should be set to `application/json` along with the merchant API key

    {: .success }
  **Example request**

    A curl request to request the cashier:

    ```
    curl -X POST \
    'https://api.dev.kibramoa.net/payment-session' \
    -H 'accept: application/json' \
    -H 'X-API-KEY: 4rDI6o6keGvH9Di+umZj6wGkMZBE7Ukrb8+8A4WErq0=.b8987f40-e1cf-488c-843a-7a634f245a04' \
    -H 'Content-Type: application/json' \
    -d '{
    "country": "BR",
    "currency": "BRL",
    "amount": 13000,
    "redirectUrl": "https://merchant.io/where-to-go",
    "language": "ES",
    "customer": {
      "name": "John Doe",
      "email": "john@email.test",
      "phone": "+34666999666",
      "userDevice": "MOBILE",
      "userAgent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/51.0.2704.103 Safari/537.36",
      "ip": "84.232.140.77",
      "address": {
        "street": "32 Windsor Gardens",
        "streetNumber": "24",
        "country": "GB",
        "zipCode": "W9 3RG",
        "city": "London",
        "state": "Great London."
      },
      "identify": {
        "number": "76486883X",
        "type": "DNI"
      }
    },
    "merchantReference": "mustbe18cars",
    "paymentReference": "Invoice ABC123",
    "userId": "Merch_User_123",
    "extra1": "extraData001",
    "extra2": "extraData002",
    "extra3": "extraData003",
    "storedToken": "index-stored",
    "tax": "21%",
    "shippingAddress": {
      "street": "32 Windsor Gardens",
      "streetNumber": "24",
      "country": "GB",
      "zipCode": "W9 3RG",
      "city": "London",
      "state": "Great London."
    },
    "orderDetails": [
      {
        "productName": "shirt-1233474",
        "quantity": 1,
        "dimensions": "85x51",
        "description": "Blue sports t-shirt "
      }
    ]
  }'

    ```

    A successful response will return an HTTP status code of `201` and have the following schema:


    | Field   | Type   | Description                        |
    | ------- | ------ | ---------------------------------- |
    | StatusCode | string | If an error is returned the error code is shown here |
    | message | string | the CashierUrl or A message of the error             |


  
right_code_blocks:
  - code_block: |1-
        {
        
        "cashierUrl": "https://cashier.dev.kibramoa.net?sessionId=54ed4d33-9c24-4ef0-a7f8-242920a657u5"
 
        }
    title: Response
    language: json
  - code_block: |2-    
          {

          "statusCode": 401,
          "message": "Unauthorized"
          
          }
    title: Error 401
    language: json
   
---