# DingConnect-API-PHP

This PHP package was generated using the [Swagger Codegen](https://github.com/swagger-api/swagger-codegen) project:

- API version: V1
- Build package: io.swagger.codegen.languages.PhpClientCodegen

## Requirements

- PHP 5.5 and later

## Installation
### Composer

```
composer require parenthesis/dingconnect-api-php
```

## Usage


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

## Documentation for API Endpoints

All URIs are relative to *https://api.dingconnect.com*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*V1Api* | [**cancelTransfers**](docs/Api/V1Api.md#canceltransfers) | **POST** /api/V1/CancelTransfers | Attempt to cancel transfers with the submitted TransferIds
*V1Api* | [**estimatePrices**](docs/Api/V1Api.md#estimateprices) | **POST** /api/V1/EstimatePrices | Estimate prices for send or receive values
*V1Api* | [**getAccountLookup**](docs/Api/V1Api.md#getaccountlookup) | **GET** /api/V1/GetAccountLookup | Get providers and product information for a specific account number
*V1Api* | [**getBalance**](docs/Api/V1Api.md#getbalance) | **GET** /api/V1/GetBalance | Get the current agent balance
*V1Api* | [**getCountries**](docs/Api/V1Api.md#getcountries) | **GET** /api/V1/GetCountries | Get a list of supported countries
*V1Api* | [**getCurrencies**](docs/Api/V1Api.md#getcurrencies) | **GET** /api/V1/GetCurrencies | Get a list of supported currencies
*V1Api* | [**getErrorCodeDescriptions**](docs/Api/V1Api.md#geterrorcodedescriptions) | **GET** /api/V1/GetErrorCodeDescriptions | Get a list of error code descriptions
*V1Api* | [**getProductDescriptions**](docs/Api/V1Api.md#getproductdescriptions) | **GET** /api/V1/GetProductDescriptions | Get localized strings for products
*V1Api* | [**getProducts**](docs/Api/V1Api.md#getproducts) | **GET** /api/V1/GetProducts | Get a list of products that can be used in SendTransfer
*V1Api* | [**getPromotionDescriptions**](docs/Api/V1Api.md#getpromotiondescriptions) | **GET** /api/V1/GetPromotionDescriptions | Get localized strings for promotions
*V1Api* | [**getPromotions**](docs/Api/V1Api.md#getpromotions) | **GET** /api/V1/GetPromotions | Get a list of promotions
*V1Api* | [**getProviderStatus**](docs/Api/V1Api.md#getproviderstatus) | **GET** /api/V1/GetProviderStatus | Get the current status of product providers
*V1Api* | [**getProviders**](docs/Api/V1Api.md#getproviders) | **GET** /api/V1/GetProviders | Get a list of product providers available to the agent
*V1Api* | [**getRegions**](docs/Api/V1Api.md#getregions) | **GET** /api/V1/GetRegions | Get a list of regions on the system
*V1Api* | [**listTransferRecords**](docs/Api/V1Api.md#listtransferrecords) | **POST** /api/V1/ListTransferRecords | Query transfers that were submitted to the system
*V1Api* | [**sendTransfer**](docs/Api/V1Api.md#sendtransfer) | **POST** /api/V1/SendTransfer | Send a transfer to an account


## Documentation For Models

 - [AccountLookup](docs/Model/AccountLookup.md)
 - [CancelTransfersResponse](docs/Model/CancelTransfersResponse.md)
 - [CancellationRequest](docs/Model/CancellationRequest.md)
 - [Country](docs/Model/Country.md)
 - [Currency](docs/Model/Currency.md)
 - [Error](docs/Model/Error.md)
 - [ErrorDescription](docs/Model/ErrorDescription.md)
 - [EstimatePricesResponse](docs/Model/EstimatePricesResponse.md)
 - [EstimatedPrice](docs/Model/EstimatedPrice.md)
 - [EstimationRequest](docs/Model/EstimationRequest.md)
 - [GetAccountLookupResponse](docs/Model/GetAccountLookupResponse.md)
 - [GetBalanceResponse](docs/Model/GetBalanceResponse.md)
 - [GetCountriesResponse](docs/Model/GetCountriesResponse.md)
 - [GetCurrenciesResponse](docs/Model/GetCurrenciesResponse.md)
 - [GetErrorCodeDescriptionsResponse](docs/Model/GetErrorCodeDescriptionsResponse.md)
 - [GetProductDescriptionsResponse](docs/Model/GetProductDescriptionsResponse.md)
 - [GetProductsResponse](docs/Model/GetProductsResponse.md)
 - [GetPromotionDescriptionsResponse](docs/Model/GetPromotionDescriptionsResponse.md)
 - [GetPromotionsResponse](docs/Model/GetPromotionsResponse.md)
 - [GetProviderStatusResponse](docs/Model/GetProviderStatusResponse.md)
 - [GetProvidersResponse](docs/Model/GetProvidersResponse.md)
 - [GetRegionsResponse](docs/Model/GetRegionsResponse.md)
 - [IApiResponse](docs/Model/IApiResponse.md)
 - [InternationalDialingInfo](docs/Model/InternationalDialingInfo.md)
 - [ListTransferRecordsRequest](docs/Model/ListTransferRecordsRequest.md)
 - [ListTransferRecordsResponse](docs/Model/ListTransferRecordsResponse.md)
 - [LocalizedProductDescription](docs/Model/LocalizedProductDescription.md)
 - [LocalizedPromotionDescription](docs/Model/LocalizedPromotionDescription.md)
 - [Price](docs/Model/Price.md)
 - [Product](docs/Model/Product.md)
 - [Promotion](docs/Model/Promotion.md)
 - [Provider](docs/Model/Provider.md)
 - [ProviderStatus](docs/Model/ProviderStatus.md)
 - [Region](docs/Model/Region.md)
 - [SendTransferRequest](docs/Model/SendTransferRequest.md)
 - [SendTransferResponse](docs/Model/SendTransferResponse.md)
 - [Setting](docs/Model/Setting.md)
 - [SettingDefinition](docs/Model/SettingDefinition.md)
 - [TransferId](docs/Model/TransferId.md)
 - [TransferRecord](docs/Model/TransferRecord.md)
 - [TransferRecordWithErrorCodes](docs/Model/TransferRecordWithErrorCodes.md)
 - [TransferWithState](docs/Model/TransferWithState.md)


## Documentation For Authorization


## APIKeyHeader

- **Type**: API key
- **API key parameter name**: api_key
- **Location**: HTTP header
