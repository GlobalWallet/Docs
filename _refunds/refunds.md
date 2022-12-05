---
title: /refund/by-reference
position_number: 1
type: post
description: Refund a previous authorized transaction on kibramoa system. 

content_markdown: |-
  This endpoint will refund a previous authorized transaction on kibramoa system, after this process the money will return to origin account, this process cannot be undone.

  {: .info }
  **Note**: The `Content-Type` header should be set to `application/json` along with the merchant API key

  Request parameters: 

  | Field   | Type   | Description                        |
  | ------- | ------ | ---------------------------------- |
  | merchantReference | string | Reference of the transaction submitted by the merchant |

  A successful response will return an HTTP status code of `201` and have the following schema:


  | Field   | Type   | Description                        |
  | ------- | ------ | ---------------------------------- |
  | StatusCode | string | If an error is returned the error code is shown here |
  | message | string | the CashierUrl or A message of the error             |
  
right_code_blocks:
  - code_block: |1-    
        {
          "merchantReference": "your-reference"
        }
    title: Request
    language: json
  - code_block: |2-
      {  
        "statusCode": "000",
        "errorReason": "Success",
        "paymentAmount": 1000,
        "status": "REFUNDED",
        "currency": "BRL",
        "country": "BR",
        "paymentOptionName": "DepositExpress",
        "userId": "merchantUser123",
        "type": "All",
        "merchantReference": "order-1235",
        "_id": "feb6a715-9f7c-49d4-b6f7-10c59d18a194",
        "createdAt": "02/09/2021 23:02:33",
        "updatedAt": "02/09/2022 00:00:00"
      }
    title: Response
    language: json
  - code_block: |3-    
          {
            "statusCode": 400,
            "message": "Business Failed"
          }
    title: Error 401
    language: json
   
---