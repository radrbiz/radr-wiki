---
title: Google Authentor
chapter: 1
order: 4
layout: default.en
lang: en
---

* auto-gen TOC
{:toc}

# Google Authentor

Google Authenticator v2.33 is an application that implements TOTP security tokens from RFC 6238 in mobile apps made by Google, sometimes branded "Two-step verification" (or 2-Step Verification). Authenticator provides a six- to eight-digit one-time password which users must provide in addition to their username and password to log into Google services or other sites. The Authenticator can also generate codes for third-party applications, such as password managers or file hosting services. Previous versions of the software were open source. 

## Technical description

The service provider generates an 80-bit secret key for each user. This is provided as a 16, 24 or 32 character base32 string or as a QR code. The client creates an HMAC-SHA1 using this secret key. The message that is HMAC-ed can be:

the number of 30 second periods having elapsed since the Unix epoch; or
the counter that is incremented with each new code.
A portion of the HMAC is extracted and converted to a 6 digit code.

Pseudocode for One Time Pasword OTP

```
 function GoogleAuthenticatorCode(string secret)
   key := base32decode(secret)
   message := floor(current Unix time / 30)
   hash := HMAC-SHA1(key, message)
   offset := value of last nibble of hash
   truncatedHash := hash[offset..offset+3]  //4 bytes starting at the offset
   Set the first bit of truncatedHash to zero  //remove the most significant bit 
   code := truncatedHash mod 1000000
   pad code with 0 until length of code is 6
   return code 
```

Pseudocode for Event/Counter OTP

```
 function GoogleAuthenticatorCode(string secret)
     key := base32decode(secret)
     message := counter encoded on 8 bytes
     hash := HMAC-SHA1(key, message)
     offset := last nibble of hash
     truncatedHash := hash[offset..offset+3]  //4 bytes starting at the offset
     Set the first bit of truncatedHash to zero  //remove the most significant bit 
     code := truncatedHash mod 1000000
     pad code with 0 until length of code is 6
     return code 
```

## Notice!!!

Google Authenticator use timestamp as the message in the codes above, so Please try to keep your phone time synchronized with the standard time in order to avoid verification failure.

## Enable Google Authenticator

### Download Google Authenticator

Google Authenticator supports iOS，Android and blackberry;
  1. iOS: include iphone，ipad，ipod touch；Search google authenticator in AppStore or Click [🌐  here](https://itunes.apple.com/en/app/google-authenticator/id388497605) to download；
  2. Android：You should have Android 2.1 or above installed in your phone before you can use. Search google authenticator in google play or any other markets；
  3. BlackBerry：Open browser of BlackBerry, visit m.google.com/authenticator, download and install.

### Enable Google Authenticator on RadrTrade

  1. Go to “Settings”-“Password management”-“Dynamic password”，select enable Google Authenticator.
  2. Select Google Authenticator on the dialog.
  3. Press ok，and enter your password.（SMS code is required if SMS is enabled.）
  4. A barcode will be displayed after the verification.
  5. Open the Google Authenticator app on your phone
    - ![img_3347](/assets/images/google_authenticate/img_3347.jpg){:height="400px" width="100px"}
  6. scan the barcode and add it to your code list.
    - ![img_3348](/assets/images/google_authenticate/img_3348.png){:height="400px" width="100px"}
  7. You should input this code when needed in RadrTrade.

### Close Google Authentication in RadrTrade

  1. Go to “Settings”-“Password management”-“Dynamic password”, choose “Close”
  2. Input payment password and Google Authenticator code on the unlock dialog.
  3. Google Authenticator will be closed after password verification.
  4. Tips：Reopen Google Authentication will use the save code before, you could choose "Change" or "Reset" to change the code.

### Find your Google Authenticator back

If you have passed the ID Verification, you can submit feedback order to reset it.
