# External API Specification

## 1. Create Order (Outbound)

**Direction:** Salesforce → External System  
**Method:** POST  
**Endpoint:** /api/orders  

### Request Body
```json
{
  "orderReference": "SF-ORD-1001",
  "customerName": "ABC Technologies",
  "amount": 75000,
  "currency": "INR"
}
```
## Success Response (200)
```json
{
  "externalOrderId": "EXT-90123",
  "status": "CREATED"
}
```
## Error Response (400 / 500)
```json
{
  "errorCode": "ORDER_CREATION_FAILED",
  "message": "Invalid order data"
}
```
## 2. Payment Update (Inbound Webhook)

**Direction:** External System → Salesforce
**Method:** POST
**Endpoint:** /services/apexrest/payment/update

## Request Body
```
{
  "externalOrderId": "EXT-90123",
  "paymentStatus": "SUCCESS",
  "transactionId": "TXN-778899"
}
```
## Success Response (200)
```
{
  "message": "Payment processed successfully"
}
```
---

## 3️⃣ Create Sample JSON Files (IMPORTANT)

Inside `/api/`, create these files:

### `sample-order-request.json`
```json
{
  "orderReference": "SF-ORD-1001",
  "customerName": "ABC Technologies",
  "amount": 75000,
  "currency": "INR"
}

{
  "externalOrderId": "EXT-90123",
  "status": "CREATED"
}
```
