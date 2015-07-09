# E-Commerce Currency Meta Document

## Summary
The purpose of this specification is to provide a common interface to currencies as defined in ISO-4217. This would allow e-commerce solutions to easily change one currency provider for another.

## Why Bother?
The notion of differing currencies is essential for e-commerce solutions that operate online and are therefore available for an international audience.

Without a common interface, that allows sharing, each e-commerce solution has to provide such data itself and must not only keep up with changing currencies, but also with un-official currencies.   

The data is essentially always the same. Parsed from a few trusted sources like the xml-file provided by ISO-4217 or the *Common Locale Data Repository* (CLDR).

## Scope
### Goals
 - Model all fields defined in ISO-4217
 - Make it possible to swap currency packages
### Non-Goals
 - Exchange rates
## Design Decisions

### Why not include exchange rates?
Providing currency data and exchange rates are two very different goals. Exchange rates define the value of one currency with regard to another. An exchange rate of 1.1 USD does not make sense without at least a second currency.

Also currencies change rarely. Exchange rates however change constantly. 

## Links

- [Currency Codes ISO-4217](http://www.iso.org/iso/home/standards/currency_codes.htm)
- [Common Locale Data Repository (CLDR)](http://cldr.unicode.org/)