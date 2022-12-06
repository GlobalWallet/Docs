---
title: /payment-session
position_number: 2
type: post
description: Initiates a payment session on Kibramoa CashierUI regarding country and currency.

content_markdown: |-
  This endpoint will generate a payment session to the load cashierUI within the merchant system. The cashierUI will display several payment options available using the given country/currency parameters.

  {: .info }
  **Note**: The `Content-Type` header should be set to `application/json` along with the merchant API key

  Payment will take place on cashierUI interface, user will need to complete the payment accordingly to the instruction and will be redirected back to merchant website indicated on the request.

  Asynchronously Kibramoa will submit a request to the merchant server. It will be triggered once the payment result is returned from the payment processors. 

  An error response will return an HTTP error code and have the following schema:

  | Field   | Type   | Description                        |
  | ------- | ------ | ---------------------------------- |
  | StatusCode | string | If an error is returned the error code is shown here |
  | message | string | the CashierUrl or A message of the error             |
  
right_code_blocks:
  - code_block: |1-
     {
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
      }
    title: Request
    language: json
  - code_block: |2-
        {
        "cashierUrl": "https://cashier.dev.kibramoa.net?sessionId=54ed4d33-9c24-4ef0-a7f8-242920a657u5"
        }
    title: Response
    language: json
  - code_block: |3-    
          {
          "statusCode": 401,
          "message": "Unauthorized"
          }
    title: Error 401
    language: json
   
---