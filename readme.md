Tomorrow
========

> Close your eyes and I'll kiss you, tomorrow I'll miss you -- The Beatles

This is a logging server using hyperloglog in Redis to count unique anonymous visitors, containing and serving as well the JavaScript library for doing client fingerprinting.

Usage: require('tomorrow').start({
	port : 8081, // Optional. Port to run server on.
	redisPass : "foobar", // Optional. Redis password.
	redisPort : 6379 // Optional. Port Redis is running on.
})

This starts a server with three routes:

/test - will load test.html file so you can play with library
/fingerprint - returns a js library that takes user fingerprints.
/log/:fingerprint - sending a :fingerprint hash to /log stores the print.
/count - returns the current cardinality (estimate of unique fingerprints)

On the client, get the library via /fingerprint, then run this JavaScript command to get the current client's unique fingerprint: 

new Fingerprint().get()

Optionally, you can add more accuracy with canvas:

new Fingerprint({canvas: true}).get())

( http://cseweb.ucsd.edu/~hovav/dist/canvas.pdf )


