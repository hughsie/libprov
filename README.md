# libprov - a small library of helpers for OpenSSL 3 providers

Currently available routines:

-   ERR helpers

    OpenSSL's ERR functions do not lend themselves very well to
    provider's own error tables, because they can't pass the
    provider's handle to the error record building routines.
    This is due to certain limitations with the base C standard
    requirements for OpenSSL itself (C90).
    
    These helpers are replacements of OpenSSL's ERR_raise() and
    ERR_raise_data() that take better advantage of more modern C
    standards.  C99 required.

    See the comments in include/prov/err.h for more information.

-   NUM helper

    Converting OSSL_PARAM numbers to native numbers present a bit of a
    challenge, as they are variable length, and may need some adaption
    to fit into native numbers.
    
    provnum_get() and provnum_set() claim to be universally applicable
    functions for converting an OSSL_PARAM number to a native integer
    or 
