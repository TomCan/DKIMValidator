# PHP DKIM Validator

A straightforward validation class for checking DKIM signatures and header settings. Requires PHP 7.2 or later.

## Installation

```
composer require tomcan/dkimvalidator
```

## Usage

```php
use TomCan\DKIMValidator\Validator;
use TomCan\DKIMValidator\DKIMException;
require 'vendor/autoload.php';
//Put a whole raw email message in here
//Load the message directly from disk -
//don't copy & paste it as that will likely affect line breaks & charsets
$message  = file_get_contents('message.eml');
$dkimValidator = new Validator($message);
try {
    if ($dkimValidator->validateBoolean()) {
        echo "Cool, it's valid";
    } else {
        echo 'Uh oh, dodgy email!';
    }
} catch (DKIMException $e) {
    echo $e->getMessage();
}
```

# Changelog

* Original package [angrychimp/php-dkim](https://github.com/angrychimp/php-dkim);
* Forked by [teon/dkimvalidator](https://github.com/teonsystems/php-dkim).
* Forked into [phpmailer/dkimvalidator](https://github.com/PHPMailer/DKIMValidator) by Marcus Bointon (Synchro) in October 2019:
  * Restructuring
  * Cleanup for PSR-12 and PHP 7.2
  * Various bug fixes and new features.
* Forked into [tomcan/dkimvalidator](https://github.com/PHPMailer/DKIMValidator) by Tom Cannaerts (TomCan) in Januari 2025:
  * Return more details in the result
