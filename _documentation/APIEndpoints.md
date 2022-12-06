---
title: Environment Endpoints 
position_number: 4
parameters:
  - name:
    content: 
content_markdown: |-
  
  Sandbox will be used for integrate with KibramoaAPI, all sandbox transactions are simulations with fake money. 

  Sandbox Environment URLs
  {: .success }
  - CashierUI (Hosted Payments Page):  https://cashier.sandbox.kibramoa.net
  - Direct API endpoint:  https://api.sandbox.kibramoa.net

  *Note: Check useful data section to find all related test data to use.

  Real transactions happen on production environment.

  Production Environment URLs
  {: .info }

  - CashierUI (Hosted Payments Page):  https://cashier.kibramoa.net
  - API: https://api.kibramoa.net


 
right_code_blocks:
  - code_block: |1-
      {
        "cashierUIEndpoint": "https://cashier.sandbox.kibramoa.net",
        "directAPIendpoint": "https://api.sandbox.kibramoa.net"
      }
    title: SANDBOX
    language: json
  - code_block: |2-
      {
        "cashierUIEndpoint": "https://cashier.kibramoa.net",
        "directAPIendpoint": "https://api.kibramoa.net"
      }
    title: PRODUCTION
    language: json
---