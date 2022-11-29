---
title: /direct-payout
position_number: 2
type: post
description: Initiates a Direct Payout session on Kibramoa CashierUI.

content_markdown: |-

  This endpoint will generate a direct payout session within the merchant system.

  {: .info }
  **Note**: The `Content-Type` header should be set to `application/json` along with the merchant API key

  {: .success }
  **Example request**

  Body request example for create cashier payment session:

  ```
  POST /direct-payout
  Host: api.sandbox.kibramoa.net
  X-API-KEY: pjxrlEFwzgYvP13V5LHWLZ5wiN6YHGKA****8-0f95-4771-a36b-d4a928c6457d
  Content-Type: application/json
  Content-Length: 1387

  {
  "country": "BR",
  "currency": "BRL",
  "option": "PIX",
  "amount": 150,
  "redirectUrl": "https://merchant1.io/where/to/go",
  "merchantReference": "custom8626666",
  "description": "Additional remark for this payout.",
  "userId": "merchant_user123",
  "ip": "13.12.11.10",
  "extra1": "merchant extra value 1",
  "extra2": "merchant extra value 2",
  "extra3": "merchant extra value 3",
  "formData": {
        "name": "PIX",
        "logo": "https://kibramoa-sandbox.s3.eu-west-1.amazonaws.com/payment-options/79a14f6d-b026-44cf-a829-07900884ff0d/pix-1661669301772-400px.png",
        "currencies": [
            "USD",
            "EUR",
            "GBP",
            "BRL"
        ],
        "arrivalCurrency": "BRL",
        "phone": "",
        "email": "",
        "account_type": "CPF",
        "account": "string",
        "document_type": "CPF",
        "document_id": "Doc12354"
     }
   } 
  ```

  An error response will return an HTTP error code and have the following schema:


  | Field   | Type   | Description                        |
  | ------- | ------ | ---------------------------------- |
  | StatusCode | string | If an error is returned the error code is shown here |
  | message | string | the success message or a message of the error             |


  
right_code_blocks:
  - code_block: |1-
        {
        
        "result": "Payout request was submitted successfully."
 
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