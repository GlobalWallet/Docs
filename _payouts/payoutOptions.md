---
title: /payout-options
position_number: 1
type: post
description: Retreive all the payout options allowed for country, currency and amounts limits.

content_markdown: |-
  #### Direct API payout options endpoint

  {: .info }
  https://api.{env}.kibramoa.net/payout-options

  This endpoint returns all payout options based on a country. It's a POST request with a json body specifing country, currency and amount for the payout.  
  You can review the request and responses from kibramoa API on the right side.

  {: .info }
  **Note**: The `Content-Type` header should be set to `application/json` along with the merchant API key

  Request parameters:

  | Field   | Type   | Description                        |
  | ------- | ------ | ---------------------------------- |
  | *country | string(2) | Country code ISO alpha 2. |
  | *currency | string(3) | Currency code ISO alpha 3. |
  | *amount | integer | Amount in decimal format, I.E: 100 = 1$ |

  Success response have the following schema:

  | Field   | Type   | Description                        |
  | ------- | ------ | ---------------------------------- |
  | currencies | array | Array of strings indicating the currencies allowed. | 
  | arrivalCurrency | string | Currency of used by the destination account. | 
  | name | string | Name of the payout option. | 
  | logo | string | Payment option logo url. | 
  | formInputs | array | Array that represent a set of input fields to be filled by end-user. Refer [Test Data](#payoutsPayoutFormData) section for futher details. | 

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
        "logo": "https://kibramoa-sandbox...pix-1661669301772-400px.png",
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