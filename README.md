
# Clientbase - Simplifique a Gestão de Clientes e Cobranças Recorrentes

**Clientbase** oferece uma solução completa para quem precisa gerenciar clientes e cobranças de forma eficiente e automatizada. Com funcionalidades que vão desde o cadastro e assinatura digital de contratos até a emissão de notas fiscais e notificações automatizadas, a ClientBase garante uma gestão financeira simplificada e eficaz para diversos setores como escolas, academias, agências, contabilidade e SaaS.

Para mais informações, visite nosso site: [Clientbase](https://clientbase.com.br).

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
      "uuid"=>"343c72fd-dad0-454b-9fea-4e99586fa5d7",
      "status"=>"active",
      "name"=>"Nome do produto",
      "description"=>"Descrição do produto",
      "amount"=>"2000.0"
    },
    "customer_uuid": "12abf34d-9e8f-4d4b-81c3-45e3f6d7a1a9",
    "merchant_uuid": "f6c8d7e3-4d2b-4a5e-b9e8-8c6f7d9a1b5d",
    "recurrence_uuid": null,
    "amount_updated": 0.1023e4,
    "nfse_status": "not_scheduled"
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
