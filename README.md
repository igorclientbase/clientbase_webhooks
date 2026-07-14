# Base de Clientes - Simplifique a Gestão de Clientes e Cobranças Recorrentes

**Base de Clientes** oferece uma solução completa para quem precisa gerenciar clientes e cobranças de forma eficiente e automatizada. Com funcionalidades que vão desde o cadastro e assinatura digital de contratos até a emissão de notas fiscais e notificações automatizadas, a Base de Clientes garante uma gestão financeira simplificada e eficaz para diversos setores como escolas, academias, agências, contabilidade e SaaS.

Para mais informações, visite nosso site: [Base de Clientes](https://basedeclientes.com.br).

---

## Webhooks

Para configurar os webhooks, é necessário solicitar a configuração fornecendo os seguintes dados:
- **URL**: Endpoint para onde os dados serão enviados.
- **Verbo**: Método HTTP a ser usado (POST ou PUT).
- **Token de Autenticação** (opcional, mas fortemente recomendado).
- **Lista de Eventos**: Eventos que deseja receber notificações.

### Billings
Os eventos de **Billings** são relacionados às cobranças emitidas. Cada status representa um estágio diferente no ciclo de vida da cobrança:

- **billing.pending**: Cobrança pendente, ainda não foi emitida.
- **billing.created_payment**: Status intermediário, cobrança está sendo aberta para pagamento.
- **billing.open_payment**: Cobrança está aberta e aguardando pagamento.
- **billing.overdue**: Cobrança está em atraso. Data de Vencimento + 1 dia.
- **billing.expiring**: Cobrança não foi paga e solicitamos os cancelamentos dos payments da fatura. (boleto, pix e/ou cartão).
- **billing.no_payment**: Cobrança não foi paga e a fatura expirou.
- **billing.paid**: Cobrança foi paga.
- **billing.cancelling**: Cobrança está em processo de cancelamento.
- **billing.cancelled**: Cobrança foi cancelada.

Exemplo de payload para Billings:

```json
{
  "event": "billing.paid",
  "payload": {
    "status": "paid",
    "description": "Pagamento referente à inscrição e consultoria avançada em estratégias de crescimento de negócios no segmento de tecnologia.",
    "due_date": "2024-07-23",
    "amount_billed": "1023.4",
    "interest_policy": "no_interest",
    "discount_policy": "no_discount",
    "discount_days": 0,
    "discount_amount": "0.0",
    "created_at": "2024-07-23T21:01:39.428-03:00",
    "updated_at": "2024-07-24T06:00:39.357-03:00",
    "uuid": "d9e8a3c2-b45a-4a98-b9f7-f4b8d9c1a5ef",
    "recurrence_cycle": 0,
    "dirty": false,
    "payment_type": "boleto;boleto_pix",
    "amount_paid": "1023.4",
    "date_paid": "2024-07-23",
    "antecipated": false,
    "issued": true,
    "viewed": false,
    "email_invoice_status": "no_state",
    "sms_invoice_status": "no_state",
    "whatsapp_invoice_status": "no_state",
    "interest_fine": null,
    "interest_fee": null,
    "expiration_date": "2024-09-21",
    "can_issue": true,
    "source": "base",
    "nfse_policy": "no_nfse",
    "billing_items": [
      {
        "uuid": "6918256d-4648-4993-90c7-dabbc43e3f36",
        "description": null,
        "amount_billed": "540.0",
        "amount_unit": "90.0",
        "quantity": "6.0",
        "billable_type": "Billing",
        "created_at": "2024-07-23T21:01:39.454-03:00",
        "updated_at": "2024-07-23T21:01:39.454-03:00",
        "product": {
          "uuid": "f1315678-4265-4191-b566-d88638991321",
          "name": "Consultoria Avançada",
          "amount": "90.0"
        }
      },
      {
        "uuid": "e2e1f3c2-43d7-40bc-b397-fb95bb7f114a",
        "description": null,
        "amount_billed": "483.4",
        "amount_unit": "241.7",
        "quantity": "2.0",
        "billable_type": "Billing",
        "created_at": "2024-07-23T21:01:39.458-03:00",
        "updated_at": "2024-07-23T21:01:39.458-03:00",
        "product": {
          "uuid": "c949e6ce-70b4-4ac8-a197-a47582f9f021",
          "name": "Inscrição Premium",
          "amount": "241.7"
        }
      }
    ],
    "payments": [
      {
        "status": "cancelled",
        "due_date": "2024-07-23",
        "amount_billed": "1023.4",
        "date_paid": null,
        "amount_paid": "0.0",
        "fee": "0.0",
        "created_at": "2024-07-23T21:01:39.971-03:00",
        "updated_at": "2024-07-24T06:00:38.497-03:00",
        "payment_type": "boleto_pix",
        "uuid": "a7b4c3d9-2e6f-4d9b-81f6-9a8e7f5b2c4d",
        "date_no_payment": "2024-07-24",
        "modified": null,
        "paymentable": {
          "emv": "00020101021226820014BR.GOV.BCB.PIX2560api.itau/pix/qr/v2/cobv/6d59c7e1-13d9-4d57-8323-4b27fef18f92x204000053039865802BR5915EXEMPLAR LTDA6008CITY62070503***6304F8C9",
          "expiration_date": "2024-09-21T23:59:59.999-03:00",
          "status": "canceled"
        },
        "customer_uuid": "12abf34d-9e8f-4d4b-81c3-45e3f6d7a1a9",
        "merchant_uuid": "f6c8d7e3-4d2b-4a5e-b9e8-8c6f7d9a1b5d",
        "billing_uuid": "d9e8a3c2-b45a-4a98-b9f7-f4b8d9c1a5ef"
      },
      {
        "status": "paid",
        "due_date": "2024-07-23",
        "amount_billed": "1023.4",
        "date_paid": "2024-07-23",
        "amount_paid": "1023.4",
        "fee": "2.99",
        "created_at": "2024-07-23T21:01:39.461-03:00",
        "updated_at": "2024-07-24T06:00:37.197-03:00",
        "payment_type": "boleto",
        "uuid": "c3b8d7a1-4e5f-4b9d-93e6-f1b7c8a2d9e4",
        "date_no_payment": null,
        "modified": null,
        "paymentable": {
          "barcode": "23794876500002000000001370065543682900050123",
          "line": "23794.87650  00670.065543  37000.050123  5  98100002000000",
          "our_number": "00765436829",
          "status": "succeeded"
        },
        "customer_uuid": "12abf34d-9e8f-4d4b-81c3-45e3f6d7a1a9",
        "merchant_uuid": "f6c8d7e3-4d2b-4a5e-b9e8-8c6f7d9a1b5d",
        "billing_uuid": "d9e8a3c2-b45a-4a98-b9f7-f4b8d9c1a5ef"
      }
    ],
    "customer": {
      "status": "active",
      "name": "Alex Ribeiro",
      "nickname": null,
      "document": "57891234567",
      "email": "contact@example.com",
      "phone": "5531998765432",
      "created_at": "2024-07-23T20:26:51.691-03:00",
      "updated_at": "2024-07-23T20:26:51.691-03:00",
      "uuid": "12abf34d-9e8f-4d4b-81c3-45e3f6d7a1a9",
      "source": "link_customer"
    },
    "product": {
      "uuid": "343c72fd-dad0-454b-9fea-4e99586fa5d7",
      "status": "active",
      "name": "Nome do produto",
      "description": "Descrição do produto",
      "amount": "2000.0"
    },
    "product_link": {
      "uuid": "7c82fd-dad0-454b-9fea-4e99asdsa83",
      "title": "Título do link"
    },
    "customer_uuid": "12abf34d-9e8f-4d4b-81c3-45e3f6d7a1a9",
    "merchant_uuid": "f6c8d7e3-4d2b-4a5e-b9e8-8c6f7d9a1b5d",
    "recurrence_uuid": null,
    "amount_updated": 0.1023e4,
    "nfse_status": "not_scheduled"
  }
}
```

### Credit Card Charges
Os eventos de **Credit Card Charges** cobrem tanto as tentativas de cobrança no cartão de crédito quanto as falhas no cadastro do cartão:

- **credit_card_charge.failed**: Falha em uma operação de cartão de crédito. Disparado em três situações:
  - **Cobrança recusada** no pagamento de uma cobrança.
  - **Cobrança recorrente recusada** na retentativa automática de uma assinatura.
  - **Erro ao cadastrar o cartão** (falha na tokenização junto ao adquirente), quando o cliente informa os dados do cartão para pagar uma cobrança.

O campo `description` identifica o motivo. Nos casos de erro de cadastro, os valores possíveis são `Número de cartão inválido`, `Cartão recusado pelo banco emissor` e `Falha no cadastro do cartão`.

Exemplo de payload para Credit Card Charges:

```json
{
  "event": "credit_card_charge.failed",
  "payload": {
    "credit_card_charge": {
      "uuid": "a1b2c3d4-5678-90ab-cdef-1234567890ab",
      "status": "unathorized",
      "description": "Cartão recusado - Saldo insuficiente",
      "created_at": "2024-07-23T21:05:30.123-03:00"
    },
    "credit_card": {
      "uuid": "b2c3d4e5-6789-01bc-def2-3456789012bc",
      "last_4_digits": "1234",
      "first_4_digits": "4111",
      "card_brand": "visa",
      "holder_name": "ALEX RIBEIRO",
      "expiration_month": 12,
      "expiration_year": 2026
    },
    "billing": {
      "status": "open_payment",
      "description": "Mensalidade - Plano Premium",
      "due_date": "2024-07-23",
      "amount_billed": "199.90",
      "interest_policy": "no_interest",
      "discount_policy": "no_discount",
      "discount_days": 0,
      "discount_amount": "0.0",
      "created_at": "2024-07-20T10:00:00.000-03:00",
      "updated_at": "2024-07-23T21:05:30.456-03:00",
      "uuid": "d9e8a3c2-b45a-4a98-b9f7-f4b8d9c1a5ef",
      "recurrence_cycle": 3,
      "dirty": false,
      "payment_type": "credit_card",
      "amount_paid": "0.0",
      "date_paid": null,
      "antecipated": false,
      "issued": true,
      "viewed": true,
      "email_invoice_status": "sent",
      "sms_invoice_status": "no_state",
      "whatsapp_invoice_status": "no_state",
      "interest_fine": null,
      "interest_fee": null,
      "expiration_date": "2024-08-22",
      "can_issue": true,
      "source": "base",
      "nfse_policy": "no_nfse",
      "billing_items": [
        {
          "uuid": "6918256d-4648-4993-90c7-dabbc43e3f36",
          "description": null,
          "amount_billed": "199.90",
          "amount_unit": "199.90",
          "quantity": "1.0",
          "billable_type": "Billing",
          "created_at": "2024-07-20T10:00:00.000-03:00",
          "updated_at": "2024-07-20T10:00:00.000-03:00",
          "product": {
            "uuid": "f1315678-4265-4191-b566-d88638991321",
            "name": "Plano Premium",
            "description": "Acesso completo a todas as funcionalidades",
            "amount": "199.90",
            "total_cycles": 12
          }
        }
      ],
      "payments": [
        {
          "status": "failed",
          "due_date": "2024-07-23",
          "amount_billed": "199.90",
          "date_paid": null,
          "amount_paid": "0.0",
          "fee": "0.0",
          "created_at": "2024-07-23T21:05:00.000-03:00",
          "updated_at": "2024-07-23T21:05:30.123-03:00",
          "payment_type": "credit_card",
          "uuid": "a7b4c3d9-2e6f-4d9b-81f6-9a8e7f5b2c4d",
          "date_no_payment": null,
          "modified": null,
          "customer_uuid": "12abf34d-9e8f-4d4b-81c3-45e3f6d7a1a9",
          "merchant_uuid": "f6c8d7e3-4d2b-4a5e-b9e8-8c6f7d9a1b5d",
          "billing_uuid": "d9e8a3c2-b45a-4a98-b9f7-f4b8d9c1a5ef"
        }
      ],
      "customer": {
        "status": "active",
        "name": "Alex Ribeiro",
        "nickname": null,
        "document": "57891234567",
        "email": "contact@example.com",
        "phone": "5531998765432",
        "created_at": "2024-07-23T20:26:51.691-03:00",
        "updated_at": "2024-07-23T20:26:51.691-03:00",
        "uuid": "12abf34d-9e8f-4d4b-81c3-45e3f6d7a1a9",
        "source": "link_customer",
        "metadata": [],
        "address": {
          "street": "Rua das Flores",
          "number": "123",
          "complement": "Apto 45",
          "neighborhood": "Centro",
          "city": "São Paulo",
          "state": "SP",
          "zip_code": "01234-567"
        }
      },
      "credit_card_charges": [
        {
          "uuid": "a1b2c3d4-5678-90ab-cdef-1234567890ab",
          "status": "unathorized",
          "description": "Cartão recusado - Saldo insuficiente",
          "created_at": "2024-07-23T21:05:30.123-03:00"
        }
      ],
      "customer_uuid": "12abf34d-9e8f-4d4b-81c3-45e3f6d7a1a9",
      "merchant_uuid": "f6c8d7e3-4d2b-4a5e-b9e8-8c6f7d9a1b5d",
      "recurrence_uuid": "c4d5e6f7-8901-23cd-ef45-6789012345cd"
    }
  }
}
```

### Recurrences
Os eventos de **Recurrences** são relacionados às recorrências de pagamento. Cada status representa um estágio diferente no ciclo de vida da recorrência:

- **recurrence.pending**: Recorrência pendente, aguardando ativação.
- **recurrence.active**: Recorrência ativa e gerando cobranças.
- **recurrence.cancelled**: Recorrência foi cancelada.
- **recurrence.finished**: Recorrência foi finalizada após completar todos os ciclos.
- **recurrence.updated**: Recorrência foi atualizada com novas informações.
- **recurrence.credit_card_assigned**: Foi cadastrado um cartão de crédito na Recorrência
- **recurrence.readjusted**: Um reajuste foi aplicado na recorrência, alterando o valor.
- **recurrence.adjustment_pending**: Há um reajuste manual aguardando confirmação, com data prevista para o próximo mês.

Exemplo de payload para Recurrences:

```json
{
  "event": "recurrence.updated",
  "payload": {
    "uuid": "4ca92d00-c214-494e-ae62-f021cc5c462b",
    "status": "active",
    "frequency": "monthly",
    "total_cycles": 0,
    "due_day": 25,
    "first_due_date": "2025-03-25",
    "amount": "806.64",
    "interest_policy": "custom",
    "discount_days": 0,
    "discount_amount": "0.0",
    "description": null,
    "created_at": "2025-03-25T13:52:14.441-03:00",
    "updated_at": "2025-03-25T13:52:16.368-03:00",
    "payment_type": "pix",
    "discount_policy": "tiers",
    "current_cycle": 1,
    "interest_fine": "2.0",
    "interest_fee": "1.0",
    "credit_card_recurring": false,
    "recurrence_type": "constant",
    "nfse_policy": "no_nfse",
    "limit_days_for_payment": 60,
    "product_quantity": 1,
    "discounts": [
      {
        "uuid": "b3ee9d1b-a8e8-4fcc-928a-a5521be26f83",
        "policy": "fixed",
        "days": 0,
        "amount": "10.0",
        "created_at": "2025-03-25T13:52:14.451-03:00",
        "updated_at": "2025-03-25T13:52:14.451-03:00",
        "discountable_type": "Recurrence"
      }
    ],
    "customer": {
      "status": "active",
      "name": "João Silva",
      "nickname": null,
      "document": "12345678900",
      "email": "joao.silva@example.com",
      "phone": "5511999999999",
      "created_at": "2025-03-19T14:52:59.822-03:00",
      "updated_at": "2025-03-19T14:52:59.822-03:00",
      "uuid": "169f912c-7d4d-489f-9622-3c0ca3e3c9d3",
      "source": "product_link",
      "email_block": 0
    },
    "billing_items": [
      {
        "uuid": "6918256d-4648-4993-90c7-dabbc43e3f36",
        "description": null,
        "amount_billed": "540.0",
        "amount_unit": "90.0",
        "quantity": "6.0",
        "billable_type": "Recurrence",
        "created_at": "2025-03-25T13:52:14.454-03:00",
        "updated_at": "2025-03-25T13:52:14.454-03:00",
        "product": {
          "uuid": "f1315678-4265-4191-b566-d88638991321",
          "name": "Produto A",
          "amount": "90.0"
        }
      },
      {
        "uuid": "e2e1f3c2-43d7-40bc-b397-fb95bb7f114a",
        "description": null,
        "amount_billed": "266.64",
        "amount_unit": "22.22",
        "quantity": "12.0",
        "billable_type": "Recurrence",
        "created_at": "2025-03-25T13:52:14.458-03:00",
        "updated_at": "2025-03-25T13:52:14.458-03:00",
        "product": {
          "uuid": "c949e6ce-70b4-4ac8-a197-a47582f9f021",
          "name": "Produto B",
          "amount": "22.22"
        }
      }
    ],
    "billings": [
      {
        "status": "pending",
        "description": null,
        "due_date": "2026-02-25",
        "amount_billed": "806.64",
        "interest_policy": "custom",
        "discount_policy": "tiers",
        "discount_days": 0,
        "discount_amount": "0.0",
        "created_at": "2025-03-25T13:52:16.282-03:00",
        "updated_at": "2025-03-25T13:52:16.282-03:00",
        "uuid": "62233b40-fa89-4508-a79c-b8505db7128e",
        "recurrence_cycle": 12,
        "dirty": false,
        "payment_type": "pix",
        "amount_paid": "0.0",
        "date_paid": null,
        "antecipated": false,
        "issued": false,
        "viewed": false,
        "email_invoice_status": "no_state",
        "sms_invoice_status": "no_state",
        "whatsapp_invoice_status": "no_state",
        "interest_fine": "2.0",
        "interest_fee": "1.0",
        "expiration_date": "2026-04-26",
        "can_issue": true,
        "source": "base",
        "nfse_policy": "no_nfse",
        "issue_date": "2026-02-13",
        "product_quantity": 1,
        "billing_items": [
          {
            "uuid": "45ce11ae-ccec-45a5-b569-f153b44637da",
            "description": null,
            "amount_billed": "540.0",
            "amount_unit": "90.0",
            "quantity": "6.0",
            "billable_type": "Billing",
            "created_at": "2025-03-25T13:52:16.296-03:00",
            "updated_at": "2025-03-25T13:52:16.296-03:00",
            "product": {
              "uuid": "f1315678-4265-4191-b566-d88638991321",
              "name": "Produto A",
              "amount": "90.0"
            }
          },
          {
            "uuid": "8bb8ebb8-4852-4dca-910b-8c2ab9418c51",
            "description": null,
            "amount_billed": "266.64",
            "amount_unit": "22.22",
            "quantity": "12.0",
            "billable_type": "Billing",
            "created_at": "2025-03-25T13:52:16.300-03:00",
            "updated_at": "2025-03-25T13:52:16.300-03:00",
            "product": {
              "uuid": "c949e6ce-70b4-4ac8-a197-a47582f9f021",
              "name": "Produto B",
              "amount": "22.22"
            }
          }
        ],
        "customer_uuid": "169f912c-7d4d-489f-9622-3c0ca3e3c9d3",
        "merchant_uuid": "3cf0a7f5-6fa7-479f-8772-fa5b9f17829a",
        "recurrence_uuid": "4ca92d00-c214-494e-ae62-f021cc5c462b"
      }
    ],
    "customer_uuid": "169f912c-7d4d-489f-9622-3c0ca3e3c9d3",
    "merchant_uuid": "3cf0a7f5-6fa7-479f-8772-fa5b9f17829a",
    "recurrence_plan": null,
    "historic": [
      {
        "event": "Criação",
        "description": "Recorrência foi criada.",
        "date_change": "2025-03-25T13:52:14.441-03:00",
        "user": "admin@example.com"
      },
      {
        "event": "Atualização",
        "description": "Recorrência foi atualizada com novos valores e políticas.",
        "date_change": "2025-03-25T14:30:00.000-03:00",
        "user": "admin@example.com"
      }
    ]
  }
}
```

#### recurrence.readjusted

Disparado quando um reajuste é efetivamente aplicado na recorrência (alterando o valor). O payload é o mesmo de `recurrence.updated` (recorrência completa), acrescido do bloco `last_adjustment` com os detalhes do reajuste aplicado:

```json
{
  "event": "recurrence.readjusted",
  "payload": {
    "uuid": "4ca92d00-c214-494e-ae62-f021cc5c462b",
    "status": "active",
    "amount": "885.96",
    "...": "demais campos da recorrência, idênticos ao recurrence.updated",
    "last_adjustment": {
      "adjustment_scheduled_uuid": "a1b2c3d4-1111-2222-3333-444455556666",
      "adjustment_type": "ipca",
      "index_name": "IPCA",
      "percentage_applied": "9.83",
      "amount_before": "806.64",
      "amount_after": "885.96",
      "applied_at": "2025-04-01T03:00:00.000-03:00"
    }
  }
}
```

> O campo `adjustment_type` pode ser `customized` (percentual definido pelo merchant), `ipca` ou `igpm`. Quando for `customized`, `index_name` retorna `Definido pelo usuário`.

#### recurrence.adjustment_pending

Disparado quando há um reajuste **manual** (que aguarda confirmação) com data prevista para o próximo mês. Serve como aviso prévio para que o merchant confirme o reajuste. É enviado uma vez por recorrência dentro do mês. O payload é a recorrência completa (mesmo formato de `recurrence.updated`), incluindo o bloco `adjustment_scheduled` com a data e o percentual previstos.

```json
{
  "event": "recurrence.adjustment_pending",
  "payload": {
    "uuid": "4ca92d00-c214-494e-ae62-f021cc5c462b",
    "status": "active",
    "amount": "806.64",
    "...": "demais campos da recorrência, idênticos ao recurrence.updated",
    "adjustment_scheduled": {
      "uuid": "a1b2c3d4-1111-2222-3333-444455556666",
      "adjustment_type": "igpm",
      "frequency": "annual",
      "percentage_value": "7.50",
      "automatic_application": false,
      "next_adjustment_date": "2025-05-01"
    }
  }
}
```

### Transfers
Os eventos de **Transfers** são relacionados às transferências dos valores recebidos para a conta de recebimento do merchant. Cada status indica um estado específico da transferência:

- **transfer.pending**: Transferência está pendente e aguardando processamento.
- **transfer.succeeded**: Transferência foi realizada com sucesso.
- **transfer.canceled**: Transferência foi cancelada.
- **transfer.failed**: Transferência falhou.
- **transfer.confirmed**: Transferência foi confirmada.

Exemplo de payload para Transfers:

```json
{
  "event": "transfer.confirmed",
  "payload": {
    "uuid": "cb2f3a42-2647-4225-bea6-0525f72edc0f",
    "description": "Transferência agendada.",
    "amount": 1032.2,
    "status": "confirmed",
    "transfer_date": "2022-08-23T00:00:00.000-03:00",
    "transfer_type": "automatic_acquirer",
    "transferable_type": "TransferZoop",
    "created_at": "2022-08-23T11:15:57.698-03:00",
    "updated_at": "2022-10-18T16:44:03.935-03:00",
    "receivables": [],
    "bank_account": {
      "uuid": "1a5ed345-5744-40f7-a310-c2313b1e5340",
      "agency": "0000",
      "agency_dv": "0",
      "account": "00000000",
      "account_dv": "0",
      "account_type": "checking",
      "active": true,
      "created_at": "2022-06-28T15:04:50.520-03:00",
      "updated_at": "2022-07-01T18:24:48.227-03:00",
      "bank": {
        "uuid": "b46c942e-ea0a-4338-9d78-d1e14677e7ca",
        "compe": "260",
        "ispb": "18236120",
        "document": "18.236.120/0001-58",
        "name": "BANK FULL NAME",
        "short_name": "BANK SHORT NAME",
        "url": null,
        "created_at": "2022-05-25T03:29:51.895-03:00",
        "updated_at": "2022-05-25T03:29:51.895-03:00"
      }
    },
    "billings": [],
    "merchant_uuid": "b9b26921-bd40-49b3-804a-f4632ecb8d7e",
    "bank_account_uuid": "1a5ed345-5744-40f7-a310-c2313b1e5340"
  }
}
```

### NFSe

Notas Fiscais de Serviço Eletrônicas (NFSe) são documentos fiscais eletrônicos utilizados para registrar a prestação de serviços. Elas formalizam a transação entre o prestador e o tomador de serviços, e são obrigatórias para diversos tipos de serviços.

Os eventos de **NFSe** representam os diferentes estados de uma nota fiscal e são descritos da seguinte forma:

- **nfse.pending**: A nota fiscal está pendente e ainda não foi emitida.
- **nfse.issued**: A nota fiscal foi emitida, mas ainda não foi confirmada.
- **nfse.confirmed**: A nota fiscal foi confirmada e está validada.
- **nfse.canceled**: A nota fiscal foi cancelada.
- **nfse.failed**: A emissão da nota fiscal falhou.

Exemplo de payload para NFSe:
```json
{
  "event": "nfse.confirmed",
  "payload": {
    "uuid": "9f47d8b6-9d5f-4b6e-9a85-3e6e4a5e3e8c",
    "status": "confirmed",
    "issue_type": "on_demand",
    "rps_number": "5813",
    "rps_serie": "B",
    "nfse_number": "4567",
    "verification_code": "D4F5G6HI",
    "url_pdf": "https://example.com/files/12345678901234_56789/202406/DANFSEs/NFSe1234567890123456789-4567-D4F5G6HI.pdf",
    "url_xml": "https://example.com/api/files/12345678901234_56789/202406/XMLsNFSe/1234567890123456789-4567-D4F5G6HI-nfse.xml",
    "created_at": "2024-06-15T10:30:20.123-03:00",
    "updated_at": "2024-06-15T10:31:15.234-03:00",
    "url_danfe": "https://example.com/security/pdf/?identifier=1234567",
    "status_detail": null,
    "nfse_billings": [],
    "customer": {
      "status": "active",
      "name": "LOJA EXEMPLO LTDA",
      "nickname": "Loja Exemplo",
      "document": "12345678000195",
      "email": "contato@lojaexemplo.com.br",
      "phone": "55912345678",
      "created_at": "2024-05-15T08:20:31.123-03:00",
      "updated_at": "2024-05-15T08:20:31.123-03:00",
      "uuid": "abcdef12-3456-7890-abcd-ef1234567890"
    },
    "nfse_item": {
      "uuid": "23456789-abcdef-1234-5678-abcdef123456",
      "iss_retention": false,
      "description": "Consultoria em marketing digital.",
      "amount": "250.0",
      "created_at": "2024-06-15T10:30:20.234-03:00",
      "updated_at": "2024-06-15T10:30:20.234-03:00",
      "nature_operation": "tributacao_no_municipio",
      "nfse_issuer_service": {
        "uuid": "34567890-bcde-1234-5678-cdef12345678",
        "code": "02.03",
        "description": "Serviços de consultoria em gestão empresarial",
        "created_at": "2024-05-10T09:00:00.000-03:00",
        "updated_at": "2024-05-10T09:00:00.000-03:00",
        "status": "active",
        "cnae": "7022000"
      }
    },
    "customer_uuid": "abcdef12-3456-7890-abcd-ef1234567890",
    "merchant_uuid": "12345678-9abc-def0-1234-56789abcdef0",
    "nfse_issuer_uuid": "09876543-21fe-dcba-8765-4321fedcba98",
    "nfse_uuid": "9f47d8b6-9d5f-4b6e-9a85-3e6e4a5e3e8c"
  }
}
```

### Contratos

Os eventos de **Contratos** são relacionados ao ciclo de vida dos contratos digitais:

- **contract.current**: Contrato totalmente assinado por todos os signatários e ativo.

Exemplo de payload para Contratos:

```json
{
  "uuid": "c9f2f1a1-3a6d-4b5f-ae3e-2a5baf13e9d2",
  "status": "current",
  "title": "Contrato de Prestação de Serviços Educacionais",
  "created_at": "2025-06-10T14:22:31-03:00",
  "updated_at": "2025-06-18T09:17:12-03:00",
  "message": null,
  "start_date": "2025-07-01",
  "end_date": "2026-06-30",
  "days_notice": 30,
  "description": "Treinamento em programação para adolescentes",
  "signed_at": "2025-06-15T16:45:00-03:00",
  "expiration_date": "2025-08-01",
  "content": null,
  "document_file_signed": "https://example-bucket.s3.amazonaws.com/uploads/contracts/contrato_educacional.pdf",
  "customer": {
    "name": "João Pedro Almeida",
    "email": "joao.p.almeida@example.com",
    "phone": "+55 11 91234-5678",
    "uuid": "a1b2c3d4-e5f6-7890-ab12-3456cd78ef90"
  },
  "signatories": [
    {
      "name": "João Pedro Almeida",
      "email": "joao.p.almeida@example.com",
      "signatory_type": "contracting_party",
      "status": "signed"
    },
    {
      "name": "Instituto Tech Jovem",
      "email": "contato@techjovem.org.br",
      "signatory_type": "contracted_party",
      "status": "signed"
    },
    {
      "name": "Fernanda Luz",
      "email": "fernanda.luz@example.com",
      "signatory_type": "witness",
      "status": "signed"
    }
  ],
  "customer_uuid": "a1b2c3d4-e5f6-7890-ab12-3456cd78ef90",
  "merchant_uuid": "9e87d6c5-b4a3-21f0-9988-1d2c3a4b5e6f"
}
```

---

Para mais informações sobre configuração e uso dos webhooks, entre em contato com nossa equipe de suporte técnico.
