
# **<center>How to create a Phone Service that will detect and repeat the Caller-Id</center>**

<br/>

## Login into Twilio's Console and buy a Phone Number

---

  * Log in to the [Twilio Console](https://console.twilio.com)
  * Navigate to`Products > Super Network > Phone Numbers > Manage > Buy a number`

  > Buy a Twilio Number

  [![Buy a Twilio Number](/assets/images/buy-a-twilio-number.png)](/assets/images/buy-a-twilio-number.png)

  <br/>

  > Verify the purchased Number

  ![Purchased Twilio Number](/assets/images/twilio-number-purchased.png)

<br/>

## Create a Twilio Function  

---

  * This Service Function will be configured to be called on every inbound call

  > Find Twilio Functions and Assets in the Console

  [![Find Twilio Functions and Assets in the Console](/assets/images/find-functions-and-assets.png)](/assets/images/find-functions-and-assets.png)

  <br/>

  > Create a new Service called **incoming-number-detector**

  [![Create a New Service](/assets/images/create-a-new-service.png)](/assets/images/create-a-new-service.png)
  
  <br/>

  > Create a new Function in the **incoming-number-detector** Service called **/main**

  [![Create a New Function called /main](/assets/images/create-a-new-main-function.png)](/assets/images/create-a-new-main-function.png)

  <br/>

  > Paste the following javascript in the Editor for the **/main** Function.

  ```
  exports.handler = function(context, event, callback) {  
    let twiml = new Twilio.twiml.VoiceResponse();        
    let fromNumber = event["Caller"]; // The From number is contained in this key 
    let speechFriendlyFromNumber = fromNumber.slice(1).split("").join(" "); // Format it better for speech

    // Add a few cosmetic pauses
    twiml.pause({
      length: 2
    });

    twiml.say({ voice: "alice" }, "Welcome to test number dot org.");

    twiml.pause({
      length: 1
    });

    // Tell the caller what we have detected as the From Number
    twiml.say({ voice: "alice" }, "You are calling from " + speechFriendlyFromNumber + ".");

    twiml.pause({
      length: 1
    });

    // Bid them farewell
    twiml.say({ voice: "alice" }, "Goodbye.");

    return callback(null, twiml);
  };    
  ```

  * Save **/main**
  * Press **Deploy All** at the bottom of the Editor

<br/>

## Configure the Phone Number

---

  > Enable the Function for incoming calls to the new Number

  [![Enable the Function for incoming calls to the new Number](/assets/images/enable-the-number-detector-function.png)](/assets/images/enable-the-number-detector-function.png)

  <br/>

  > Verify the Function is the default for the new Number

  [![Verify the function is the default for the Number](/assets/images/verify-the-function-is-the-default-for-the-number.png)](/assets/images/verify-the-function-is-the-default-for-the-number.png)

<br/>

## Call your new Phone Number

---

  * Dial the Phone Number from a working telephone
  * You should hear your Caller ID repeated back to you
  * We'll cover debugging in another session
