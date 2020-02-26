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


  - Protect and associate user data with individual users

  - Restrict access to certain areas of website depending on status of user i.e. paid services

  - Authentication can be done in many ways dependent on how secure you want your website/app.


* __Level 1 Security - Email & Password__


  - User email and password stored using Mongoose & MongoDB

  - This level of security displays the users' password in plaintext in database.

  - Most users use the same email & password across multiple sites so storing user passwords in plaintext is a definite NO!


* __Level 2 Security - Encryption__


  - Encryption is basically taking a password and using some type of key and cipher method to ciphertext.

  - Examples of encryption:
      * Caesar's cipher
      * Vigenere's cipher

  - Encryption requires a key to unscramble message

  - NPM package mongoose-encryption is used to achieve encryption <https://www.npmjs.com/package/mongoose-encryption>

  - mongoose-encryption works by encrypting when the `save()` is called and decrypt when `find()` is called.

  - The password field is now long binary string instead of plaintext

  - This level of security is not much more secure compared to Level 1 because secret password is exposed in app.js


        const secret = "Thisismylittlesecret.";

        userSchema.plugin(encrypt, { secret: secret, encryptedFields: ['password']});

        // This adds _ct and _ac fields to the schema, as well as pre 'init' and pre 'save' middleware,
        // and encrypt, decrypt, sign, and authenticate instance methods

  - To combat this issue environment variables we used.  I accomplished this by using an npm module dotenv <https://www.npmjs.com/package/dotenv>

  - Environment variables are kept in a simple .env file which is used to keep sensitive variables and/or API keys safe.

* __Level 3 Security - Hashing__

  - Hashing takes away the need of an encryption key as previous needed with Level 2 security.

  - Hashing uses a hash function turns to passwords and/or sensitive data into a hashes. Hash passwords are then stored into the db

  - Hash functions are mathematical equations that are designed to make it almost impossible to go backwards.

  - Hashing was achieved by using NPM module md5 <https://www.npmjs.com/package/md5>

  - When a hash function is ran on a value it produces the same hash value every time. This eliminates the need for reversing the function for data verification.
