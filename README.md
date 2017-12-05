# Payment Lib.
Zarinpal Payment SDK for Yekta Co.


- Need Library:
```Gradle
   compile 'com.github.imanx:PaymentSDK:0.0.4'
 ```
 - Example :
 ```Java
            
                String merchantID = "57a1943e-858e-11e7-a187-005056a205be"; //this ZarinPal merchantID 
                long amount = 100; //this payment amount
                String description = "test of pay"; //this payment description

                ZarinPalPayment.Builder builder = new ZarinPalPayment.Builder(
                getBaseContext(), 
                merchantID, 
                amount, 
                description);

                builder.setToolbarColor(R.color.colorPrimary); //this is optional and change toolbar color in payment activity
                builder.setEmail("user@gmail.com"); //this is optional || mobile payer
                builder.setMobile("+989355106***"); //this is optional || email payer

                builder.build().purchase(new OnCallbackPurchaseListener() {
                    @Override
                    public void onSuccessPayment(String refID, String authority, ZarinPalPayment.Builder payment) {
                        //when Payment is Success and return:
                        //refID: this is transaction id.
                        //authority: this is a payment unique id
                        //payment : included payment details ex: amount , description
                        Toast.makeText(getApplicationContext(), refID, Toast.LENGTH_LONG).show();
                    }

                    @Override
                    public void onFailure(int status, String authority) {
                        //when Payment is failure and return:
                        //status : ZarinPal failure codes
                        //authority: this is a payment unique id

                        Toast.makeText(getApplicationContext(), status + "", Toast.LENGTH_LONG).show();

                    }

                });

 ```
