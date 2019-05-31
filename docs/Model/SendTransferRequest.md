# SendTransferRequest

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**sku_code** | **string** | Code provided by GetProducts API | 
**send_value** | **double** | The transfer value to be sent. Specified to two decimal places of accuracy of the major currency unit, e.g. 3.17 USD. | 
**send_currency_iso** | **string** | The currency of the &#x60;SendValue&#x60;. If this is null or empty, we will assume distributor currency. | [optional] 
**account_number** | **string** | The account number to target | 
**distributor_ref** | **string** | Unique identifier in the distributor system to be associated with the transfer | 
**settings** | [**\Parenthesis\DingConnect\Model\Setting[]**](Setting.md) | Product specific name/value pairs to be associated with the transfer request | [optional] 
**validate_only** | **bool** | Validate the request with the provider without doing a transfer | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


