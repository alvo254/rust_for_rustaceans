Rust allows the owner of a value to lend out that value to others, without
giving up ownership, through references.
References are pointers that come
with an additional contract for how they can be used, such as whether the
reference provides exclusive access to the referenced value, or whether the
referenced value may also have other references point to it.

**shard refernces

A shared reference, &T , is, as the name implies, a pointer that may be
shared. Any number of other references may exist to the same value, and
each shared reference is Copy , so you can trivially make more of them.
Values behind shared references are not mutable; you cannot modify or
reassign the value a shared reference points to, nor can you cast a shared
reference to a mutable one.
The Rust compiler is allowed to assume that the value a shared refer-
ence points to will not change while that reference lives. For example, if the
Rust compiler sees that the value behind a shared reference is read multiple
times in a function, it is within its rights to read it only once and reuse that
value.