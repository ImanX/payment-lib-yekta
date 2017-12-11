# Payment Lib.
Zarinpal Payment SDK for Yekta Co.

#iOS
- Need Framework:
```framework
 add to Project frameworks 'ZarinPalSDKPayment.framework'
 ```
 
 
 - Example :
 ```Swift
            
import UIKit
import ZarinPalSDKPayment <- import this.
class ViewController: UIViewController , ZarinPalPaymentDelegate {
    
    func didSuccess(refID: String, authority: String, builder: ZarinPal.Builder) {
                        //when Payment is Success and return:
                        //refID: this is transaction id.
                        //authority: this is a payment unique id
                        //payment : included payment details ex: amount , description
        print(refID);
    }
    
    func didFailure(code: Int, authority: String?) {
     //when Payment is failure and return:
                        //status : ZarinPal failure codes
                        //authority: this is a payment unique id
        print(code);
    }
   
    
    @IBAction func click(_ sender: Any) {
        
        let zarinpal =   ZarinPal.Builder(vc: self, merchantID: "****************", amount: 100, description: "description");
       
        zarinpal.indicatorColor = UIColor.black;  //this set indicator color *optional
        zarinpal.title = "Payment Gateway";  //this set title of payment page *optional
        zarinpal.pageBackgroundColor = UIColor.lightGray; // this set background payment color *optional
        zarinpal.email = "email@gmail.com"; //this set email *optional
        zarinpal.mobile = "09355106005"; //this set mobile *optional
        zarinpal
            .build()
            .start(delegate: self);
        
    }
   

    override func viewDidAppear(_ animated: Bool) {
    
   
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }


}


 ```



#Android
- Need Library:
```Gradle
   compile 'com.github.imanx:PaymentSDK:0.0.4'
 ```
 - Example :
 ```Java
            
                String merchantID = "**********************"; //this ZarinPal merchantID 
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
