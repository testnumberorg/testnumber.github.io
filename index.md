## Test PSTN and VOIP Calls

  *We create tools to make it easy test and troubleshoot phone calls.*

## Current Features

- Determines the calling number
- Determines the STIR/SHAKEN attestation level
- Determines if the calling number is flagged as a robocaller according to [Scout](https://scout.tel)
- Determines if DTMF is working properly

## Usage

  *Simply call one of the Telephone Numbers or SIP addresses listed below. Listen on the line for information about your call and calling number.*

## Test PSTN Numbers

  *Note: different numbers may return different results*

* <a href="tel:+17377273232">+1-737-727-3232</a>
* <a href="tel:+12602701982">+1-260-270-1982</a>
* <a href="tel:+19593351959">+1-959-335-1959</a>

## Test SIP Addresses

* <a href="sip:test1@sip.testnumber.org:5060">sip:test1@sip.testnumber.org:5060</a>

## How It Works

  *The Phone Numbers and SIP addresses at [testnumber.org](http://testnumber.org) map to [Twilio](http://twilio.com) functions which use [Scout](https://scout.tel) to detect Robocalls.*

## SHAKEN/STIR Response Reference

  *Currently the SHAKEN/STIR response is derived from Twilio's implementation which is documented [here](https://www.twilio.com/docs/voice/trusted-calling-with-shakenstir)*

## Tutorials

  * Learn how we access the calling number in Twilio call flow [here](/twilio/how-to-detect-the-number-a-caller-is-calling-from-on-twilio)
  * Learn to use [Scout](https://scout.tel) to find the SPAM Risk Rating of an incoming Twilio call [here](/twilio/how-to-use-phone-number-info-using-scout-twilio-lookup-addon)