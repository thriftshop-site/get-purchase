# get-purchase FN

## Development

- cp .env.example .env

- edit .env

```toml
GOOGLE_SERVICE_ACCOUNT_EMAIL=
GOOGLE_PRIVATE_KEY=
GOOGLE_SPREADSHEET_ID_FROM_URL=
```

<details>
  <summary>Set Up Google Services If Not Yet Set Up</summary>
 
> [Create New Google Project](https://console.developers.google.com/projectcreate)

![pic-selected-200630-1220-20](https://user-images.githubusercontent.com/55337687/86083241-414ecf00-bacc-11ea-83a9-f93a44e06bf0.png)


> [Enable Google Spreadsheet API](https://console.developers.google.com/apis/library/sheets.googleapis.com)

![enable-google-api](https://user-images.githubusercontent.com/55337687/86082798-3a738c80-bacb-11ea-8d8d-350b80950566.png)


> [Select Your New Created Project](https://console.cloud.google.com/projectselector2/iam-admin/serviceaccounts)

![pic-selected-200630-1228-25](https://user-images.githubusercontent.com/55337687/86083583-482a1180-bacd-11ea-95f3-4387d52b7ea3.png)

- Create New Google Service Account

![pic-selected-200630-1229-33](https://user-images.githubusercontent.com/55337687/86083658-79a2dd00-bacd-11ea-95c9-d744b5ecf829.png)

- Fill Up Service Account Details

![pic-selected-200630-1232-27](https://user-images.githubusercontent.com/55337687/86083938-241b0000-bace-11ea-8794-2d0e5e886cc1.png)

- Add Role Owner

![pic-selected-200630-1236-01](https://user-images.githubusercontent.com/55337687/86084019-59bfe900-bace-11ea-86d6-900d57ce9668.png)

> Create New Secret KEY

![pic-selected-200630-1238-12](https://user-images.githubusercontent.com/55337687/86084128-a60b2900-bace-11ea-8618-cb7c174f37f5.png)

- Select JSON

![pic-selected-200630-1239-14](https://user-images.githubusercontent.com/55337687/86084226-dc48a880-bace-11ea-915c-8169c747dece.png)

- This will Download A JSON , Open that File which Will Contain GOOGLE_PRIVATE_KEY and GOOGLE_SERVICE_ACCOUNT_EMAIL

```js
{
  "private_key": "GOOGLE_PRIVATE_KEY", // COPY THIS AND PASTE TO YOU .env file
  "client_email": "GOOGLE_SERVICE_ACCOUNT_EMAIL", // COPY AND PASTE THIS TO YOUR .env file
}
```

> Get Google Spreadsheet ID

1. Go to this link: https://docs.google.com/spreadsheets/u/0/

2.  Create A New Spreadsheet

3. Check The URL and Copy URL Segment and Paste to GOOGLE_SPREADSHEET_ID_FROM_URL

```
https://docs.google.com/spreadsheets/d/COPY-THIS-URL-SEGMENT/edit#gid=0
```

> Grant Permission to GOOGLE_SERVICE_ACCOUNT_EMAIL

- Inside Your SpreadSheet ,Click Share Button , paste your GOOGLE_SERVICE_ACCOUNT_EMAIL

![share-to-google-email](https://user-images.githubusercontent.com/55337687/86082878-6858d100-bacb-11ea-93fc-0a40f2baf692.png)

</details>

> run `netlify dev` command

- test http://localhost:8888/api in postman


<details>
  <summary>Raw JSON PAYLOAD</summary>

```json
{
    "reference_no": "dh5zPAn"
}
```

- reference_no is required

- throws error when not found in sheet

- returns all data in specific row where reference_no is matched.

> **EXAMPLE JSON RESPONSE**
```json
{
    "reference_no":"dh5zPAn",
    "pm_link":"https://pm.link/test/test/dh5zPAn",
    "payment_id":"pay_fA1B2STsdJd1QoyfbaeUUun3",
    "paid":"yes",
    "date_paid":"2020-5-16",
    "mop":"GCash","currency":"PHP","net_amount":"971","fee":"29","payout_date":"2020-5-19","referral_code":"midascode","referral_fee":"97.1",
    "sent":"",
    "courier":"",
    "tracking_no":"",
    "received":"",
    "deliverable": true,
    "order_details":"This is an Example Paymongo Create Link On Checkout",
    "receiver_name":"Midas Code Breaker",
    "receiver_phone":"roo5xUi",
    "notes":"7CbbxoP",
    "delivery_address":"No Permanent Address",
    "payer_name":"Mongo Bean",
    "payer_email":"mrbean@gmail.com",
    "payer_phone":"9155609040",
    "billing_address":"12th floor The Trade and Financial Tower u1206 32nd street and 7th Avenue,Taguig Bonifacio Global City 1630, PH"
}
```

</details>

## Deploy
[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/thriftshop-fn/get-purchase)

## Set Your Domain In Netlify

- Go to [Settings](https://app.netlify.com/sites/tss-test/settings/general)

- Click Change Site Name `${username}-tss-fn-get-purchase.${domain}.com`

## Production

- make post request with Needed *payload* to `${username}-tss-fn-get-purchase.${domain}.com/api`


