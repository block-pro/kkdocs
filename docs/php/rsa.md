# php rsa demo

## install php

```bash
sudo apt install php
```

## install composor

* <https://getcomposer.org/>

```bash
sudo curl -s https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/composer
```

## install phpseclib

* <https://github.com/phpseclib/phpseclib>

```bash
composer require phpseclib/phpseclib:~2.0
```

## rsa demo

```php
<?php
require __DIR__ . '/vendor/autoload.php';

use phpseclib\Crypt\RSA;

$plaintext = 'abcdTest';
$outPriKey = "MIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQDAAbXA7tnnMuWV6WO1bKEKGyKZRFcRCGDW+UfGFZdx0MEm6+fKTNGTsalEFwFPK36YtQFXcN0FciGmQp1wGts4IqLaEzk9az5UcxIfR00JxpNsTYSZb82ZMpj52WF0FHtyj7qE+K3k/FcKCcEHQ3Soa9LL/GQpyVO0yhxeV5tiRfnHoJxxCRHp3jM//VnlCd6koTwPNPFKsf8Vf+dtGA3/BZPFoHvFP0+vfLmEi2TIHO1f1CZDg67TiC/Kkusl0XBiUAXhjAz1SleNQzKHtUVPbVluBtG8ydk8kcLpqDDST6WPnHg5NgHt9qXp0vOLO7ABkQz+dGCXKm+tWXHnRjj1AgMBAAECggEAMm7AjMKwHZgy0aOR+w9jZUInXlai/+hRd2XWwmLdepm4gj6ojWyMB908dpQMVf04rWetyIfupgWKbR9GNzH2rtH6MImoGUfYAVqQQgL6azzrcCEUWTESsdCmecntXQ4cNsUl2tNu6ZyWSB6zwvKm664Wmlna/VbSU8RamzUrrS362gxNFdcEyvCstlnNx1aC5VCRFHm6uBO2uFSYR4dh4e0KpEmYsPT41k93Z4KQHFTCwcvuQu+or5WKL44hKYHyXoZbWiZhfvBRXBVDT7TLmObkeQXAr/Uu1SO5AkblYqG0dyYVy1ea2xANjt8Mw+OP4kRu8IFikALwWp4iYdyAaQKBgQD5mrsx6KrRHbtpBZzHBcEL+/tttA8YAskH2NlkEcGDPcwwULdEYRUUEvX5J+9sTwZHLnE6O9YKI0UtbEBLmDGDfoHy9OM0NCHEaxmZJvmizzfGGc4u/+EtrNCZh1nXUvz1cPip6tywpuHuIgcdAczm0kD9vMWcKHWJSZv+gdClpwKBgQDE7StEIc/c4/fYjIzUaMh6NHqGGB/SpqpfyKHdNZG1xhacN3zY44fO4X8U93uV+thhY3a66TjvvfC2kQAidWWwn4DzmOgWCSPPtuYuI5vouqW/HL8rLKf3hV2rGCC6fz9PDgjy1tl6ZxI10YsA0VjWuHQ9OcQjBl/ypoGfTCJ4AwKBgQCvMhwSe+zpuqTAol/YkgFeGA/ygF/XypywFVUBGDVrmQSpJP590GarIGPl7lHvA8i0TbTL2xPxKbB0oXa/mKOoWDN+BMU07yKEa2gcR28RB8FuGs7NzmyPUq1YFdjJekZzQEhJe8BLfdc2/ktf4NOhcBKOBuHtKbjWFASaLyP0IQKBgHjRSYozdGQBOT4SfRSUdOsE52b9xghnWIALh8M/6nWrYpPVNzOZ5Oh4UI98hsYtcDPP4jgqflQYJGbd70c0337NXUAWv81FLkNx4ybLkgvm92mZKXBDpYmmuSEPXIUPLLhD1Bmo1yTRt8ptFOsbhXW3FRm7JyqV7qfgoAYrn7ohAoGAT2YHHABe8UHfo8ZnLKjjC3FfUcrGd87LTB8EbADVb+Vuak7/8/FTGRDGxygeH3/haB86Dv1nRQJ2Jp1fS9HrWfX/cart1H6Ef/FKT6Td3aCZAwM6kTLWkDepX+2qWW3pnKytrnp1rHFu9XIR+iFlG2hFOg+ppzUKfX3L3A57xDU=";
$tnPubKey = "MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAwAG1wO7Z5zLlleljtWyhChsimURXEQhg1vlHxhWXcdDBJuvnykzRk7GpRBcBTyt+mLUBV3DdBXIhpkKdcBrbOCKi2hM5PWs+VHMSH0dNCcaTbE2EmW/NmTKY+dlhdBR7co+6hPit5PxXCgnBB0N0qGvSy/xkKclTtMocXlebYkX5x6CccQkR6d4zP/1Z5QnepKE8DzTxSrH/FX/nbRgN/wWTxaB7xT9Pr3y5hItkyBztX9QmQ4Ou04gvypLrJdFwYlAF4YwM9UpXjUMyh7VFT21ZbgbRvMnZPJHC6agw0k+lj5x4OTYB7fal6dLzizuwAZEM/nRglypvrVlx50Y49QIDAQAB";



echo '原始字符串:' . $plaintext . "\n";

$rsa = new RSA();
$rsa->loadKey($outPriKey); //privatekey

//sign with private key

$rsa->setSignatureMode(RSA::SIGNATURE_PKCS1);
$rsa->setHash('sha256');
$signature = $rsa->sign($plaintext);
$hex_signature = bin2hex($signature);
echo '签名后:' . $hex_signature . "\n";

//verify with public key 
$rsa->loadKey($tnPubKey); // public key
$bin_signature = hex2bin($hex_signature);
$verified = $rsa->verify($plaintext, $bin_signature);
echo '验签结果is verified:' . $verified . "\n";

//encrypt by pub key
$rsa->loadKey($tnPubKey); // public key
$rsa->setEncryptionMode(RSA::ENCRYPTION_PKCS1); //注意设置,否则java会nopadding exection
$ciphertext = $rsa->encrypt($plaintext);
$hex_ciphertext = bin2hex($ciphertext);
echo '加密结果:' . $hex_ciphertext . "\n";

//decrypt by private key
$rsa->loadkey($outPriKey);
$dec_text = $rsa->decrypt(hex2bin($hex_ciphertext));
echo '解密结果:' . $dec_text . "\n";
?>
```
