# Hashes

Hashes are a data structure that gives O(1) lookup times for any item that has been intserted if you have an associated key. They have no structure, meaning that a key/value pair that has been added to a hash does not know what other items it is close to. Hashes use arrays and a function called the `hash` function to work behind the scenes, and the easiest way to explain what's really happening is to code it out, so let's build our own hash class in Ruby.



