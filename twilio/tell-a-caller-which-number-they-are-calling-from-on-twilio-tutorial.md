
# <center>How to Create a Phone Number can will Callers their Caller Id</center>

---

<br/>

## Buy a Twilio Phone Number

---

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

  > Create a New Service called `incoming-number-detector`

  ![Create a New Service](/assets/images/create-a-new-service.png)
  
  <br/>

  > Create a New Function in the `incoming-number-detector` Service called `main`

  ![Create a New Function called main](/assets/images/create-a-new-main-function.png)

  <br/>

  > Post the following in the Editor for the `main` Function.

  ```
    exports.handler = function(context, event, callback) {      
      let twiml = new Twilio.twiml.VoiceResponse();        
      let fromNumber = event["Caller"];  

      twiml.pause({
        length: 2
      });

      twiml.say({ voice: "alice" }, "Welcome to test number dot org.");

      twiml.pause({
        length: 1
      });

      twiml.say({ voice: "alice" }, "You are calling from " + fromNumber.slice(1).split("").join(" ") + ".");

      twiml.pause({
        length: 1
      });

      twiml.say({ voice: "alice" }, "Goodbye.");

      // This callback is what is returned in response to this function being invoked.
      // It's really important! E.g. you might respond with TWiML here for a voice or SMS response.
      // Or you might return JSON data to a studio flow. Don't forget it!
      return callback(null, twiml);
    };
  ```
<br/>

## Configure the Phone Number

---

  > Enable the Function for incoming calls to the new Number

  ![Enable the Function for incoming calls to the new Number](/assets/images/enable-the-number-detector-function.png)

  <br/>

  > Verify the function is the default for the Number

  ![Verify the function is the default for the Number](/assets/images/verify-the-function-is-the-default-for-the-number.png)

<br/>

## Call the Phone Number

---

  * Dial the Phone Number from a working Telephone
