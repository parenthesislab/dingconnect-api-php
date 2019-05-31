# Parenthesis\DingConnect\V1Api

All URIs are relative to *https://api.dingconnect.com*

Method | HTTP request | Description
------------- | ------------- | -------------
[**cancelTransfers**](V1Api.md#cancelTransfers) | **POST** /api/V1/CancelTransfers | Attempt to cancel transfers with the submitted TransferIds
[**estimatePrices**](V1Api.md#estimatePrices) | **POST** /api/V1/EstimatePrices | Estimate prices for send or receive values
[**getAccountLookup**](V1Api.md#getAccountLookup) | **GET** /api/V1/GetAccountLookup | Get providers and product information for a specific account number
[**getBalance**](V1Api.md#getBalance) | **GET** /api/V1/GetBalance | Get the current agent balance
[**getCountries**](V1Api.md#getCountries) | **GET** /api/V1/GetCountries | Get a list of supported countries
[**getCurrencies**](V1Api.md#getCurrencies) | **GET** /api/V1/GetCurrencies | Get a list of supported currencies
[**getErrorCodeDescriptions**](V1Api.md#getErrorCodeDescriptions) | **GET** /api/V1/GetErrorCodeDescriptions | Get a list of error code descriptions
[**getProductDescriptions**](V1Api.md#getProductDescriptions) | **GET** /api/V1/GetProductDescriptions | Get localized strings for products
[**getProducts**](V1Api.md#getProducts) | **GET** /api/V1/GetProducts | Get a list of products that can be used in SendTransfer
[**getPromotionDescriptions**](V1Api.md#getPromotionDescriptions) | **GET** /api/V1/GetPromotionDescriptions | Get localized strings for promotions
[**getPromotions**](V1Api.md#getPromotions) | **GET** /api/V1/GetPromotions | Get a list of promotions
[**getProviderStatus**](V1Api.md#getProviderStatus) | **GET** /api/V1/GetProviderStatus | Get the current status of product providers
[**getProviders**](V1Api.md#getProviders) | **GET** /api/V1/GetProviders | Get a list of product providers available to the agent
[**getRegions**](V1Api.md#getRegions) | **GET** /api/V1/GetRegions | Get a list of regions on the system
[**listTransferRecords**](V1Api.md#listTransferRecords) | **POST** /api/V1/ListTransferRecords | Query transfers that were submitted to the system
[**sendTransfer**](V1Api.md#sendTransfer) | **POST** /api/V1/SendTransfer | Send a transfer to an account


# **cancelTransfers**
> \Parenthesis\DingConnect\Model\CancelTransfersResponse cancelTransfers($cancellation_requests)

Attempt to cancel transfers with the submitted TransferIds

The agent should call `ListTransferRecords` with an appropriate query to   get a list of `TransferIds` that are available to cancel.    Not all transfers can be cancelled. This method will return the `ProcessingState` of the transfer: if the  state is \"Cancelled\", then the transfer was successfully cancelled and any appropriate balance compensations  will have been applied to the agent account. If the state is anything else, then the transfer could not be  cancelled.    Please see the documentation section on [batching](#batching).

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Parenthesis\DingConnect\Api\V1Api(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$cancellation_requests = array(new \Parenthesis\DingConnect\Model\CancellationRequest()); // \Parenthesis\DingConnect\Model\CancellationRequest[] | An explicit list of records to cancel.

try {
    $result = $apiInstance->cancelTransfers($cancellation_requests);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling V1Api->cancelTransfers: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **cancellation_requests** | [**\Parenthesis\DingConnect\Model\CancellationRequest[]**](../Model/CancellationRequest.md)| An explicit list of records to cancel. |

### Return type

[**\Parenthesis\DingConnect\Model\CancelTransfersResponse**](../Model/CancelTransfersResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json, text/json, application/x-www-form-urlencoded
 - **Accept**: application/json, text/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **estimatePrices**
> \Parenthesis\DingConnect\Model\EstimatePricesResponse estimatePrices($requested_estimations)

Estimate prices for send or receive values

Before a transfer is attempted, it is impossible to know the exact value that an account will receive due to fluctuating foreign exchange rates, provider promotions and fees.  This API call will attempt to estimate, from the current prices in the products list, what receive value will result from a given send value or vice versa.    Please see the documentation section on [batching](#batching).    ### Input parameters  In each input, `SendValue` and `ReceiveValue` cannot both be non-zero.    If `ReceiveValue` is non-zero we will attempt to estimate the price that the customer would need to *send* (in the agent currency) in order to receive the given `ReceiveValue`.    If `SendValue` is non-zero (and `SendCurrencyIso` is null or empty) we will attempt to estimate what the customer would *receive* for the given `SendValue` (and send value would be interpreted as a value expressed in the agent currency).    If `SendValue` is non-zero and `SendCurrencyIso` is specified, we will attempt to estimate what the customer would *receive* for the given `SendValue/SendCurrencyIso`.  The agent  should contact Ding if he/she wishes to send in currencies other than the main currency of his/her account.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Parenthesis\DingConnect\Api\V1Api(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$requested_estimations = array(new \Parenthesis\DingConnect\Model\EstimationRequest()); // \Parenthesis\DingConnect\Model\EstimationRequest[] | 

try {
    $result = $apiInstance->estimatePrices($requested_estimations);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling V1Api->estimatePrices: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **requested_estimations** | [**\Parenthesis\DingConnect\Model\EstimationRequest[]**](../Model/EstimationRequest.md)|  |

### Return type

[**\Parenthesis\DingConnect\Model\EstimatePricesResponse**](../Model/EstimatePricesResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json, text/json, application/x-www-form-urlencoded
 - **Accept**: application/json, text/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getAccountLookup**
> \Parenthesis\DingConnect\Model\GetAccountLookupResponse getAccountLookup($account_number)

Get providers and product information for a specific account number

Returns country, provider and region code details for the account number.  This information can be then be used as input parameters  to `GetProducts`.    Please note, while `GetProducts` (and `GetProviders`) can also accept an `AccountNumber`, their behaviour when the system cannot match  the account number to a subset of products or providers is to return the entire list.  This could be a problem for consuming  systems if the entire list of products or providers is very large.    `GetAccountLookup` behaves differently - if no matching provider/region information can be found, it will return an empty list.     In most cases it will return a single entry, but it is possible to return mulitple items.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Parenthesis\DingConnect\Api\V1Api(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$account_number = "account_number_example"; // string | For phone number based products, the account number should be in international phone number format.

try {
    $result = $apiInstance->getAccountLookup($account_number);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling V1Api->getAccountLookup: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **account_number** | **string**| For phone number based products, the account number should be in international phone number format. | [optional]

### Return type

[**\Parenthesis\DingConnect\Model\GetAccountLookupResponse**](../Model/GetAccountLookupResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, text/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getBalance**
> \Parenthesis\DingConnect\Model\GetBalanceResponse getBalance()

Get the current agent balance

Returns the current agent balance. This will include any commission-on-sale increments, but will not reflect any  transfers that are currently processing.     For Instant transfers, the balance is decremented after a successful interaction with the product provider.  For Batch transfers, the balance is decremented immediately, and will be refunded later in case of failure.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Parenthesis\DingConnect\Api\V1Api(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);

try {
    $result = $apiInstance->getBalance();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling V1Api->getBalance: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters
This endpoint does not need any parameter.

### Return type

[**\Parenthesis\DingConnect\Model\GetBalanceResponse**](../Model/GetBalanceResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, text/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getCountries**
> \Parenthesis\DingConnect\Model\GetCountriesResponse getCountries()

Get a list of supported countries

Retrieves a list of standard two letter country codes that the system supports, along with the country name in English.    Please see the documentation section on [reference data](#reference-data).    We use <a href=\"https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2\" target=\"_blank\">ISO 3166-1 alpha-2</a> for our country codes, with the exception of XG used for products that are available for all countries.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Parenthesis\DingConnect\Api\V1Api(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);

try {
    $result = $apiInstance->getCountries();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling V1Api->getCountries: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters
This endpoint does not need any parameter.

### Return type

[**\Parenthesis\DingConnect\Model\GetCountriesResponse**](../Model/GetCountriesResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, text/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getCurrencies**
> \Parenthesis\DingConnect\Model\GetCurrenciesResponse getCurrencies()

Get a list of supported currencies

Retrieves a list of standard three letter currency codes that the system supports, along with the currency name in English.    Please see the documentation section on [reference data](#reference-data).    We use <a href=\"https://en.wikipedia.org/wiki/ISO_4217\" target=\"_blank\">ISO 4217</a> for our currency codes.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Parenthesis\DingConnect\Api\V1Api(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);

try {
    $result = $apiInstance->getCurrencies();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling V1Api->getCurrencies: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters
This endpoint does not need any parameter.

### Return type

[**\Parenthesis\DingConnect\Model\GetCurrenciesResponse**](../Model/GetCurrenciesResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, text/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getErrorCodeDescriptions**
> \Parenthesis\DingConnect\Model\GetErrorCodeDescriptionsResponse getErrorCodeDescriptions()

Get a list of error code descriptions

Every API response can contain one or more ErrorCodes that indicate why a request failed. This API can be used to   get a list of human readable errors that correspond to those ErrorCodes. These error messages are aimed at the  agent and are not suitable for display to the end user/customer.    Note that we will not remove ErrorCodes, but we reserve the right to add new ones.    Please see the documentation section on [responses](#responses).

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Parenthesis\DingConnect\Api\V1Api(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);

try {
    $result = $apiInstance->getErrorCodeDescriptions();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling V1Api->getErrorCodeDescriptions: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters
This endpoint does not need any parameter.

### Return type

[**\Parenthesis\DingConnect\Model\GetErrorCodeDescriptionsResponse**](../Model/GetErrorCodeDescriptionsResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, text/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getProductDescriptions**
> \Parenthesis\DingConnect\Model\GetProductDescriptionsResponse getProductDescriptions($language_codes, $sku_codes)

Get localized strings for products

Please see the documentation section on [localization](#localization).    Please see the documentation section on [querying](#querying).

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Parenthesis\DingConnect\Api\V1Api(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$language_codes = array("language_codes_example"); // string[] | Filter the list to product descriptions with the submitted language codes.
$sku_codes = array("sku_codes_example"); // string[] | Filter the list to descriptions for products with the submitted SkuCodes.

try {
    $result = $apiInstance->getProductDescriptions($language_codes, $sku_codes);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling V1Api->getProductDescriptions: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **language_codes** | [**string[]**](../Model/string.md)| Filter the list to product descriptions with the submitted language codes. | [optional]
 **sku_codes** | [**string[]**](../Model/string.md)| Filter the list to descriptions for products with the submitted SkuCodes. | [optional]

### Return type

[**\Parenthesis\DingConnect\Model\GetProductDescriptionsResponse**](../Model/GetProductDescriptionsResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, text/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getProducts**
> \Parenthesis\DingConnect\Model\GetProductsResponse getProducts($country_isos, $provider_codes, $sku_codes, $benefits, $region_codes, $account_number)

Get a list of products that can be used in SendTransfer

This API returns a list of available products that satisfy request criteria.    Please see the documentation section on [querying](#querying).    #### Localization  Products have localized descriptions and you should call `GetProductDescriptions` to get the appropriate  localizations.  See the section on [Localization](#localization) above.    #### Setting Definitions  Some providers require additional information to be submitted with transfer requests in the form of name-value  settings where the `Name` of the setting is defined by the provider and the `Value` is submitted with the request.    If a provider does require this, `SettingDefinitions` will be populated with the definition of those settings. The  `Name` of each definition is used in transfer requests, and the Description will contain a hint as to what the  `Value`s should contain.      The `Name` must be used verbatim (including casing and any special characters) in the SendTransfer request.    The `Description` is unformatted and non-localized so is not appropriate for any customer facing UI elements.  This field is informational and targeted at the API agent/integrator.    #### Commission Rate  The rate of commission that will be applied for selling this product (if applicable).    #### Processing Mode  Products can be processed in real-time (`ProcessingMode=Instant`), or some time in the future (`ProcessingMode=Batch`).    * **Instant:** We will attempt to process the transfer immediately. The response from `SendTransfer` will   contain a transfer record whose `ProcessingState` is one of `Completed` or `Failed`.  * **Batch:** We will process the transfer later. The response from `SendTransfer` will contain a transfer   record with a `ProcessingState` of `Submitted`. The agent should use `ListTransferRecords` to periodically   check the status of the transfer.    #### Redemption Mechanism  Some products require further intervention from the end-user or agent before their benefit is realized.  For example, the user may  need to dial a number and enter a PIN that was returned in the receipt or the agent may need to complete other steps before the   product can be sold.      This property can contain the following values:    * **Immediate:** The transfer requires no further action from the customer, and will be received immediately.    * **ReadReceipt:** Further instructions for how to complete the transfer will be printed within the `ReceiptText` property and the end user should  follow those instructions. For example: PIN based products, or Long Distance Minutes.    * **ReadAdditionalInformation:** Further instructions for how to complete or use the transfer are in the `AdditionalInformation` property of the Product  and the agent will need to code their application to follow those instructions.  For example, a user may be required to submit their account number  against one product (to \"register\" their phone number) before they may use other products    #### Benefits  Each product can convey a number of benefits on an account number, including account top up, data, bundles, sms, long distance credit, and so forth.    Current benefits include the following:     *  Mobile  *  Minutes  *  Data  *  LongDistance  *  Electricity  *  TV  *  Internet  *  Utility  *  Balance    The benefit list will be extended in time. To make your system robust, we recommend you implement your integration so that it can handle any benefit type.    Alternatively, you could routinely filter the product list to a list of benefits supported by your application.    #### Validity Period  Some transfers must be redeemed within a certain time-window by the user after purchase. `ValidityPeriodIso` communicates how long the user will  have to complete the transaction. For example, many PIN based products must be redeemed before the validity period elapses.     We use the ISO8601 duration format. For example, `P30D` is 30 days.    #### UAT Number  Transfers submitted using this number will be in test mode only. No balance will be deducted, but no  provider transaction will actually be performed.      #### Additional Information   From time to time we will try to offer completely new or non-standard products to existing agents that  can only be redeemed using non-standard mechanisms/procedures. We will use this field to communicate any  information that we think will help the agent integrate.     This field is unformatted, not localized and unsuitable for end-user display.    ### Price Properties  #### Agent and Customer Fees  The `CustomerFee` is the amount (in the agent currency) that the agent has asked us to collect from the customer. We will subtract this from the `SendValue` before passing to the provider.     The `DistributorFee` is the amount (in agent currency) that Ding charges the agent to fulfil the transfer.  We will deduct this amount from the agent balance in addition to the `SendValue`.      For example, if  - SendValue = 10  - CustomerFee = 1  - DistributorFee = 2  Then  - SendValue - CustomerFee (= 9) will be passed to the Provider, and   - SendValue + DistributorFee (= 12) will be deducted from the agent balance    #### Tax Calculation  Countries around the world have different ways of quoting Tax values.  `TaxCalculation` indicates how you should interpret the values in the other Tax fields.     Possible values are:  * Inclusive  * Exclusive    Please see <a href=\"https://en.wikipedia.org/wiki/Tax_rate#Inclusive_and_exclusive\" target=\"_blank\">Tax Rates on Wikipedia</a> for an explanation of the values.    If the `TaxCalculation` field is left blank, then tax is handled by the provider.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Parenthesis\DingConnect\Api\V1Api(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$country_isos = array("country_isos_example"); // string[] | Filter the list to products for countries with the given ISOs.
$provider_codes = array("provider_codes_example"); // string[] | Filter the list to products supplied by providers with the submitted provider codes.
$sku_codes = array("sku_codes_example"); // string[] | Filter the list to products with the submitted SkuCodes.
$benefits = array("benefits_example"); // string[] | Filter the list to products with the listed benefits.
$region_codes = array("region_codes_example"); // string[] | Filter the list to products in regions with the submitted regionCodes.
$account_number = "account_number_example"; // string | Filter the list to products that are valid for the submitted account number. For phone number based products, the account number should be in international phone number format.

try {
    $result = $apiInstance->getProducts($country_isos, $provider_codes, $sku_codes, $benefits, $region_codes, $account_number);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling V1Api->getProducts: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **country_isos** | [**string[]**](../Model/string.md)| Filter the list to products for countries with the given ISOs. | [optional]
 **provider_codes** | [**string[]**](../Model/string.md)| Filter the list to products supplied by providers with the submitted provider codes. | [optional]
 **sku_codes** | [**string[]**](../Model/string.md)| Filter the list to products with the submitted SkuCodes. | [optional]
 **benefits** | [**string[]**](../Model/string.md)| Filter the list to products with the listed benefits. | [optional]
 **region_codes** | [**string[]**](../Model/string.md)| Filter the list to products in regions with the submitted regionCodes. | [optional]
 **account_number** | **string**| Filter the list to products that are valid for the submitted account number. For phone number based products, the account number should be in international phone number format. | [optional]

### Return type

[**\Parenthesis\DingConnect\Model\GetProductsResponse**](../Model/GetProductsResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, text/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getPromotionDescriptions**
> \Parenthesis\DingConnect\Model\GetPromotionDescriptionsResponse getPromotionDescriptions($language_codes)

Get localized strings for promotions

Please see the documentation section on [localization](#localization).    Please see the documentation section on [querying](#querying).    #### Dates  It is not always possible to express when a promotion is available using the `ValidityPeriodIso`.  For example, a promotion may run for a two week period, but only be applicable on specific dates within that period.    In this case the `Dates` property of the localization description will contain a localized string describing the applicable  dates separated by semicolons. Blank means 'ongoing'.  For example - \"07/02/2017;07/03/2017;07/04/2017\".

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Parenthesis\DingConnect\Api\V1Api(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$language_codes = array("language_codes_example"); // string[] | Filter the list to promotion descriptions with the submitted language codes.

try {
    $result = $apiInstance->getPromotionDescriptions($language_codes);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling V1Api->getPromotionDescriptions: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **language_codes** | [**string[]**](../Model/string.md)| Filter the list to promotion descriptions with the submitted language codes. | [optional]

### Return type

[**\Parenthesis\DingConnect\Model\GetPromotionDescriptionsResponse**](../Model/GetPromotionDescriptionsResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, text/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getPromotions**
> \Parenthesis\DingConnect\Model\GetPromotionsResponse getPromotions($country_isos, $provider_codes, $account_number)

Get a list of promotions

Returns a list promotions that may apply for the submitted criteria.     Please see the documentation section on [querying](#querying).    #### Localization  Promotions have localized descriptions and you should call `GetPromotionDescriptions` to get the appropriate  localizations.  See the section on Localization above.    #### Validity Period  `ValidityPeriodIso` is expressed in the ISO8601 duration format. EG `P30D` is 30 days.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Parenthesis\DingConnect\Api\V1Api(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$country_isos = array("country_isos_example"); // string[] | Filter the list to promotions for countries with the given ISOs.
$provider_codes = array("provider_codes_example"); // string[] | Filter the list to promotions on products supplied by providers with the submitted provider codes.
$account_number = "account_number_example"; // string | Filter the list to promotions on products that are valid for the submitted account number. For phone number based products, the account number should be in international phone number format.

try {
    $result = $apiInstance->getPromotions($country_isos, $provider_codes, $account_number);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling V1Api->getPromotions: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **country_isos** | [**string[]**](../Model/string.md)| Filter the list to promotions for countries with the given ISOs. | [optional]
 **provider_codes** | [**string[]**](../Model/string.md)| Filter the list to promotions on products supplied by providers with the submitted provider codes. | [optional]
 **account_number** | **string**| Filter the list to promotions on products that are valid for the submitted account number. For phone number based products, the account number should be in international phone number format. | [optional]

### Return type

[**\Parenthesis\DingConnect\Model\GetPromotionsResponse**](../Model/GetPromotionsResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, text/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getProviderStatus**
> \Parenthesis\DingConnect\Model\GetProviderStatusResponse getProviderStatus($provider_codes)

Get the current status of product providers

Providers can be suspended or be in an error state. This API allows an agent to find out if it will be possible  to send a transfer to a particular provider.    Please see the documentation section on [querying](#querying).    #### Message  The `Message` property in the response is unformatted and non-localized text that gives further details of the   status of an operator. This message is directed at the agent and is not suitable for end-user consumption.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Parenthesis\DingConnect\Api\V1Api(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$provider_codes = array("provider_codes_example"); // string[] | Filter the list to providers with the submitted provider codes.

try {
    $result = $apiInstance->getProviderStatus($provider_codes);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling V1Api->getProviderStatus: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **provider_codes** | [**string[]**](../Model/string.md)| Filter the list to providers with the submitted provider codes. | [optional]

### Return type

[**\Parenthesis\DingConnect\Model\GetProviderStatusResponse**](../Model/GetProviderStatusResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, text/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getProviders**
> \Parenthesis\DingConnect\Model\GetProvidersResponse getProviders($provider_codes, $country_isos, $region_codes, $account_number)

Get a list of product providers available to the agent

Retrieves the list of providers available to the agent.    Please see the documentation section on [querying](#querying).    #### Name and ShortName  In some cases the `Name` property may include a country name or code. For example: \"Airtel India\" or  \"Vodafone UK\". `ShortName` will be the `Name` with country information removed, for example \"Airtel\" or \"Vodafone\". However  there are cases where that will make no sense: `Nepal Telecom` for example.  In these cases `ShortName` will be the same as `Name`    #### Validation Regex  When a transfer is attempted against products that a provider supplies, the first thing we will do is evaluate the   submitted Account Number against the `ValidationRegex`. The regex may contain multiple \"alternates\" in its definition  to cover all the products that the provider supplies, as a result an account number may pass the regex, but be invalid  for one product and valid for another.    The Ding system is .Net based and as a result we will use the <a href=\"https://msdn.microsoft.com/en-us/library/hs600312\" target=\"_blank\">Regex library from Microsoft</a>. That library is reported to  be Perl 5 compatible. We make every effort to ensure that the regular expression constructs we use are cross-language  compatible and we use <a href=\"https://regex101.com/\" target=\"_blank\">regex101</a> to test our regular expressions using the \"pcre\"   setting.    #### Customer Care Number  For certain products like PINs, it may be necessary to include a customer care number of the provider on the receipt  in order to handle customer care issues.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Parenthesis\DingConnect\Api\V1Api(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$provider_codes = array("provider_codes_example"); // string[] | Filter the list to providers with the submitted provider codes.
$country_isos = array("country_isos_example"); // string[] | Filter the list to providers in countries with the submitted countryIso.
$region_codes = array("region_codes_example"); // string[] | Filter the list to providers in regions with the submitted regionCodes.
$account_number = "account_number_example"; // string | Filter the list to providers that are valid for the submitted account number. For phone number based products, the account number should be in international phone number format.

try {
    $result = $apiInstance->getProviders($provider_codes, $country_isos, $region_codes, $account_number);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling V1Api->getProviders: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **provider_codes** | [**string[]**](../Model/string.md)| Filter the list to providers with the submitted provider codes. | [optional]
 **country_isos** | [**string[]**](../Model/string.md)| Filter the list to providers in countries with the submitted countryIso. | [optional]
 **region_codes** | [**string[]**](../Model/string.md)| Filter the list to providers in regions with the submitted regionCodes. | [optional]
 **account_number** | **string**| Filter the list to providers that are valid for the submitted account number. For phone number based products, the account number should be in international phone number format. | [optional]

### Return type

[**\Parenthesis\DingConnect\Model\GetProvidersResponse**](../Model/GetProvidersResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, text/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getRegions**
> \Parenthesis\DingConnect\Model\GetRegionsResponse getRegions($country_isos)

Get a list of regions on the system

Retrieves a list of regions used in the system. Each region includes a Region Code, Region Name and CountryIso.    Please see the documentation section on [reference data](#reference-data).

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Parenthesis\DingConnect\Api\V1Api(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$country_isos = array("country_isos_example"); // string[] | Filter the list to regions in countries with the submitted countryIso.

try {
    $result = $apiInstance->getRegions($country_isos);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling V1Api->getRegions: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **country_isos** | [**string[]**](../Model/string.md)| Filter the list to regions in countries with the submitted countryIso. | [optional]

### Return type

[**\Parenthesis\DingConnect\Model\GetRegionsResponse**](../Model/GetRegionsResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, text/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **listTransferRecords**
> \Parenthesis\DingConnect\Model\ListTransferRecordsResponse listTransferRecords($request)

Query transfers that were submitted to the system

ListTransferRecords gives the ability to search the details of transfers that have been submitted to the system by  the agent.  Note these transfers must not be older than 2 months.    Please see the documentation section on [paging](#paging).    Please see the documentation section on [querying](#querying).

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Parenthesis\DingConnect\Api\V1Api(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$request = new \Parenthesis\DingConnect\Model\ListTransferRecordsRequest(); // \Parenthesis\DingConnect\Model\ListTransferRecordsRequest | 

try {
    $result = $apiInstance->listTransferRecords($request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling V1Api->listTransferRecords: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **request** | [**\Parenthesis\DingConnect\Model\ListTransferRecordsRequest**](../Model/ListTransferRecordsRequest.md)|  |

### Return type

[**\Parenthesis\DingConnect\Model\ListTransferRecordsResponse**](../Model/ListTransferRecordsResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json, text/json, application/x-www-form-urlencoded
 - **Accept**: application/json, text/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **sendTransfer**
> \Parenthesis\DingConnect\Model\SendTransferResponse sendTransfer($request)

Send a transfer to an account

An agent will construct a request that contains a product `SkuCode` and a `SendValue` that  is between the Min and Max price (inclusive). The agent should also include a `DistributorRef` that   uniquely identifies the transfer within their system.    SendTransfer will respond with the transfer that was created - including a `TransferRef` that uniquely identifies the transfer within  our system. There will also be information about the state of the transfer and the amount that was received.    On success, we will deduct the value of the transfer from the agent balance and apply any applicable commissions.    The SendTranfer method has a maximum proccessing time of 90 seconds. After 90 seconds, if the SendTransfer request is not completed, the system will return a response with `ProviderTimedOut`.   This transaction will be treated as a failed transaction and the balance will not be deducted.     #### Sku Codes  You should only use `SkuCode` values returned by the `GetProducts` API call. No attempt should be made to guess or manufacture SkuCodes.    Products can be discontinued from time to time, and it is important that you keep up-to-date with the products available to your  account by regularly calling `GetProducts`.      #### ValidateOnly  When `ValidateOnly=true`, we will validate the request in our system to give an indication if a non validate transfer  would succeed with the submitted parameters.  We will attempt to contact the product provider to see if the  AccountNumber is valid in their system.  However, not all providers have a mechanism to validate account numbers. In  this case the system can not indicate if the SendTransfer will fail in advance.      The agent balance will not be deducted during ValidateOnly, however the balance will be checked.    When `ValidateOnly=true`, the `Price` in the response should be interpreted as an estimate only.    We will not assign a `TransferId` to the response when `ValidateOnly=true`    #### Settings  Some products declare `SettingDefintions` that mandate name-value pairs that can be submitted with the transfer and will be passed to  the Provider.     Agents can submit their own name-value pairs and we will store them with the transfer. These name-value pairs  can be queried upon using the `ListTransferRecords` method.    #### Processing State  `ProcessingState` will indicate the current state of the transfer as it progresses through our system over time.    - **Submitted**: The transfer was just submitted to the system and we have a record of it.  - **Processing**: The system has started processing the request and we are in the act of fulfilling the transfer.  - **Complete**: The transfer request is finished and it was successful.  - **Failed**: The transfer request is finished, but there was some form of error.  - **Cancelled**: The transfer request was cancelled.  - **Cancelling**: A request to cancel the transfer has been sent to the provider.    #### Receipts  In some cases there will be a `ReceiptText` in the response which will text that the product provider responded with, and this may  contain further instructions for the end user.      Sometimes the formatting of the ReceiptText returned by the provider is not acceptable, and an agent would like   to use the values in their own template. For example in a HTML page, or on a space restricted device. `ReceiptParams` will contain   information in name-value pairs that can be used to populate a template. The actual names will vary by provider and we will endeavour   to supply all the right pairs.      If there is a PIN code available, 'ReceiptParams' will contain the key 'Pin' with it's associated value.    In some cases, we do not control the receipt text returned by the provider, and from time to time they may alter  their text. If this happens, a name-value pair that previously existed in ReceiptParams dictionary may   disappear or a new one may pop up. Your application should be robust to these kind of changes.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Parenthesis\DingConnect\Api\V1Api(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$request = new \Parenthesis\DingConnect\Model\SendTransferRequest(); // \Parenthesis\DingConnect\Model\SendTransferRequest | 

try {
    $result = $apiInstance->sendTransfer($request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling V1Api->sendTransfer: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **request** | [**\Parenthesis\DingConnect\Model\SendTransferRequest**](../Model/SendTransferRequest.md)|  |

### Return type

[**\Parenthesis\DingConnect\Model\SendTransferResponse**](../Model/SendTransferResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json, text/json, application/x-www-form-urlencoded
 - **Accept**: application/json, text/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

