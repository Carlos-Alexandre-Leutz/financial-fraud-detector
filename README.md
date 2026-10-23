# 🛡️ Matrix Fraud API

Uma API pública e gratuita para **avaliação de risco de fraude em transações financeiras**, desenvolvida com **álgebra linear, otimização matricial e computação vetorizada em NumPy**.

## 🎯 Apresentação

O serviço fornece um endpoint de consulta direta para e-commerces e gateways de pagamento analisarem transações em tempo real. A API recebe o contexto da compra e o histórico do usuário, aplica uma transformação polinomial no espaço de características e processa os dados em um modelo de regressão logística para retornar um score de probabilidade de fraude.

## 📐 Fundamentação Matemática

* **Expansão Polinomial de Características:** Mapeamento de atributos para grau 2, permitindo identificar fronteiras de decisão não-lineares e interações complexas entre variáveis (como horário, valor e frequência de compra).
* **Computação Vetorizada:** Cálculos efetuados através de produto escalar e operações matriciais diretas em NumPy para garantir respostas em milissegundos.
* **Classificação Logística Regularizada:** Otimização via Gradiente Descendente com penalização L2 para mitigação de overfitting.

## ⚡ Integração da API

A consulta é feita através de uma requisição HTTP enviando os dados da transação.

### Requisição de Exemplo

**`POST /v1/evaluate`**

```json
{
  "user_id": "usr_981273",
  "transaction": {
    "amount": 3500.00,
    "hour_of_day": 3,
    "distance_from_home_km": 450.0
  },
  "user_history": {
    "avg_purchase_amount": 120.00,
    "total_previous_transactions": 24,
    "days_since_last_purchase": 2
  }
}
```

### Resposta de Retorno

```json
{
  "transaction_id": "tx_uuid_12345",
  "fraud_probability": 0.942,
  "risk_level": "HIGH",
  "action_recommended": "REVIEW_MANUAL"
}
```
