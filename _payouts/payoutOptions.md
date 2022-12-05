---
title: /payout-options
position_number: 1
type: post
description: Retreive all the payout options allowed for country, currency and amounts limits.

content_markdown: |-
  This endpoint returns all payout options based on a country. It's a POST request with a json body specifing country, currency and amount for the payout.  
  You can review the request and responses from kibramoa API on the right side.

  {: .info }
  **Note**: The `Content-Type` header should be set to `application/json` along with the merchant API key

  Request parameters:

  | Field   | Type   | Description                        |
  | ------- | ------ | ---------------------------------- |
  | country | string(2) | Country code ISO alpha 2. |
  | currency | string(3) | Currency code ISO alpha 3. |
  | amount | integer | Amount in decimal format, I.E: 100 = 1$ |

  An error response will return an HTTP error code and the following schema:

  | Field   | Type   | Description                        |
  | ------- | ------ | ---------------------------------- |
  | statusCode | string | If an error is returned the error code is shown here |
  | message | string | the CashierUrl or A message of the error             |

right_code_blocks:
  - code_block: |1-    
     {
        "country": "BR",
        "currency": "BRL",
        "amount": 1500
     }
    title: Request
    language: json
  - code_block: |2-
      [
        {
        "name": "Bank Transfer",
        "logo": null,
        "currencies": [
            "USD",
            "EUR",
            "GBP",
            "BRL"
        ],
        "arrivalCurrency": "BRL",
        .....
        },
        {
        "name": "PIX",
        "logo": "https://kibramoa-sandbox.s3.eu-west-1.amazonaws.com/payment-options/79a14f6d-b026-44cf-a829-07900884ff0d/pix-1661669301772-400px.png",
        "currencies": [
            "USD",
            "EUR",
            "GBP",
            "BRL"
        ],
        "arrivalCurrency": "BRL",
        "formInputs": [
            {
                "label": "Beneficiary's name",
                "name": "name",
                "type": "string",
                "values": [],
                "required": true,
                "validations": {
                    "minLength": 5,
                    "maxLength": 100
                }
            },
            {
                "label": "Beneficiary's phone",
                "name": "phone",
                "type": "string",
                "values": [],
                "required": false,
                "validations": null
            },
        ],
        .....
        }
      ]
    title: Response
    language: json
  - code_block: |3-    
         {
            "statusCode": 400,
            "message": [
              "Country must be 2 alpha character ISO country code."
            ]
          }
    title: Error 400
    language: json
   
---