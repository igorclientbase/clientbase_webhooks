
# ClientBase - Simplifique a Gestão de Clientes e Cobranças Recorrentes

**ClientBase** oferece uma solução completa para quem precisa gerenciar clientes e cobranças de forma eficiente e automatizada. Com funcionalidades que vão desde o cadastro e assinatura digital de contratos até a emissão de notas fiscais e notificações automatizadas, a ClientBase garante uma gestão financeira simplificada e eficaz para diversos setores como escolas, academias, agências, contabilidade e SaaS.

Para mais informações, visite nosso site: [ClientBase](https://clientbase.com.br).

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
    "description": "",
    "due_date": "2022-09-09",
    "amount_billed": 150.0,
    "interest_policy": "no_interest",
    "discount_policy": "fixed",
    "discount_days": 15,
    "discount_amount": 10.0,
    "created_at": "2022-08-16T00:04:27.521-03:00",
    "updated_at": "2022-10-18T16:39:22.045-03:00",
    "uuid": "54dc74ef-72c9-4d88-a444-3ef49c4513ad",
    "recurrence_cycle": 13,
    "dirty": true,
    "payment_type": "boleto;credit_card",
    "amount_paid": "0.0",
    "date_paid": null,
    "antecipated": false,
    "issued": true,
    "viewed": false,
    "email_invoice_status": "no_state",
    "sms_invoice_status": "no_state",
    "customer": {
      "status": "active",
      "name": "João da Silva",
      "nickname": "João",
      "document": "00000000000",
      "email": "test@clientbase.com.br",
      "phone": "5599999999999",
      "created_at": "2022-05-31T22:13:03.326-03:00",
      "updated_at": "2022-08-19T14:03:25.991-03:00",
      "uuid": "91fca8f9-439c-476f-bf93-75b3707b9f6d"
    },
    "customer_uuid": "91fca8f9-439c-476f-bf93-75b3707b9f6d",
    "merchant_uuid": "3cf0a7f5-6fa7-479f-8772-fa5b9f17829a",
    "recurrence_uuid": "4d804ec9-4dbd-4eba-a207-820ea61e2bd2",
    "payments": [
      {
        "status": "paid",
        "due_date": "2022-09-09",
        "amount_billed": 150.0,
        "date_paid": null,
        "amount_paid": 0.0,
        "bank_fee": null,
        "fee": null,
        "paymentable_type": null,
        "created_at": "2022-10-17T16:43:04.460-03:00",
        "updated_at": "2022-10-17T16:43:04.460-03:00",
        "payment_type": "credit_card",
        "uuid": "39413596-7763-4780-a3d2-440fe0ff0ae1",
        "date_no_payment": null,
        "modified": null,
        "customer_uuid": "91fca8f9-439c-476f-bf93-75b3707b9f6d",
        "merchant_uuid": "3cf0a7f5-6fa7-479f-8772-fa5b9f17829a",
        "billing_uuid": "54dc74ef-72c9-4d88-a444-3ef49c4513ad"
      }
    ]
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
