---
title: /payout-session
position_number: 2
type: post
description: Initiate a payout request on Kibramoa CashierUI.

content_markdown: |-

  This endpoint will generate a payout session to the load cashierUI within the merchant system. The cashierUI will display several payout options available to the customer using the given country/currency parameters.


  {: .info }
  **Note**: The `Content-Type` header should be set to `application/json` along with the merchant API key

  {: .success }
  **Example request**

  A example request for intiate a payout on the cashier:

  ```
  POST /payout-session HTTP/1.1
  Host: api.sandbox.kibramoa.net
  X-API-KEY: pjxrlEFwzgYvP13V5LHWLZ5wiN6YHG***4771-a36b-d4a928c6457d
  Content-Type: application/json
  Content-Length: 485

  {
    "country": "BR",
    "currency": "BRL",
    "amount": 150,
    "redirectUrl": "https://merchant1.io/where/to/go",
    "merchantReference": "custom8108",
    "description": "Additional remark for this payout.",
    "userId": "merchant_user123",
    "userAgent": "Mozilla/5.0 (X11; Linux x86_64)",
    "userDevice": "DESKTOP",
    "ip": "13.12.11.10",
    "language": "PT",
    "extra1": "merchant extra value 1",
    "extra2": "merchant extra value 2",
    "extra3": "merchant extra value 3"
  }
  ```

  An error response will return an HTTP error code and have the following schema:


  | Field   | Type   | Description                        |
  | ------- | ------ | ---------------------------------- |
  | StatusCode | string | If an error is returned the error code is shown here |
  | message | string | the CashierUrl or A message of the error             |


right_code_blocks:
  - code_block: |1-
        {
        
        "cashierUrl": "https://cashier.kibramoa.net/payout/?sessionId=54ed4d33-9c24-4ef0-a7f8-242920a657u5"
 
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