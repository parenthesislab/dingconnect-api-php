# TransferRecord

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**transfer_id** | [**\Parenthesis\DingConnect\Model\TransferId**](TransferId.md) | Both system and customer identifiers for the specific transfer | [optional] 
**sku_code** | **string** | The unique product SkuCode | 
**price** | [**\Parenthesis\DingConnect\Model\Price**](Price.md) | The resulting price of the SendTransfer | [optional] 
**commission_applied** | **float** | The actual commision that was earned for selling this transfer | 
**started_utc** | [**\DateTime**](\DateTime.md) | The UTC datetime when processing the transfer was started. | [optional] 
**completed_utc** | [**\DateTime**](\DateTime.md) | The UTC datetime that the transfer was recorded as being completed in our system | [optional] 
**processing_state** | **string** | Will indicate the current state of the transfer as it progresses through our system | 
**receipt_text** | **string** | Provider specific receipt text for the transfer. May contain additional information for the end customer. | [optional] 
**receipt_params** | **map[string,string]** | Name value pairs of data that is in the ReceiptText. | [optional] 
**account_number** | **string** | The account number targeted in the transfer | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


