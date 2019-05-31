# TransferRecordWithErrorCodes

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**transfer_record** | [**\Parenthesis\DingConnect\Model\TransferRecord**](TransferRecord.md) | The transfer record that was created as a result of a SendTransfer | 
**result_code** | **int** |  | 
**error_codes** | [**\Parenthesis\DingConnect\Model\Error[]**](Error.md) | Any error codes that were returned as part of the SendTransfer or in the case of a Batch &#x60;ProcessingMode&#x60;              that may have occurred later after the batch was submitted to the Provider. | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


