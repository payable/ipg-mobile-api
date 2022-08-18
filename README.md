# PAYable Mobile IPG API

#### 1. Generate payment url 

GET: `https://us-central1-payable-mobile.cloudfunctions.net/ipg/sandbox/`

Body: `GET`

```url
?merchantKey=XXXXXXXXXX
&merchantToken=XXXXXXXXXXXXXXXXXXXX
&refererUrl=https://www.example.com
&logoUrl=https://example.com/logo.png

// (Optional) The card details will be notified with POST request
&notificationUrl=https://example.com/request-test 

// (Optional) Once the payment is done this URL will be redirected with `resultIndicator` 
// which is required to check the payment status
&returnUrl=https://example.com/status-view 

&amount=100.00
&currencyCode=LKR
&orderDescription=PAYable_Mobile_IPG

&customerFirstName=Aslam
&customerLastName=Anver
&customerEmail=aslam@example.lk
&customerMobilePhone=0777123456
&billingAddressStreet=Hill Street
&billingAddressCity=Dehiwala
&billingAddressCountry=LK
&billingAddressPostcodeZip=10350
&billingAddressStateProvince=Western

// Shipping details are optional
&shippingContactFirstName=Aslam
&shippingContactLastName=Anver
&shippingContactEmail=aslam@example.lk
&shippingContactMobilePhone=0777123456
&shippingAddressStreet=Hill Street
&shippingAddressCity=Dehiwala
&shippingAddressCountry=LK
&shippingAddressPostcodeZip=10350
&shippingAddressStateProvince=Western

// json - JSON response which contains the payment page URL
// html - The payment page will be loaded
&responseType=json
```

Response:
```json
{
    "status": "PENDING",
    "uid": "969077C7-EBB5-428A-9F09-FF195560F200",
    "successIndicator": "9c8d273567be4c58",
    "paymentPage": "https://us-central1-payable-mobile.cloudfunctions.net/ipg/sandbox/?uid=969077C7-EBB5-428A-9F09-FF195560F200"
}
```

#### 2. Payment Page

GET: `https://us-central1-payable-mobile.cloudfunctions.net/ipg/sandbox/`

Body: `GET`

```url
?uid=969077C7-EBB5-428A-9F09-FF195560F200
```

Response: <br/>
![](https://i.imgur.com/p0aewHZ.png)

#### 3. Payment Status

GET: `https://us-central1-payable-mobile.cloudfunctions.net/ipg/sandbox/status-view`

Body: `GET`

```url
?uid=C7ADE26D-B62C-4AC5-AE44-19F1C3139F84
&resultIndicator=5752890e6cae4be4

// Json reponse or HTML page with payment status
&responseType=json
```

Response:

```json
{
    "status": "SUCCESS",
    "data": {
        "cardHolderName": "HNB.S 776",
        "statusCode": 1,
        "payableCurrency": "LKR",
        "payableOrderId": "oid-2b7b4069-1ef2-11ed-baa9-31321920b630",
        "merchantKey": "A75BCD8EF30E529A",
        "cardNumber": "511111xxxxxx1118",
        "txType": "ONE_TIME_PAYMENT",
        "paymentType": 1,
        "payableTransactionId": "86a89f17-1ef2-11ed-bd7a-2db910859eae",
        "invoiceNo": "INV1660826095925",
        "custom1": "",
        "payableAmount": "100.00",
        "paymentScheme": "MASTERCARD",
        "checkValue": "395E8610AE334B47EE0D3F31E5CC9B6C3C7AE454C3AAD5999CCAD7C9C4E8ADB56A52BA273AAC0D0AFE48EF4AD13A4B05FF7291E63C1BF30AE4DA1C3E1DA958C6",
        "paymentMethod": 1,
        "custom2": "",
        "statusMessage": "SUCCESS"
    }
}
```
