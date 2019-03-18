# Sample Codes

Following is sample minimal initiate-payment and submit-payment direct API.

```php
<?php

// Integeration configuration

// pipwave-provided API key
$pw_api_key = '';
// pipwave-provided API secret
$pw_api_secret = '';
// Unique transaction ID
$txn_id = 'REF001';
// Transaction amount
$amt = '1';
// Transaction currency
$curr_code = 'MYR';
// Unique buyer ID
$buyer_id = 'USER001';
// Buyer's email address
$buyer_email = 'email@domain.com';
$pm = null;
// Payment method to use (if direct-api is employed)
//$pm = 'paypal.ec';

// Sample code

class pipwave_integration {

    function generate_pw_signature($signatureParam) {
        ksort($signatureParam);
        $signature = "";
        foreach ($signatureParam as $key => $value) {
            $signature .= $key . ':' . $value;
        }
        return sha1($signature);
    }

    function send_request_to_pw($data, $pw_api_key) {
        $agent = "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0)";
        $ch = curl_init();
        curl_setopt($ch, CURLOPT_HTTPHEADER, array('x-api-key:' . $pw_api_key));
        curl_setopt($ch, CURLOPT_POST, 1);
        curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($data));
        curl_setopt($ch, CURLOPT_URL, 'https://api.pipwave.com/payment');
        curl_setopt($ch, CURLOPT_VERBOSE, 1);
        curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, 2);
        curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, FALSE);
        curl_setopt($ch, CURLOPT_TIMEOUT, 120);
        curl_setopt($ch, CURLOPT_USERAGENT, $agent);
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
        $response = curl_exec($ch);
        if ($response == false) {
            echo "<pre>";
            echo 'CURL ERROR: ' . curl_errno($ch) . '::' . curl_error($ch);
            die;
        }
        curl_close($ch);
        return json_decode($response, true);
    }

}

$pw = new pipwave_integration();

// Minimal data required for initiate-payment to work
$data = array(
    'action' => 'initiate-payment',
    'timestamp' => time(),
    'api_key' => $pw_api_key,
    'txn_id' => $txn_id,
    'amount' => $amt,
    'currency_code' => $curr_code,
    'buyer_info' => array(
        'id' => $buyer_id,
        'email' => $buyer_email,
    ),
);
$signatureParam = array(
    'api_key' => $pw_api_key,
    'api_secret' => $pw_api_secret,
    'txn_id' => $data['txn_id'],
    'amount' => $data['amount'],
    'currency_code' => $data['currency_code'],
    'action' => $data['action'],
    'timestamp' => $data['timestamp']
);

$data['signature'] = $pw->generate_pw_signature($signatureParam);
$response = $pw->send_request_to_pw($data, $pw_api_key);
$token = $response['token'];

// Render pwsdk with the token, or direct-api with pipwave's submit-payment API
$method = 'direct';
$method = 'hpp'; //Uncomment this to test hpp
$method = 'sdk'; //Uncomment this to test sdk

if ($method == 'direct' && !empty($pm)) {
    // Minimal data required for submit-payment to work
    $data = array(
        'action' => 'submit-payment',
        'timestamp' => time(),
        'api_key' => $pw_api_key,
        'token' => $token,
        'payment_method_code' => $pm,
    );
    // must redirect buyer to URL provided by pipwave for next payment step
    $response = $pw->send_request_to_pw($data, $pw_api_key);
    header('Location: ' . $response ['redirect_url']);
    exit;
} else if ($method != 'sdk') {
    //Method 2: Redirect to pipwave HPP
    header('Location: ' . $response ['redirect_url']);
    exit;
}

//Method 3: sdk
?>
<html>
<head></head>
<body>
<div id="pwloading" class="text-center">
    Loading...
</div>
<div id="pwscript"></div>
<div id="pwarea" class="row-fluid clearfix"></div>
<script>
    var pwconfig = {"api_key":"<?php echo $pw_api_key; ?>","token":"<?php echo $token; ?>","debug":false,"caller_version":"pipwave HPP v1.0"};
    (function (_, p, w, s, d, k) {
        var a = _.createElement("script");
                a.setAttribute('src', w + d);
        a.setAttribute('id', k);
        setTimeout(function() {
            var reqPwInit = (typeof reqPipwave != 'undefined');
            if (reqPwInit) {
                reqPipwave.require(['pw'], function(pw) {
                    pw.setOpt(pwconfig);
                    pw.startLoad();
                });
            } else {
                _.getElementById(k).parentNode.replaceChild(a, _.getElementById(k));
            }
        }, 800);
    })(document, 'script', "//secure.pipwave.com/sdk/", "pw.sdk.min.js", "pw.sdk.min.js", "pwscript");
</script>
</body>
</html>
```

