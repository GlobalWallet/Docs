---
title: Cashier Integration
position_number: 2
parameters:
  - name:
    content:
content_markdown: |-
  CashierUI displays all the payment options available for the merchant, users can choose their favourite payment option, later the payment is managed and secured by kibramoa.

  Fast integration flow:
  - A link to CashierUI will be generated for the merchant platform after session requesting.
  - Merchant would have to be boarded and generate his API key from merchant portal in order to access CashierUI API.
  - The HTTP header must attach the Merchant API key before open a new session on the CashierUI API call.
  - When payment is completed by user, Kibramoa will redirect to merchant website and notify the payment by a webhook.
 
  ![User and merchant actions on CashierUI](/images/FLOW2.png)
left_code_blocks:
  - code_block:
    title:
    language:
right_code_blocks:
  - code_block:
    title:
    language:
---
