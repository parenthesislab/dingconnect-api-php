# Product

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**provider_code** | **string** | The provider of the product | 
**sku_code** | **string** | Unique code to be used in conjunction with &#x60;SendTransfer&#x60; (SKU: \&quot;Stock Keeping Unit\&quot;). | 
**localization_key** | **string** | Key to be used in conjunction with &#x60;GetProductDescriptions&#x60; | 
**setting_definitions** | [**\Parenthesis\DingConnect\Model\SettingDefinition[]**](SettingDefinition.md) | Name/Value pairs that should be submitted during &#x60;SendTransfer&#x60; | 
**maximum** | [**\Parenthesis\DingConnect\Model\Price**](Price.md) | The Maximum price that can be sold | 
**minimum** | [**\Parenthesis\DingConnect\Model\Price**](Price.md) | The Minimum price that can be sold | 
**commission_rate** | **float** | The rate of commission that will be applied for selling this product | 
**processing_mode** | **string** | Transaction processing mode for this product | 
**redemption_mechanism** | **string** | Indicates if the customer is required to take further action in order to redeem the transfer | 
**benefits** | **string[]** | What type of benefits will the transfer give to the target account | 
**validity_period_iso** | **string** | How long is the product valid for after purchase | [optional] 
**uat_number** | **string** | User Acceptance Test Number | 
**additional_information** | **string** | Any distributor specific information/caveats about this particular product | [optional] 
**default_display_text** | **string** | The Display text from the &#x60;LocalizedProductDescription&#x60; in the default language (usually \&quot;en\&quot;). | 
**region_code** | **string** | Region for this product | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


