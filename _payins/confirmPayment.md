---
title: /confirm-payment
position_number: 3
type: post
description: Payment API endpoint to confirm a direct payment by uploading a receipt.

content_markdown: |-
  Confirm payment is an optional extra step for some processors that requires to upload the payment receipt or payment ticket by the end user.

  {: .info }
  *Note: this request is only required when /direct-payment call returns the 'receipt' action code.

  The file must have the following formats: .peg, .png, .jpg, .gif, .pdf.

  {: .info }
  Request must include the header: "Content-Type: multipart/form-data;"

  Request parameters:

  | Field   | Type   | Description                        |
  | ------- | ------ | ---------------------------------- |
  | *sessionId | string | UUID of the session generated previously. |
  | *document | string(binary) | Uploaded file string. |


  Success response have the following schema:

  | Field   | Type   | Description                        |
  | ------- | ------ | ---------------------------------- |
  | *message | string | Success text message. | 

  {: .info }
  **Note**: The `Content-Type` header should be set to `application/json` along with the merchant API key

right_code_blocks:
  - code_block: |1-
     curl -X 'POST' \
        'https://api.sandbox.kibramoa.net/confirm-payment' \
        -H 'accept: application/json' \
        -H 'X-API-KEY: qHAnwVwu6Ivfs32NZ9xrZV6V...2d6-bcca3a87e8aa' \
        -H 'Content-Type: multipart/form-data' \
        -F 'sessionId=d88605f8-99e4-493b-98c7-4bbe8ba5df33' \
        -F 'document=@Captura.JPG;type=image/jpeg'
    title: Request
    language: http
  - code_block: |2-
      {
        "message": "Success."
      }
    title: Success
    language: json
  - code_block: |3-    
       {
          "statusCode": 404,
          "message": [
            "Invalid session id."
          ]
        }
    title: Error 404
    language: json
---