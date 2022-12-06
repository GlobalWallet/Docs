---
title: Direct API overview
position_number: 1
parameters:
  - name:
    content:
content_markdown: |-
  Direct API allow merchants to create their own payment page, providing all the required data to:

  - Initiate a payment through your back-end to Kibramoa.
  - You will get all the available payment options to be rendered.
  - Display all supported banks.
  - Trigger actions to complete the payment, such redirections, receipts or QrCodes.

  ![kibramoa Direct API sequence](/images/directAPIflow.svg)

  Notification callback always will be triggered after the comunication with the payment processor is completed or closed. Merchants must always response with 200 HTTP status, otherwise notification will be triggered again up to 10 times.
  
  #### *Note: transactions notified with ERROR status are never processed due to validation or networking issues.

left_code_blocks:
  - code_block:
    title:
    language:
right_code_blocks:
  - code_block:
    title:
    language:
---
