# The Hash Method

First, a quick lesson over the hash method. The [hash method](http://ruby-doc.org/core-2.1.2/Object.html#method-i-hash) is an Object level method that produces a 64 bit number that should be unique to the object it is called on. So, any time that you call `.hash` on anything, it provides you with a unique number that you can use to identify it with.  Here are a couple examples of what `.hash` will do:

```ruby
"This is a string".hash
=> -1954425285861713910
3.hash
=> 525195615531772641
{}.hash
=> 972105201414601777
[].hash
=> -270653834513852927
3.5.hash
=> -858263241639918961
:symbol.hash
=> 3679609551628441338
"This is a string".hash
=> -1954425285861713910
```

* NOTE: Your .hash values WILL be different than those above!

As you can see above, `.hash` can be called on any object. It also returns the same number if called on the same object twice. `"This is a string".hash` will continue to return `=> -1954425285861713910` for the entirety of the session. If you restart your session, your .hash values will change. The new hash value I got for the "This is a string" once I restarted my irb session can be seen below:

```ruby
"This is a string".hash
=> 3548872752519183882
```

With the power of the `.hash` method, can you start to see how we might use arrays to create our hash? Take a minute to think through it.
