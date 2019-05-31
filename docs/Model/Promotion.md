# Promotion

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**provider_code** | **string** | The code of the provider that the promotion applies to | 
**start_utc** | [**\DateTime**](\DateTime.md) | Start date and time in UTC of the promotion | 
**end_utc** | [**\DateTime**](\DateTime.md) | End date and time in UTC of the promotion. This will be DateTime.MaxValue if there is no end date. | 
**currency_iso** | **string** | Currency promotion - usually the same as the Provider | 
**validity_period_iso** | **string** | Validity of the promotion | [optional] 
**minimum_send_amount** | **float** | Minimum amount to be sent to apply for this promotion, specified in the distributor&#39;s currency | 
**localization_key** | **string** | Key to be used in conjunction with &#x60;GetPromotionDescriptions&#x60; | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


