# GetAccountLookupResponse

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**country_iso** | **string** | The country of the account number | [optional] 
**account_number_normalized** | **string** | We attempt to normalize phone numbers following the public telecommunication numbering plan &lt;a href&#x3D;\&quot;https://en.wikipedia.org/wiki/E.164\&quot; target&#x3D;\&quot;_blank\&quot;&gt;E.164&lt;/a&gt;, if we succeed the normalized number will be returned in this field formatted as E164 without leading &#39;+&#39; | [optional] 
**items** | [**\Parenthesis\DingConnect\Model\AccountLookup[]**](AccountLookup.md) | This will contain provider information associated to the account number. If we can succesfully lookup the account number               the list will contain the info for products associated to it. | 
**result_code** | **int** |  | 
**error_codes** | [**\Parenthesis\DingConnect\Model\Error[]**](Error.md) |  | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


