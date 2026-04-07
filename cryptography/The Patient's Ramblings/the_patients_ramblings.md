# Psych CTF

# 1. The Patient's Ramblings

**Category:** Crypto

## Approach

Opening the provided evaluation form gives us two large numbers: the case file reference number and a number noted down as the patient's response.

Case File Reference No.:
111868901247420316641476851232090548464779536856140058952901622429320070031514973559280614879906286508519367202343622059532988929347378179790769989031071337084626257163124983495032485401511286405058157599088478612762588258584134812975299789351812692805302354346208568002749574430118849091098982333015119833543

PATIENT'S WRITTEN RESPONSE (reproduced exactly as written):
20962756738430634532041602293406428409611191953016656295918762305816341153057445308997480511666622352278550329257503849203702181806899212779289488527962657008105761161632101

There are numerous mentions of the number 3.
This points to a very simple RSA with exponent, e = 3.

The line 'the root of the problem is 3' led me to believe the message was not large enough to have been shortened by modulo.
Then, directly taking the cube root of the smaller number (ciphertext, c) gives us the message bytes.

## Final Flag

psych{v0ic3s_1n_my_h34d}
