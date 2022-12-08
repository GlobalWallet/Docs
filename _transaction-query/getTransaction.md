---
title: /payments/{transactionId}
position_number: 1
type: get
description: Get transaction details from kibramoa. 

content_markdown: |-
  Return all details about the transaction, GET request and a valid transactionId must be present in the route and should match with an uuid in kibramoa transaction DB. 

  {: .info }
  **Note**: The `Content-Type` header should be set to `application/json` along with the merchant API key

  For more details about the transaction object, please check useful data section.

right_code_blocks:
  - code_block: |1-
     GET /payments/099cdc76-45d1-49e1-8985-e1c82dcfadb3 HTTP/1.1
     Host: api.sandbox.kibramoa.net
     Accept: application/json
     X-API-KEY: pjxrlEFwzgYvP13V5LH***c8-0f95-4771-a36b-d4a928c6457d
    title: Request
    language: http
  - code_block: |2-
      {
        "id": "099cdc76-45d1-49e1-8985-e1c82dcfadb3",
        "sessionId": "90545ca3-fe0d-457c-a9da-283ee2561d82",
        "country": "GB",
        "currency": "GBP",
        "paymentAmount": 1000,
        "method": "Bank Transfer",
        "status": "COMPLETED",
        "paymentReference": "invoice-4726",
        "merchantReference": "merchant-order-8271",
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
            "productName": "shirt-328471",
            "dimensions": "85x51",
            "description": "Blue sports t-shirt "
          }
        ],
        "errors": {
          "code": "999",
          "msg": "Business failed - duplicate order number"
        },
        "createdAt": "2022-08-04T08:23:50.738Z",
        "updatedAt": "2022-08-05T08:23:50.738Z"
       }
    title: Response
    language: json
  - code_block: |3-    
         {
            "statusCode": 404,
            "message": [
              "Transaction not found."
            ]
          }
    title: Error 404
    language: json
   
---