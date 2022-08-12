# testnumber.org
###### Make test calls to our PSTN phone numbers and VOIP SIP addresses

## Current Features
- Determines the calling number
- Determines the STIR/SHAKEN attestation level
- Determines if the calling number is flagged as a robocaller
- Determines if DTMF is working properly

## How It Works
The Phone Numbers and SIP addresses at [testnumber.org](https://testnumber.org) terminate at a [Twilio](https://twilio.com) function which uses [Scout](https://scout.tel) to detect Robocalls.


