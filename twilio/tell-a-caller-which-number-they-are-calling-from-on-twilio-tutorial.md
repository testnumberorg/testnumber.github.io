---
title: Test PSTN Phone Numbers and SIP Addresses
description: How to Create a Phone Number that can tell Callers their Caller Id
---

# <center>How to Create a Phone Number that can tell Callers their Caller Id</center>

<br/>

## Buy a Twilio Phone Number

---

  * Log in to the [https://console.twilio.com](Twilio Console)

  > Buy a Twilio Number

  ![Buy a Twilio Number](/assets/images/buy-a-twilio-number.png)

  <br/>

  > Verify purchased Number

  ![Purchased Twilio Number](/assets/images/twilio-number-purchased.png)

<br/>

## Create the Twilio Function  

---

  > Find Twilio Functions and Assets in the Console

  ![Find Twilio Functions and Assets in the Console](/assets/images/find-functions-and-assets.png)

  <br/>

  > Create a new Service called **incoming-number-detector**

  ![Create a New Service](/assets/images/create-a-new-service.png)
  
  <br/>

  > Create a new Function in the **incoming-number-detector** Service called **/main**

  ![Create a New Function called /main](/assets/images/create-a-new-main-function.png)

  <br/>

  > Paste the following javascript in the Editor for the **/main** Function.

  ```
    exports.handler = function(context, event, callback) {  
      let twiml = new Twilio.twiml.VoiceResponse();        
      let fromNumber = event["Caller"];  
      let speechFriendlyFromNumber = fromNumber.slice(1).split("").join(" ");

      twiml.pause({
        length: 2
      });

      twiml.say({ voice: "alice" }, "Welcome to test number dot org.");

      twiml.pause({
        length: 1
      });

      twiml.say({ voice: "alice" }, "You are calling from " + speechFriendlyFromNumber + ".");

      twiml.pause({
        length: 1
      });

      twiml.say({ voice: "alice" }, "Goodbye.");

      return callback(null, twiml);
    };    
  ```
<br/>

## Configure the Phone Number

---

  > Enable the Function for incoming calls to the new Number

  ![Enable the Function for incoming calls to the new Number](/assets/images/enable-the-number-detector-function.png)

  <br/>

  > Verify the Function is the default for the Number

  ![Verify the function is the default for the Number](/assets/images/verify-the-function-is-the-default-for-the-number.png)

<br/>

## Call the Phone Number

---

  * Dial the Phone Number from a working Telephone
