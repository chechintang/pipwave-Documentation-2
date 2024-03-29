# Signature

Signature generation is dependant on the APIs being called. Some API do not require signature, while others require. Note the “Signature” section for each API for the list of data required to be included for signature generation.

For those API which require signature, signature can be generated by following PHP example:

```text
function generateSignature($array) {
    $s = "";
    foreach($array as $key => $value) {
        $s .= $key . ':' . $value;
    }
    return sha1($s);
}
```

Put the resulting string in “signature” parameter when making the API request.

