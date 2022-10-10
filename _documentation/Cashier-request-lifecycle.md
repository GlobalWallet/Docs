---
title: Cashier Payin Request Life-cycle
position_number: 5
parameters:
  - name:
    content:
content_markdown: |-
   When the API is correctly built and accepted the Kibramoa system will send back a URL with the Kibramoa cashier.
   
   Sequence diagram with the comunication process between systems:
   
   ![kibramoa cashier sequence](/images/Cashier_Request_Api_Steps.png)

   *Merchant system must always respond to notification with Http 200 code, otherwise Kibramoa API will retry at least 10 times.
---
left_code_blocks:
  - code_block: |-
    title: 
    language: 
right_code_blocks:
  - code_block:
    title:
    language:


