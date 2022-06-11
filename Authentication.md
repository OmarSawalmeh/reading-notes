# **Authentication :**
---
---
## **Securing Passwords with Bcrypt Hashing Function :**
Passwords are the first line of defense against cyber criminals. It is the most vital secret of every activity we do over the internet and also a final check to get into any of your user account, whether it is your bank account, email account, shopping cart account or any other account you have.
We all know storing passwords in clear text in your database is ridiculous. Many desktop applications and almost every web service including, blogs, forums eventually need to store a collection of user data and the passwords, that has to be stored using a hashing algorithm.
Cryptographic hash algorithms MD5, SHA1, SHA256, SHA512, SHA-3 are general purpose hash functions, designed to calculate a digest of huge amounts of data in as short a time as possible. Hashing is the greatest way for protecting passwords and considered to be pretty safe for ensuring the integrity of data or password.
The benefit of hashing is that if someone steals the database with hashed passwords, they only make off with the hashes and not the actual plaintext passwords. But why do we always hear about passwords being cracked? There are some weaknesses in cryptographic hash algorithm that allows an attacker to calculate the original value of a hashed password, as explained below:
PROBLEMS WITH CRYPTOGRAPHIC HASH ALGORITHM
Brute Force attack: Hashes can't be reversed, so instead of reversing the hash of the password, an attacker can simply keep trying different inputs until he does not find the right now that generates the same hash value, called brute force attack.
General-purpose hash function designed for speed,because they are often used to calculate checksum values for large data sets and files, to check for data integrity. Using a modern computer one can crack a 16 Character Strong password in less than an hour, thanks to GPU.
Hash Collision attack: Hash functions have infinite input length and a predefined output length, so there is inevitably going to be the possibility of two different inputs that produce the same output hash. MD5, SHA1, SHA2 are vulnerable to Hash Collision Attack i.e. two input strings of a hash function that produce the same hash result.
Salting your password may foil dictionary attacks, but an attacker can still use a wordlist to crack the hashes. So, what exactly could be a good for securing your passwords with hashing?
BCrypt, IT's SLOW AND STRONG AS HELL
To overcome such issues, we need algorithms which can make the brute force attacks slower and minimize the impact. Such algorithms are PBKDF2 and BCrypt, both of these algorithms use a technique called Key Stretching.
Bcrypt is an adaptive hash function based on the Blowfish symmetric block cipher cryptographic algorithm and introduces a work factor (also known as security factor), which allows you to determine how expensive the hash function will be.
This work factor value determines how slow the hash function will be, means different work factor will generate different hash values in different time span, which makes it extremely resistant to brute force attacks. When computers become faster next year we can increase the work factor to balance it out i.e. to make the attack slower.
This hashing algorithm is implemented in a number programming languages like PHP, Java, Ruby, C#, C etc. If you are a PHP developer, you can simply use the crypt() function with a Blowfish required salt.
![](https://i.stack.imgur.com/ovvAZ.png)

---
## **Authentication Cheat Sheet¶**
## Introduction¶
Authentication is the process of verifying that an individual, entity or website is whom it claims to be. Authentication in the context of web applications is commonly performed by submitting a username or ID and one or more items of private information that only a given user should know.

Session Management is a process by which a server maintains the state of an entity interacting with it. This is required for a server to remember how to react to subsequent requests throughout a transaction. Sessions are maintained on the server by a session identifier which can be passed back and forward between the client and server when transmitting and receiving requests. Sessions should be unique per user and computationally very difficult to predict. The Session Management Cheat Sheet contains further guidance on the best practices in this area.

## Authentication General Guidelines¶
**User IDs¶**<br/>
Make sure your usernames/user IDs are case-insensitive. User 'smith' and user 'Smith' should be the same user. Usernames should also be unique. For high-security applications, usernames could be assigned and secret instead of user-defined public data.

**Email address as a User ID¶**<br/>
For information on validating email addresses, please visit the input validation cheatsheet email discussion.

**Authentication Solution and Sensitive Accounts¶**<br/>
Do NOT allow login with sensitive accounts (i.e. accounts that can be used internally within the solution such as to a back-end / middle-ware / DB) to any front-end user-interface
Do NOT use the same authentication solution (e.g. IDP / AD) used internally for unsecured access (e.g. public access / DMZ)
Implement Proper Password Strength Controls¶
A key concern when using passwords for authentication is password strength. A "strong" password policy makes it difficult or even improbable for one to guess the password through either manual or automated means. The following characteristics define a strong password.

---

## **node.bcrypt.js**
[References for node.js Authentication](https://www.npmjs.com/package/bcrypt)

---
- [BACK (Main Page)](./README.md)
---

