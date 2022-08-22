# **<center>How to use Phone Number Information from Twilio Lookup Scout Addon</center>**

<br/>

## Objective

---

  - Create a Twilio Voice Service that will answer an incoming call
  - Retreive the [Scout](https://scout.tel) Risk Level
  - Tell the caller their detected From Number and SPAM Risk Level

<br/>  

## Install the Scout Lookup Addon for Twilio and create an inbound Phone Number

---

  - Follow the directions to install the Scout Addon [here](https://www.scout.tel/blog/2021/7/12/how-to-install-scout-phone-number-lookup-twilio-addon)
  - Follow our tutorial covering setting up an inbound Twilio phone number [here](/twilio/how-to-detect-the-number-a-caller-is-calling-from-on-twilio)

<br/>

## Update your **incoming-number-detector** Twilio Service **/main** Function

---

  <br/>

  > Paste the following javascript in the Editor for the **/main** Function.

  ```
  exports.handler = function(context, event, callback) {  
    let twiml = new Twilio.twiml.VoiceResponse();        
    let fromNumber = event["Caller"]; // The From number is contained in this key 
    let speechFriendlyFromNumber = fromNumber.slice(1).split("").join(" "); // Format it better for speech
    let addons = JSON.parse(event["AddOns"]); // Parse your Addon data
    let scoutResult = addons.results.icehook_scout.result; // Grab the Scout data in particular
    let riskRating = scoutResult.spam_rating; // Explicitly set the Scout risk rating
    let riskLevel = scoutResult.spam_level; // Explicitly set the Scout risk level

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

    // Tell the caller their scout risk level
    twiml.say({ voice: "alice" }, "Scout determined your row bo call risk level is " + riskLevel + ".");

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