---
title: Payout Form Data
position_number: 3
type: Data
description: Direct payouts requires to get certains details from end-users in order to complete /payout-session request.

content_markdown: |-
  Form data details comes from the response retreived from /payout-options, indicated on the array "formInputs".

  | **Parameter**   | **Data Type** | **Example**                     | **Description** |
  | label\*         | string    | Bank Code        | Input label name to display. |
  | name\*          | string    | bankCode         | Name of the input to submit. |
  | type\*          | string    | select   | Type of the input to render, supported types: string, select, boolean. |
  | values\*        | array     | [ {"value": "0001", "name": "TEST BANK"} ] | Array of objects that indicates values for the input field. |
  | required\*      | boolean   | true   | Indicates if the input field is required. |
  | validations     | object    | { "minLength": 5, "maxLength": 100 } | Record object to indicate some extra validations. |

  {: .warning }
  **Note**: Integration must process this array of inputs and build later the request on the formData object to be submited on /direct-payout call.

right_code_blocks:
  - code_block: |1-
     {
        ...
        "formInputs": [
            {
                "label": "Beneficiary's name",
                "name": "name",
                "type": "string",
                "values": [],
                "required": true,
                "queryOptions": null,
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
                "queryOptions": null,
                "validations": null
            },
            {
                "label": "Beneficiary's email",
                "name": "email",
                "type": "string",
                "values": [],
                "required": false,
                "queryOptions": null,
                "validations": null
            },
            {
                "label": "Beneficiary's PIX account type",
                "name": "account_type",
                "type": "select",
                "values": [
                    {
                        "value": "CPF",
                        "name": "CPF"
                    },
                    {
                        "value": "PHONE",
                        "name": "Phone"
                    },
                    {
                        "value": "EMAIL",
                        "name": "Email"
                    }
                ],
                "required": true,
                "queryOptions": null,
                "validations": null
            }
            ...
          ]
    title: Form Inputs array example
    language: json
  - code_block: |2-
        {
          "country": "BR",
          "currency": "BRL",
          "option": "PIX", 
          "amount": 150.00,
          "redirectUrl": "https://merchant1.io/where/to/go",
          "merchantReference": "customRef-999",
          "description": "Additional remark for this payout.",
          "userId": "merchant_user123",
          "ip": "13.12.11.10",
          "extra1": "merchant extra value 1",
          "extra2": "merchant extra value 2",
          "extra3": "merchant extra value 3",
          "formData": {
              "name": "John Doe",
              "account_type": "EMAIL",
              "account": "merchant@pagsmile.com",
              "document_type": "CPF",
              "document_id": "50284414727"
          }
        }
    title: Direct payout example
    language: json

---