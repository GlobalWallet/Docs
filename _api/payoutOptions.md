---
title: /payout-options/{country}
position_number: 2
type: get
description: Get Payout options based on country

content_markdown: |-
  This endpoint returns all payout options based on a country. It's a GET request and a valid ISO country code must be present in the route.  

  {: .info }
  **Note**: The `Content-Type` header should be set to `application/json` along with the merchant API key

  {: .success }
  **Example request**

  ```
  GET /payout-options/BR HTTP/1.1
  Host: api.sandbox.kibramoa.net
  Accept: application/json
  X-API-KEY: pjxrlEFwzgYvP13V5LH***c8-0f95-4771-a36b-d4a928c6457d
  ```

  An error response will return an HTTP error code and the following schema:


  | Field   | Type   | Description                        |
  | ------- | ------ | ---------------------------------- |
  | statusCode | string | If an error is returned the error code is shown here |
  | message | string | the CashierUrl or A message of the error             |


  
right_code_blocks:
  - code_block: |1-
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
  - code_block: |2-    
         {
            "statusCode": 400,
            "message": [
              "Country must be 2 alpha character ISO country code."
            ]
          }
    title: Error 400
    language: json
   
---