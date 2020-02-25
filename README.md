# Secrets App

Secrets website is modeled from Whisper App which allows user to submit their secrets anonymously. This application was built for the purpose of practicing and understanding different levels of authentication and security.    


## Built With

* EJS
* CSS
* Javascript
* NodeJs & Express
* Mongoose

## What I learned building Secrets

* A better understanding of Authentication and why we need to authenticate.
          * Protect and associate user data with individual users
          * Restrict access to certain areas of website depending on status of user i.e. paid services
          * Authentication can be done in many ways dependent on how secure you want your website/app.


* Level 1 Security - Email & Password


          * User email and password stored using Mongoose & MongoDB

          * This level of security displays the users' password in plaintext in database.

          * Most users use the same email & password across multiple sites so storing user passwords in plaintext is a definite NO!


* Level 2 Security - Encryption


          * Encryption is basically scrambling the original message.

          * Examples of encryption:
              * Caesar's cipher
              * Vigenere's cipher

          * Encryption requires a key to unscramble message

          * NPM package mongoose-encryption is used to achieve encryption https://www.npmjs.com/package/mongoose-encryption


          ```const secret = "Thisismylittlesecret.";

          userSchema.plugin(encrypt, { secret: secret, encryptedFields: ['password']});

          ```
          
          * mongoose-encryption works by encrypting when the `save()` is called and decrypt when `find()` is called.
          * The password field is now long binary string instead of plaintext
          * This level of security is not much more secure compared to Level 1 because secret password is exposed in app.js
