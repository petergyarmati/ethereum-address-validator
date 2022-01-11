Ethereum Address Validator
--
(c) by Andrzej Budzanowski <kontakt@andrzej.budzanowski.pl>

## License
MPL-2.0

## Brief
Class that verifies if [Ethereum](https://www.ethereum.org/) or BSC address is properly formatted and - optionaly - properly checksummed according to [EIP-55](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-55.md).

## Installation
Use composer:

```bash
composer require mrgyarmati/ethereum-address-validator
```

## Usage
```php
<?php
    use \PsychoB\Ethereum\AddressValidator;
    
    // Addresses that have good format and checksum are considered valid
    AddressValidator::isValid('0xA477941c7AAD6536f175ef123bf9eeD6F82A4c85') === AddressValidator::ADDRESS_VALID;
    
    // Also addresses that are all uppercase or all lowercase are considered valid (no checksum check performed)
    AddressValidator::isValid('0xA477941C7AAD6536F175EF123BF9EED6F82A4C85') === AddressValidator::ADDRESS_VALID;
    AddressValidator::isValid('0xa477941c7aad6536f175ef123bf9eed6f82a4c85') === AddressValidator::ADDRESS_VALID;
    
    // Addresses that have good format but incorrect checksum
    AddressValidator::isValid('0xA477941c7aaD6536f175ef123bf9eeD6F82A4c85') === AddressValidator::ADDRESS_CHECKSUM_INVALID;
    
    // Address without proper format return
    AddressValidator::isValid('invalid address') === AddressValidator::ADDRESS_INVALID;
    
    // To get canonical (properly checksummed) addres, use:
    AddressValidator::getCanonicalAddress('0xA477941C7AAD6536F175EF123BF9EED6F82A4C85') === '0xA477941c7AAD6536f175ef123bf9eeD6F82A4c85'
```
