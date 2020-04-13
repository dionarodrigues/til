# How to create UUIDs in javascript

__A universally unique identifier (UUID) or globally unique identifier (GUID) is a 128-bit number used to identify information in computer systems according to [RFC 4122](https://www.ietf.org/rfc/rfc4122.txt).__

We can use [**uuidv4**](https://github.com/thenativeweb/uuidv4) to generate a unique identifier for an object in javascript. 

Currently I'm using the UUID npm dependency in Node.js projects to manipulate data in Postgres database.

## Basic format of UUID
It's five segments of seemingly random hex data, beginning with eight hex characters, followed by three four-character strings, then 12 characters at the end. These segments are separated by a “-”.

![](https://developer.akamai.com/sites/default/files/inline-images/Screen%20Shot%202019-09-06%20at%202.03.42%20PM.png)
