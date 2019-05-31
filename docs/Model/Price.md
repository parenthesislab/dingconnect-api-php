# Price

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**customer_fee** | **float** | The fee that the distributor has asked us to collect from the customer | 
**distributor_fee** | **float** | The fee that Ding charges the distributor to fulfil the transfer | 
**receive_value** | **float** | The estimated value that will be received by the target account, including any tax (if applicable). | 
**receive_currency_iso** | **string** | The currency of the ReceiveValue and ReceiveValueExcludingTax fields | 
**receive_value_excluding_tax** | **float** | The estimated amount received into the account before Tax was added | 
**tax_rate** | **float** | The tax rate that was applied | [optional] 
**tax_name** | **string** | The name of the tax applicable to this product | [optional] 
**tax_calculation** | **string** | The type of calculation that was done (can vary by country) | [optional] 
**send_value** | **float** | The value that is submitted to SendTransfer | 
**send_currency_iso** | **string** | The currency of the SendValue field | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


