#This is an example output from the built in EMV card emulator:
```
---------------------------------------------------------------------
[Step 1] SELECT FILE Master File (if available)
---------------------------------------------------------------------
00 A4 00 00 00
response hex    :

response SW1SW2 : 6d 00
response ascii  : 
response parsed :


---------------------------------------------------------------------
[Step 2] SELECT FILE 1PAY.SYS.DDF01 to get the PSE directory
---------------------------------------------------------------------
00 A4 04 00 0E 31 50 41 59 2E 53 59 53 2E 44 44 46 30 31
response hex    :
6f 20 84 0e 31 50 41 59 2e 53 59 53 2e 44 44 46
30 31 a5 0e 88 01 02 5f 2d 04 6e 6f 65 6e 9f 11
01 01
response SW1SW2 : 90 00
response ascii  : o ..1PAY.SYS.DDF01....._-.noen....
response parsed :

6f 20 -- File Control Information (FCI) Template
      84 0e -- Dedicated File (DF) Name
            31 50 41 59 2e 53 59 53 2e 44 44 46 30 31 (BINARY)
      a5 0e -- File Control Information (FCI) Proprietary Template
            88 01 -- Short File Identifier (SFI)
                  02 (BINARY)
            5f 2d 04 -- Language Preference
                     6e 6f 65 6e (=noen)
            9f 11 01 -- Issuer Code Table Index
                     01 (NUMERIC)

---------------------------------------------------------------------
[Step 3] Send READ RECORD to read all records in SFI 2
---------------------------------------------------------------------
00 B2 01 14 00
response hex    :
70 23 61 21 4f 07 a1 23 45 67 89 10 10 50 04 56
49 53 41 9f 12 0c 56 49 53 41 20 43 6c 61 73 73
69 63 87 01 02
response SW1SW2 : 90 00
response ascii  : p#a!O..#Eg...P.VISA...VISA Classic...
response parsed :

70 23 -- Record Template (EMV Proprietary)
      61 21 -- Application Template
            4f 07 -- Application Identifier (AID) - card
                  a1 23 45 67 89 10 10 (BINARY)
            50 04 -- Application Label
                  56 49 53 41 (=VISA)
            9f 12 0c -- Application Preferred Name
                     56 49 53 41 20 43 6c 61 73 73 69 63 (=VISA Classic)
            87 01 -- Application Priority Indicator
                  02 (BINARY)

---------------------------------------------------------------------
[Step 4] Send READ RECORD to read all records in SFI 2
---------------------------------------------------------------------
00 B2 02 14 00
response hex    :
70 25 61 23 4f 07 d5 78 00 00 02 10 10 50 09 62
61 6e 6b 61 78 65 70 74 9f 12 09 62 61 6e 6b 61
78 65 70 74 87 01 01
response SW1SW2 : 90 00
response ascii  : p%a#O..x.....P.bankaxept...bankaxept...
response parsed :

70 25 -- Record Template (EMV Proprietary)
      61 23 -- Application Template
            4f 07 -- Application Identifier (AID) - card
                  d5 78 00 00 02 10 10 (BINARY)
            50 09 -- Application Label
                  62 61 6e 6b 61 78 65 70 74 (=bankaxept)
            9f 12 09 -- Application Preferred Name
                     62 61 6e 6b 61 78 65 70 74 (=bankaxept)
            87 01 -- Application Priority Indicator
                  01 (BINARY)

---------------------------------------------------------------------
[Step 5] Send READ RECORD to read all records in SFI 2
---------------------------------------------------------------------
00 B2 03 14 00
response hex    :

response SW1SW2 : 6a 83
response ascii  : 
response parsed :


---------------------------------------------------------------------
[Step 6] Select application by AID
---------------------------------------------------------------------
00 A4 04 00 07 a1 23 45 67 89 10 10
response hex    :
6f 37 84 07 a1 23 45 67 89 10 10 a5 2c 50 04 56
49 53 41 87 01 02 9f 38 06 9f 1a 02 5f 2a 02 5f
2d 04 6e 6f 65 6e 9f 11 01 01 9f 12 0c 56 49 53
41 20 43 6c 61 73 73 69 63
response SW1SW2 : 90 00
response ascii  : o7...#Eg....,P.VISA....8...._*._-.noen.......VISA Classic
response parsed :

6f 37 -- File Control Information (FCI) Template
      84 07 -- Dedicated File (DF) Name
            a1 23 45 67 89 10 10 (BINARY)
      a5 2c -- File Control Information (FCI) Proprietary Template
            50 04 -- Application Label
                  56 49 53 41 (=VISA)
            87 01 -- Application Priority Indicator
                  02 (BINARY)
            9f 38 06 -- Processing Options Data Object List (PDOL)
                     9f 1a 02 -- Terminal Country Code
                     5f 2a 02 -- Transaction Currency Code
            5f 2d 04 -- Language Preference
                     6e 6f 65 6e (=noen)
            9f 11 01 -- Issuer Code Table Index
                     01 (NUMERIC)
            9f 12 0c -- Application Preferred Name
                     56 49 53 41 20 43 6c 61 73 73 69 63 (=VISA Classic)

---------------------------------------------------------------------
[Step 7] Send GET PROCESSING OPTIONS command
---------------------------------------------------------------------
80 A8 00 00 06 83 04 08 26 08 26
response hex    :
80 0a 5c 00 08 01 01 00 08 02 05 01
response SW1SW2 : 90 00
response ascii  : ..\.........
response parsed :

80 0a -- Response Message Template Format 1
      5c 00 08 01 01 00 08 02 05 01 (BINARY)

---------------------------------------------------------------------
[Step 8] Send READ RECORD to read SFI 1 record 1
---------------------------------------------------------------------
00 B2 01 0c 00
response hex    :
70 4d 9f 1f 18 32 34 39 35 30 30 30 30 30 30 30
30 30 30 30 31 30 31 30 30 30 30 30 30 57 13 54
11 11 88 88 88 88 82 d1 20 32 01 12 34 56 78 90
00 0f 5f 20 1a 53 4d 49 54 48 2f 4a 4f 48 4e 20
20 20 20 20 20 20 20 20 20 20 20 20 20 20 20
response SW1SW2 : 90 00
response ascii  : pM...249500000000000101000000W.T........ 2..4Vx..._ .SMITH/JOHN                
response parsed :

70 4d -- Record Template (EMV Proprietary)
      9f 1f 18 -- [Magnetic Stripe] Track 1 Discretionary Data
               32 34 39 35 30 30 30 30 30 30 30 30 30 30 30 31
               30 31 30 30 30 30 30 30 (=249500000000000101000000)
      57 13 -- Track 2 Equivalent Data
            54 11 11 88 88 88 88 82 d1 20 32 01 12 34 56 78
            90 00 0f (BINARY)
      5f 20 1a -- Cardholder Name
               53 4d 49 54 48 2f 4a 4f 48 4e 20 20 20 20 20 20
               20 20 20 20 20 20 20 20 20 20 (=SMITH/JOHN                )

---------------------------------------------------------------------
[Step 9] Send READ RECORD to read SFI 1 record 2
---------------------------------------------------------------------
00 B2 02 0c 00
response hex    :
70 50 5f 24 03 12 03 31 5f 25 03 09 02 05 5a 08
54 11 11 88 88 88 88 82 5f 34 01 01 9f 07 02 ff
00 8e 12 00 00 00 00 00 00 00 00 42 01 41 03 5e
03 42 03 1f 00 9f 0d 05 f0 20 24 28 00 9f 0e 05
00 50 80 00 00 9f 0f 05 f0 28 3c f8 00 5f 28 02
05 78
response SW1SW2 : 90 00
response ascii  : pP_$...1_%....Z.T......._4.................B.A.^.B....... $(.....P.......(<.._(..x
response parsed :

70 50 -- Record Template (EMV Proprietary)
      5f 24 03 -- Application Expiration Date
               12 03 31 (NUMERIC)
      5f 25 03 -- Application Effective Date
               09 02 05 (NUMERIC)
      5a 08 -- Application Primary Account Number (PAN)
            54 11 11 88 88 88 88 82 (NUMERIC)
      5f 34 01 -- Application Primary Account Number (PAN) Sequence Number
               01 (NUMERIC)
      9f 07 02 -- Application Usage Control
               ff 00 (BINARY)
      8e 12 -- Cardholder Verification Method (CVM) List
            00 00 00 00 00 00 00 00 42 01 41 03 5e 03 42 03
            1f 00 (BINARY)
      9f 0d 05 -- Issuer Action Code - Default
               f0 20 24 28 00 (BINARY)
      9f 0e 05 -- Issuer Action Code - Denial
               00 50 80 00 00 (BINARY)
      9f 0f 05 -- Issuer Action Code - Online
               f0 28 3c f8 00 (BINARY)
      5f 28 02 -- Issuer Country Code
               05 78 (NUMERIC)

---------------------------------------------------------------------
[Step 10] Send READ RECORD to read SFI 1 record 3
---------------------------------------------------------------------
00 B2 03 0c 00
response hex    :
70 47 9f 42 02 05 78 9f 44 01 02 9f 08 02 00 8c
8c 15 9f 02 06 9f 03 06 9f 1a 02 95 05 5f 2a 02
9a 03 9c 01 9f 37 04 8d 17 8a 02 9f 02 06 9f 03
06 9f 1a 02 95 05 5f 2a 02 9a 03 9c 01 9f 37 04
5f 30 02 02 01 9f 4a 01 82
response SW1SW2 : 90 00
response ascii  : pG.B..x.D...................._*......7................_*......7._0....J..
response parsed :

70 47 -- Record Template (EMV Proprietary)
      9f 42 02 -- Application Currency Code
               05 78 (NUMERIC)
      9f 44 01 -- Application Currency Exponent
               02 (NUMERIC)
      9f 08 02 -- Application Version Number - card
               00 8c (BINARY)
      8c 15 -- Card Risk Management Data Object List 1 (CDOL1)
            9f 02 06 -- Amount, Authorised (Numeric)
            9f 03 06 -- Amount, Other (Numeric)
            9f 1a 02 -- Terminal Country Code
            95 05 -- Terminal Verification Results (TVR)
            5f 2a 02 -- Transaction Currency Code
            9a 03 -- Transaction Date
            9c 01 -- Transaction Type
            9f 37 04 -- Unpredictable Number
      8d 17 -- Card Risk Management Data Object List 2 (CDOL2)
            8a 02 -- Authorisation Response Code
            9f 02 06 -- Amount, Authorised (Numeric)
            9f 03 06 -- Amount, Other (Numeric)
            9f 1a 02 -- Terminal Country Code
            95 05 -- Terminal Verification Results (TVR)
            5f 2a 02 -- Transaction Currency Code
            9a 03 -- Transaction Date
            9c 01 -- Transaction Type
            9f 37 04 -- Unpredictable Number
      5f 30 02 -- Service Code
               02 01 (NUMERIC)
      9f 4a 01 -- Static Data Authentication Tag List
               82 (BINARY)

---------------------------------------------------------------------
[Step 11] Send READ RECORD to read SFI 1 record 4
---------------------------------------------------------------------
00 B2 04 0c 00
response hex    :
70 81 c0 8f 01 07 90 81 90 04 71 93 ac fb 32 3a
bb 95 ac e6 c5 b4 69 27 6d b5 93 16 73 cb a2 e0
ee 23 37 9d 02 79 50 b6 c1 c8 4d 59 e9 aa 7a 54
1b 51 06 0b 0b df 51 4f 44 40 10 2b ee e8 4c 38
3a ce 13 b0 72 84 4e 97 a6 5e 0e 69 b1 c8 c5 dc
f3 08 b4 26 b8 b3 3d 72 07 ff 29 a7 7d d5 64 46
ae 8d ba b8 d1 b9 ea 6a 32 ab 11 64 e7 35 2c 14
6d 0a 61 e6 de b1 ec 2f 91 25 27 b9 ce df 72 a9
b0 86 3a 9c 45 b4 9a 81 8a f4 69 8c 71 c9 72 d2
eb 25 41 84 5e 4d f8 a3 49 9f 32 01 03 92 24 5b
c8 f7 38 4c 06 dc dc 35 97 51 d1 d4 31 52 0d f5
ff 2d 43 47 4a 88 60 3c 9e fc a0 66 6a 1a 42 bd
f0 a4 f5
response SW1SW2 : 90 00
response ascii  : p.........q...2:......i'm...s....#7..yP...MY..zT.Q....QOD@.+..L8:...r.N..^.i.......&..=r..).}.dF.......j2..d.5,.m.a..../.%'...r...:.E.....i.q.r..%A.^M..I.2...$[..8L...5.Q..1R...-CGJ.`<...fj.B.... [`]
response parsed :

70 81 c0 -- Record Template (EMV Proprietary)
         8f 01 -- Certification Authority Public Key Index - card
               07 (BINARY)
         90 81 90 -- Issuer Public Key Certificate
                  04 71 93 ac fb 32 3a bb 95 ac e6 c5 b4 69 27 6d
                  b5 93 16 73 cb a2 e0 ee 23 37 9d 02 79 50 b6 c1
                  c8 4d 59 e9 aa 7a 54 1b 51 06 0b 0b df 51 4f 44
                  40 10 2b ee e8 4c 38 3a ce 13 b0 72 84 4e 97 a6
                  5e 0e 69 b1 c8 c5 dc f3 08 b4 26 b8 b3 3d 72 07
                  ff 29 a7 7d d5 64 46 ae 8d ba b8 d1 b9 ea 6a 32
                  ab 11 64 e7 35 2c 14 6d 0a 61 e6 de b1 ec 2f 91
                  25 27 b9 ce df 72 a9 b0 86 3a 9c 45 b4 9a 81 8a
                  f4 69 8c 71 c9 72 d2 eb 25 41 84 5e 4d f8 a3 49 (BINARY)
         9f 32 01 -- Issuer Public Key Exponent
                  03 (BINARY)
         92 24 -- Issuer Public Key Remainder
               5b c8 f7 38 4c 06 dc dc 35 97 51 d1 d4 31 52 0d
               f5 ff 2d 43 47 4a 88 60 3c 9e fc a0 66 6a 1a 42
               bd f0 a4 f5 (BINARY)

---------------------------------------------------------------------
[Step 12] Send READ RECORD to read SFI 1 record 5
---------------------------------------------------------------------
00 B2 05 0c 00
response hex    :
70 81 93 93 81 90 41 7c 43 3e 07 08 e7 14 4e ce
c1 d3 6b bf 44 09 2e fe 27 3d aa 24 cb 34 c3 77
9e 4f 29 e7 7f 59 10 a9 c5 7e 0c bb e3 73 81 93
b3 51 f5 e4 66 18 75 1f 0a 5f fb 59 c7 76 1f f1
28 8d dd ac a8 86 9b 61 14 b0 5c 6b 79 e4 d3 2b
97 95 c7 b4 ea e4 62 17 1b 05 90 7d 67 09 03 4e
58 26 aa 97 a8 d8 ab 71 c5 70 a5 8d 4a 4a f0 a5
a7 06 5e 7a 22 ec 9b d3 a0 06 f2 4d 29 40 9c 22
88 87 c8 14 2a f1 37 da d9 f8 3c 64 96 32 ce ab
8b 3c 1c d1 eb 58
response SW1SW2 : 90 00
response ascii  : p.....A|C>....N...k.D...'=.$.4.w.O)..Y...~...s...Q..f.u.._.Y.v..(......a..\ky..+......b....}g..NX&.....q.p..JJ....^z"......M)@."....*.7...<d.2...<...X [']
response parsed :

70 81 93 -- Record Template (EMV Proprietary)
         93 81 90 -- Signed Static Application Data
                  41 7c 43 3e 07 08 e7 14 4e ce c1 d3 6b bf 44 09
                  2e fe 27 3d aa 24 cb 34 c3 77 9e 4f 29 e7 7f 59
                  10 a9 c5 7e 0c bb e3 73 81 93 b3 51 f5 e4 66 18
                  75 1f 0a 5f fb 59 c7 76 1f f1 28 8d dd ac a8 86
                  9b 61 14 b0 5c 6b 79 e4 d3 2b 97 95 c7 b4 ea e4
                  62 17 1b 05 90 7d 67 09 03 4e 58 26 aa 97 a8 d8
                  ab 71 c5 70 a5 8d 4a 4a f0 a5 a7 06 5e 7a 22 ec
                  9b d3 a0 06 f2 4d 29 40 9c 22 88 87 c8 14 2a f1
                  37 da d9 f8 3c 64 96 32 ce ab 8b 3c 1c d1 eb 58 (BINARY)

---------------------------------------------------------------------
[Step 13] Send GET DATA command to find the Application Transaction Counter (ATC)
---------------------------------------------------------------------
80 CA 9F 36 00
response hex    :
9f 36 02 00 79
response SW1SW2 : 90 00
response ascii  : .6..y
response parsed :

9f 36 02 -- Application Transaction Counter (ATC)
         00 79 (BINARY)

---------------------------------------------------------------------
[Step 14] Send GET DATA command to find the Last Online ATC Register
---------------------------------------------------------------------
80 CA 9F 13 00
response hex    :
9f 13 02 00 67
response SW1SW2 : 90 00
response ascii  : ....g
response parsed :

9f 13 02 -- Last Online Application Transaction Counter (ATC) Register
         00 67 (BINARY)

---------------------------------------------------------------------
[Step 15] Send GET DATA command to find the PIN Try Counter
---------------------------------------------------------------------
80 CA 9F 17 00
response hex    :
9f 17 01 03
response SW1SW2 : 90 00
response ascii  : ....
response parsed :

9f 17 01 -- Personal Identification Number (PIN) Try Counter
         03 (BINARY)

---------------------------------------------------------------------
[Step 16] Send GET DATA command to find the Log Format
---------------------------------------------------------------------
80 CA 9F 4F 00
response hex    :

response SW1SW2 : 6a 81
response ascii  : 
response parsed :


---------------------------------------------------------------------
[Step 17] VERIFY (PIN)
---------------------------------------------------------------------
00 20 00 80 08 24 12 34 ff ff ff ff ff
response hex    :

response SW1SW2 : 90 00
response ascii  : 
response parsed :


---------------------------------------------------------------------
[Step 18] Select application by AID
---------------------------------------------------------------------
00 A4 04 00 07 d5 78 00 00 02 10 10
response hex    :
6f 2e 84 07 d5 78 00 00 02 10 10 a5 23 50 09 62
61 6e 6b 61 78 65 70 74 87 01 01 5f 2d 02 6e 6f
9f 11 01 01 9f 12 09 62 61 6e 6b 61 78 65 70 74
response SW1SW2 : 90 00
response ascii  : o....x......#P.bankaxept..._-.no.......bankaxept
response parsed :

6f 2e -- File Control Information (FCI) Template
      84 07 -- Dedicated File (DF) Name
            d5 78 00 00 02 10 10 (BINARY)
      a5 23 -- File Control Information (FCI) Proprietary Template
            50 09 -- Application Label
                  62 61 6e 6b 61 78 65 70 74 (=bankaxept)
            87 01 -- Application Priority Indicator
                  01 (BINARY)
            5f 2d 02 -- Language Preference
                     6e 6f (=no)
            9f 11 01 -- Issuer Code Table Index
                     01 (NUMERIC)
            9f 12 09 -- Application Preferred Name
                     62 61 6e 6b 61 78 65 70 74 (=bankaxept)

---------------------------------------------------------------------
[Step 19] Send GET PROCESSING OPTIONS command
---------------------------------------------------------------------
80 A8 00 00 02 83 00
response hex    :
80 06 18 00 08 01 01 00
response SW1SW2 : 90 00
response ascii  : ........
response parsed :

80 06 -- Response Message Template Format 1
      18 00 08 01 01 00 (BINARY)

---------------------------------------------------------------------
[Step 20] Send READ RECORD to read SFI 1 record 1
---------------------------------------------------------------------
00 B2 01 0c 00
response hex    :
70 6e 5a 09 95 78 52 64 12 34 56 78 90 5f 34 01
02 5f 24 03 12 03 29 57 13 95 78 52 64 12 34 56
78 90 d1 20 36 01 12 34 56 78 90 0f 8c 15 9f 02
06 9f 03 06 9f 1a 02 95 05 5f 2a 02 9a 03 9c 01
9f 37 04 8d 17 8a 02 9f 02 06 9f 03 06 9f 1a 02
95 05 5f 2a 02 9a 03 9c 01 9f 37 04 8e 0a 00 00
00 00 00 00 00 00 02 00 9f 0d 05 b0 40 04 88 00
response SW1SW2 : 90 00
response ascii  : pnZ..xRd.4Vx._4.._$...)W..xRd.4Vx.. 6..4Vx..............._*......7................_*......7.................@...
response parsed :

70 6e -- Record Template (EMV Proprietary)
      5a 09 -- Application Primary Account Number (PAN)
            95 78 52 64 12 34 56 78 90 (NUMERIC)
      5f 34 01 -- Application Primary Account Number (PAN) Sequence Number
               02 (NUMERIC)
      5f 24 03 -- Application Expiration Date
               12 03 29 (NUMERIC)
      57 13 -- Track 2 Equivalent Data
            95 78 52 64 12 34 56 78 90 d1 20 36 01 12 34 56
            78 90 0f (BINARY)
      8c 15 -- Card Risk Management Data Object List 1 (CDOL1)
            9f 02 06 -- Amount, Authorised (Numeric)
            9f 03 06 -- Amount, Other (Numeric)
            9f 1a 02 -- Terminal Country Code
            95 05 -- Terminal Verification Results (TVR)
            5f 2a 02 -- Transaction Currency Code
            9a 03 -- Transaction Date
            9c 01 -- Transaction Type
            9f 37 04 -- Unpredictable Number
      8d 17 -- Card Risk Management Data Object List 2 (CDOL2)
            8a 02 -- Authorisation Response Code
            9f 02 06 -- Amount, Authorised (Numeric)
            9f 03 06 -- Amount, Other (Numeric)
            9f 1a 02 -- Terminal Country Code
            95 05 -- Terminal Verification Results (TVR)
            5f 2a 02 -- Transaction Currency Code
            9a 03 -- Transaction Date
            9c 01 -- Transaction Type
            9f 37 04 -- Unpredictable Number
      8e 0a -- Cardholder Verification Method (CVM) List
            00 00 00 00 00 00 00 00 02 00 (BINARY)
      9f 0d 05 -- Issuer Action Code - Default
               b0 40 04 88 00 (BINARY)

---------------------------------------------------------------------
[Step 21] Send GET DATA command to find the Application Transaction Counter (ATC)
---------------------------------------------------------------------
80 CA 9F 36 00
response hex    :
9f 36 02 01 73
response SW1SW2 : 90 00
response ascii  : .6..s
response parsed :

9f 36 02 -- Application Transaction Counter (ATC)
         01 73 (BINARY)

---------------------------------------------------------------------
[Step 22] Send GET DATA command to find the Last Online ATC Register
---------------------------------------------------------------------
80 CA 9F 13 00
response hex    :
9f 13 02 01 72
response SW1SW2 : 90 00
response ascii  : ....r
response parsed :

9f 13 02 -- Last Online Application Transaction Counter (ATC) Register
         01 72 (BINARY)

---------------------------------------------------------------------
[Step 23] Send GET DATA command to find the PIN Try Counter
---------------------------------------------------------------------
80 CA 9F 17 00
response hex    :
9f 17 01 03
response SW1SW2 : 90 00
response ascii  : ....
response parsed :

9f 17 01 -- Personal Identification Number (PIN) Try Counter
         03 (BINARY)

---------------------------------------------------------------------
[Step 24] Send GET DATA command to find the Log Format
---------------------------------------------------------------------
80 CA 9F 4F 00
response hex    :

response SW1SW2 : 6a 81
response ascii  : 
response parsed :

======================================
               [EMVCard]              
======================================
Answer To Reset (ATR)
   3b 67 00 00 a6 40 40 00 09 90 00
   Description From Public Database - [Visa card issued by Norway bank DNBNor, VISA Classic - Landkreditt Bank (Norway), VISA Classic - Nordea Bank (Norway)]
   ISO Compliant Answer To Reset (ATR)
      Convention - DIRECT
      Protocol - T=0
      Historical bytes - a6 40 40 00 09 90 00


   Directory Definition File
      Name: 315041592e5359532e4444463031 (=1PAY.SYS.DDF01)
      Issuer Code Table Index: 1 (ISO-8859-1)
      Short File Identifier:
         2 (Governed by the EMV specification)
      Language Preference (in order of preference):
         Language: no (Norwegian)
         Language: en (English)


      Applications (2 found):

         Application
            AID: a1 23 45 67 89 10 10
            Label: VISA
            Preferred Name: VISA Classic
            Application Effective Date: Thu Feb 05 00:00:00 CET 2009
            Application Expiration Date: Sat Mar 31 00:00:00 CEST 2012
            Application Version Number: 140
            Application Currency Code (ISO 4217): 578 (NOK Norwegian Krone)
            Application Currency Exponent: 2 (Position of the decimal point from the right)
            Issuer Country Code (ISO 3166-1): 578 (Norway)
            Application Transaction Counter (ATC): 121
            Last Online ATC Register: 103
            PIN Try Counter: 3 (Number of PIN tries remaining)
            Cardholder Name: SMITH/JOHN                
            Primary Account Number (PAN) - 5411118888888882
               Major Industry Identifier = 5 (Banking and financial)
               Issuer Identifier Number: 541111
               Account Number: 888888888
               Check Digit: 2 (Valid)
            PAN Sequence Number: 1
            Application Priority Indicator
               May be selected without cardholder confirmation
               Selection Priority: 2
            Application Interchange Profile
               Static Data Authentication (SDA) supported
               Dynamic Data Authentication (DDA) not supported
               Cardholder verification is supported
               Terminal risk management is to be performed
               Issuer authentication is supported
               CDA not supported
            Application File Locator
               Application Elementary File
                  Short File Identifier:
                     1 (Governed by the EMV specification)
                  Start Record: 1
                  End Record: 1
                  Number of Records Involved In Offline Data Authentication: 0
                  Record: 1
                     Length: 79
                     Involved In Offline Data Authentication: false
               Application Elementary File
                  Short File Identifier:
                     1 (Governed by the EMV specification)
                  Start Record: 2
                  End Record: 5
                  Number of Records Involved In Offline Data Authentication: 1
                  Record: 2
                     Length: 82
                     Involved In Offline Data Authentication: true
                  Record: 3
                     Length: 73
                     Involved In Offline Data Authentication: false
                  Record: 4
                     Length: 195
                     Involved In Offline Data Authentication: false
                  Record: 5
                     Length: 150
                     Involved In Offline Data Authentication: false
            Application Usage Control
               Valid for domestic cash transactions
               Valid for international cash transactions
               Valid for domestic goods
               Valid for international goods
               Valid for domestic services
               Valid for international services
               Valid at ATMs
               Valid at terminals other than ATMs
               Domestic cashback not allowed
               International cashback not allowed
            Processing Options Data Object List
               Terminal Country Code (2 bytes)
               Transaction Currency Code (2 bytes)
            Issuer Public Key Certificate
               Issuer Identifier: 492564
               CA Public Key Index: 7
               Certificate Format: 2
               Certificate Expiration Date (MMYY): 1214
               Certificate Serial Number: 00e16d (57709)
               Hash Algorithm Indicator: 1 (=SHA-1)
               Issuer Public Key Algorithm Indicator: 1 (=RSA)
               Hash: b6819d8d5af4034214973edbad1bd2866a550dbb
               Issuer Public Key
                  Length: 1152bit
                  Exponent:
                     03
                  Modulus:
                     ba 53 3e b8 ec c9 f9 b8 b2 a3 5e ed 3b e0 3f 7d
                     3a cf e2 46 a3 4c 8e 75 f5 c7 4a 64 e6 5c 97 cb
                     4f 2f ab 97 09 cf 7e 12 89 0e af f1 8a 4f cf b4
                     fa 98 18 db c3 be 5f dc 65 91 54 46 cb 86 24 ac
                     2d 1e 07 72 f2 52 49 02 f9 8b a5 5b 4b 4b 11 00
                     1e 4e cf b7 0f 12 19 a3 97 12 98 e7 ed c5 b9 2b
                     8d 44 c9 80 e2 f6 8f 90 8f 9d ad 78 5b c8 f7 38
                     4c 06 dc dc 35 97 51 d1 d4 31 52 0d f5 ff 2d 43
                     47 4a 88 60 3c 9e fc a0 66 6a 1a 42 bd f0 a4 f5
            Card Risk Management Data Object List 1
               Amount, Authorised (Numeric) (6 bytes)
               Amount, Other (Numeric) (6 bytes)
               Terminal Country Code (2 bytes)
               Terminal Verification Results (TVR) (5 bytes)
               Transaction Currency Code (2 bytes)
               Transaction Date (3 bytes)
               Transaction Type (1 byte)
               Unpredictable Number (4 bytes)
            Card Risk Management Data Object List 2
               Authorisation Response Code (2 bytes)
               Amount, Authorised (Numeric) (6 bytes)
               Amount, Other (Numeric) (6 bytes)
               Terminal Country Code (2 bytes)
               Terminal Verification Results (TVR) (5 bytes)
               Transaction Currency Code (2 bytes)
               Transaction Date (3 bytes)
               Transaction Type (1 byte)
               Unpredictable Number (4 bytes)
            Signed Static Application Data
               Hash Algorithm Indicator: 1 (=SHA-1)
               Data Authentication Code: 0123
               Hash: 74159900848ab829b9f0318950cdad9351e0bfdf
            Cardholder Verification Method (CVM) List:
               Cardholder Verification Rule
                  Rule: Enciphered PIN verified online
                  Condition Code: If unattended cash
                  Apply succeeding CV Rule if this CVM is unsuccessful
               Cardholder Verification Rule
                  Rule: Plaintext PIN verification performed by ICC
                  Condition Code: If terminal supports the CVM
                  Apply succeeding CV Rule if this CVM is unsuccessful
               Cardholder Verification Rule
                  Rule: If transaction is in the application currency and is under 0.00 value
                  Condition Code: If terminal supports the CVM
                  Apply succeeding CV Rule if this CVM is unsuccessful
               Cardholder Verification Rule
                  Rule: Enciphered PIN verified online
                  Condition Code: If terminal supports the CVM
                  Apply succeeding CV Rule if this CVM is unsuccessful
               Cardholder Verification Rule
                  Rule: If transaction is in the application currency and is over 0.00 value
                  Condition Code: Always
                  Fail cardholder verification if this CVM is unsuccessful
            Static Data Authentication Tag List
               Application Interchange Profile
            Track 1 Discretionary Data:
               323439353030303030303030303030313031303030303030 (ASCII: 249500000000000101000000)
            Track 2 Equivalent Data:
               Primary Account Number (PAN) - 5411118888888882
                  Major Industry Identifier = 5 (Banking and financial)
                  Issuer Identifier Number: 541111
                  Account Number: 888888888
                  Check Digit: 2 (Valid)
               Expiration Date: Wed Feb 29 00:00:00 CET 2012
               Service Code: 201
               Discretionary Data: 1234567890000
            Service Code: 201
            Language Preference (in order of preference):
               Language: no (Norwegian)
               Language: en (English)
            Issuer Code Table Index: 1 (ISO-8859-1)
            Issuer Action Code - Default:
               11110000
               00100000
               00100100
               00101000
               00000000
            Issuer Action Code - Denial:
               00000000
               01010000
               10000000
               00000000
               00000000
            Issuer Action Code - Online:
               11110000
               00101000
               00111100
               11111000
               00000000

         Application
            AID: d5 78 00 00 02 10 10
            Label: bankaxept
            Preferred Name: bankaxept
            Application Expiration Date: Thu Mar 29 00:00:00 CEST 2012
            Application Transaction Counter (ATC): 115
            Last Online ATC Register: 114
            PIN Try Counter: 3 (Number of PIN tries remaining)
            Primary Account Number (PAN) - 957852641234567890
               Major Industry Identifier = 9 (For assignment by national standards bodies)
               Country Code (ISO 3166-1): 578 (=Norway)
               Issuer Identifier Number: 957852
               Account Number: 64123456789
               Check Digit: 0 (Valid)
            PAN Sequence Number: 2
            Application Priority Indicator
               May be selected without cardholder confirmation
               Selection Priority: 1
            Application Interchange Profile
               Static Data Authentication (SDA) not supported
               Dynamic Data Authentication (DDA) not supported
               Cardholder verification is supported
               Terminal risk management is to be performed
               Issuer authentication is not supported
               CDA not supported
            Application File Locator
               Application Elementary File
                  Short File Identifier:
                     1 (Governed by the EMV specification)
                  Start Record: 1
                  End Record: 1
                  Number of Records Involved In Offline Data Authentication: 0
                  Record: 1
                     Length: 112
                     Involved In Offline Data Authentication: false
            Card Risk Management Data Object List 1
               Amount, Authorised (Numeric) (6 bytes)
               Amount, Other (Numeric) (6 bytes)
               Terminal Country Code (2 bytes)
               Terminal Verification Results (TVR) (5 bytes)
               Transaction Currency Code (2 bytes)
               Transaction Date (3 bytes)
               Transaction Type (1 byte)
               Unpredictable Number (4 bytes)
            Card Risk Management Data Object List 2
               Authorisation Response Code (2 bytes)
               Amount, Authorised (Numeric) (6 bytes)
               Amount, Other (Numeric) (6 bytes)
               Terminal Country Code (2 bytes)
               Terminal Verification Results (TVR) (5 bytes)
               Transaction Currency Code (2 bytes)
               Transaction Date (3 bytes)
               Transaction Type (1 byte)
               Unpredictable Number (4 bytes)
            Cardholder Verification Method (CVM) List:
               Cardholder Verification Rule
                  Rule: Enciphered PIN verified online
                  Condition Code: Always
                  Fail cardholder verification if this CVM is unsuccessful
            Track 2 Equivalent Data:
               Primary Account Number (PAN) - 957852641234567890
                  Major Industry Identifier = 9 (For assignment by national standards bodies)
                  Country Code (ISO 3166-1): 578 (=Norway)
                  Issuer Identifier Number: 957852
                  Account Number: 64123456789
                  Check Digit: 0 (Valid)
               Expiration Date: Wed Feb 29 00:00:00 CET 2012
               Service Code: 601
               Discretionary Data: 12345678900
            Language Preference (in order of preference):
               Language: no (Norwegian)
            Issuer Code Table Index: 1 (ISO-8859-1)
            Issuer Action Code - Default:
               10110000
               01000000
               00000100
               10001000
               00000000

---------------------------------------
                FINISHED               
---------------------------------------
```