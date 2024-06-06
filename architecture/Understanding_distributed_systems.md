# Understanding_distributed_systems by Roberto Vitillo

##### Chapter 1 - Intro

“A distributed system is one in which the failure of a computer you didn’t even know existed can render your own
computer unusable.”

In software development, a leaky abstraction is an abstraction that leaks details that it is supposed to abstract
away.

##### Chapter 2 - Reliable links

* TCP: Reliable Data Delivery
    * Breaks data into numbered segments.
    * Receiver checks for missing or out-of-order segments.
    * Segments require acknowledgement, otherwise they're resent.
    * Checksums ensure data arrives without corruption.