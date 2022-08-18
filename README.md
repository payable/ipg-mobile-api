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

// (Optional) Once the payment is done we redirect to this URL
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

#### 2. Payment page

GET: `https://us-central1-payable-mobile.cloudfunctions.net/ipg/sandbox/`

Body: `GET`

```url
?uid=969077C7-EBB5-428A-9F09-FF195560F200
```

Response: <br/>
![](https://i.imgur.com/p0aewHZ.png)
