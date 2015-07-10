#Currency Interfaces

This document describes common interfaces for currencies and retrieving currencies as described in [ISO-4217](http://www.iso.org/iso/home/standards/currency_codes.htm).

In addition to ISO-4217 a currency also defines its symbol. A currency therefore consists of

 - a name
 - an alphabetic code
 - a numeric code
 - minor units
 - a symbol

## Specification

### Currency

```php
<?php

namespace Pesr\Currency;

/**
 * Defines the methods a currency must have.
 * 
 * A currency is the unit of a price or money. It gives context to
 * the value of a price or money and together they define worth.
 * 
 * @see http://www.iso.org/iso/home/standards/country_codes.htm
 * @see http://www.iso.org/iso/home/standards/currency_codes.htm
 */
interface Currency
{	
	/**
	 * Returns the three letter code for the currency.
	 * 
	 * The three letter code is based of ISO 3166, which defines
	 * two letter codes for country names. The third letter is the 
	 * first letter of the currencies name.
	 *
	 * **Examples**
	 * 
	 *     USD - United States (US) Dollar (D)
	 *     CHF - Swiss (CH) Francs (F)
	 * 
	 *
	 * @return string
	 */
	public function getAlphabeticCode();

	/**
	 * A three-digit number to identify the currency.
	 * 
	 * If possible the number is identical to the three-digit country 
	 * code defined in ISO-3166-1.   
	 *
	 * @return integer
	 */
	public function getNumericCode();

	 /**
	 * Returns a list of ISO-3166-Alpha-3 country codes.
	 * 
	 * The list contains the ISO-codes of those countries, that
	 * use the currency in circulation.
	 *
	 * @return string[]
	 */
	public function getCountries();
    
	/**
	 * This integer indicates how many digits may follow the
	 * decimal point.
	 *
	 * The number of minor units can be used to format prices
	 * correctly.
	 * 
	 * **Example**
	 * 
	 *     The USD has 2 minor units. This means that two 
	 *     digit can stand on the right of the decimal point.
	 *     Or in other words that the USD is divisable by 
	 *     100 (10^2).
	 *     
	 *        10.02
	 *        23.40
	 *        4.47 
	 *     
	 *     The Viet Name Dong (VND) has 0 minor units. It should
	 *     not be displayed with a decimal point and following
	 *     digits.
	 *     
	 *        107
	 *        2340
	 *        563      
	 *
	 * @return integer
	 */
	public function getMinorUnits()

	/**
	 * The name of the currency in English.
	 * 
	 * **Example**
	 * 
	 *       US Dollar
	 *       Canadian Dollar
	 *       Australian Dollar 
	 * 
	 * @return string
	 */
	public function getName();

	/**
	 * The symbol which can be used when displaying prices.
	 *
	 * If a currency does not have a symbol, the alphabetic code
	 * should be returned and used.
	 * 
	 * Please note, currency symbols are not necessarily unique.
	 * The alphabetic code may be used instead, if the meaning of 
	 * the symbol is unclear. 
	 *
	 * @return string
	 */
	public function getSymbol();
}
```

```php
<?php

namespace Pesr\Currency;

/**
 * Defines how Currencies can be retrieved, while hiding the exact retrieval scheme.
 * 
 * @see http://www.iso.org/iso/home/standards/country_codes.htm
 * @see http://www.iso.org/iso/home/standards/currency_codes.htm
 */
interface CurrencyRepository
{	
	/**
	 * Returns the currency identified by the given alphabetic code.
	 *  
	 * This method MUST always return a currency. It MUST NOT return 
	 * anything else (like null or false).
	 * 
	 * @return Currency
	 * 
	 * @throws Psr\Ecommerce\Currency\InvalidCurrencyException If no currency with the given code exists
	 */
	public function retrieveByAlphabeticCode( $code );

	/**
	 * Returns the currency identified by the given numeric code.
	 *  
	 * This method MUST always return a currency. It MUST NOT return 
	 * anything else (liek null or false).
	 * 
	 * @return Currency
	 * 
	 * @throws Psr\Ecommerce\Currency\InvalidCurrencyException If no currency with the given code exists
	 */
	public function retrieveByNumericCode( $code );
	
	/**
	 * Returns all currencies distributed in a country.
	 * 
	 * The country is identified by its iso-3166-alpha-3 code.
	 *  
	 * This method MUST always return an array. If no currency is found an
	 * empty array MUST be returned.
	 * 
	 * @return Currency[]
	 */
	public function retrieveByCountryCode( $code );
	
	/**
	 * Returns all currencies in the repository.
	 *  
	 * This method MUST always return an array. If the repository has no
	 * currencies an empty array MUST be returned.
	 * 
	 * @return Currency[]
	 */
	public function retrieveAll( $code );
}
```
```php
<?php

namespace Pesr\Currency;

/**
 * Exception interface for invalid currency arguments.
 *
 * Any time a currency is retrieved with an invalid code, the method
 * MUST throw an exception class which implements Pesr\Currency\InvalidCurrencyException
 */
interface InvalidCurrencyException {}
```
