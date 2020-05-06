# 👌 Hashing Passwords with Node.js and Bcryptjs

__The [bcryptjs](https://www.npmjs.com/package/bcryptjs) library on NPM makes it really easy to hash and compare passwords in Node.js__

---

## Some features of bcryptjs

- __Salted hashing__: Generating random bytes (the salt) and combining it with the password before hashing creates unique hashes across each user’s password. If two users have the same password they will not have the same password hash.

- __saltRounds__: Bcryptjs allows us to choose the value of saltRounds, which gives us control over the cost of processing the data. The higher this number is, the longer it takes for the machine to calculate the hash associated with the password and the more securityit it is. 8 is a good value for saltRounds.

-- 

## How to use

```
const hashedPassword = hash(password, 8);
```
