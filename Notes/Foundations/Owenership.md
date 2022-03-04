Rust’s memory model centers on the idea that all values have a single
owner—that is, exactly one location (usually a scope) is responsible for
ultimately deallocating each value.
This is enforced through the borrow
checker. If the value is moved, such as by assigning it to a new variable,
pushing it to a vector, or placing it on the heap, the ownership of the value
moves from the old location to the new one.
To see why, consider what would happen if a type like Box were Copy .
If we executed box2 = box1 , then box1 and box2 would both believe that
they owned the heap memory allocated for the box, and they would both
attempt to free it when they went out of scope. Freeing the memory twice
could have catastrophic consequences.