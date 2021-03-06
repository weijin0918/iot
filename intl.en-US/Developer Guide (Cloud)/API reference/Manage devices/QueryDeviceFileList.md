# QueryDeviceFileList {#reference_rzd_ftf_2hb .reference}

You can call this operation to query information about all files that are uploaded to IoT Platform from the specified device.

## Restrictions and guidelines {#section_ol2_ytf_2hb .section}

The returned file information for this operation call does not contain download URLs. To obtain the download URL of a file, call [QueryDeviceFile](reseller.en-US/Developer Guide (Cloud)/API reference/Manage devices/QueryDeviceFile.md#).

## Request parameters {#section_oxs_xtf_2hb .section}

|Parameter|Type|Required|Description|
|:--------|:---|:-------|:----------|
|Action|String |Yes|The operation that you want to perform. Set the value to QueryDeviceFileList.|
|IotId|String|No|The unique identifier of the device.**Note:** If you provide this parameter, you do not need to provide the ProductKey or DeviceName parameters. As the GUID of the device, IotId corresponds to the combination of ProductKey and DeviceName. If you provide both IotId and the combination of ProductKey and DeviceName, IotId takes precedence. This parameter cannot be left empty.

|
|ProductKey|String|No|The key of the product to which the device belongs. **Note:** If you provide this parameter, you must also provide the DeviceName parameter.

|
|DeviceName|String|No|The device name. **Note:** If you provide this parameter, you must also provide the ProductKey parameter.

|
|PageSize|Integer|No|The number of items per page displayed in the returned results. Maximum value: 200. Default value: 10.|
|CurrentPage|Integer|No|The page of returned results to be displayed. Minimum value:1 . Default value: 1.|
|Common request parameters|N/A|Yes|See [Common parameters](reseller.en-US/Developer Guide (Cloud)/API reference/Common parameters.md#).|

## Response parameters {#section_m2r_35f_2hb .section}

|Parameter|Type|Description|
|:--------|:---|:----------|
|RequestId|String|The GUID generated by Alibaba Cloud for the request.|
|Success|Boolean|Indicates whether the call is successful. A value of true indicates that the call is successful. A value of false indicates that the call has failed.|
|ErrorMessage|String|The error message returned when the call fails.|
|Code|String|The error code returned when the call fails. For more information about error codes, see [Error codes](reseller.en-US/Developer Guide (Cloud)/API reference/Error codes.md#).|
|Data|List<FileStoreSummary\>|The list of file information returned when the call is successful. For more information, see the following table: [Parameters in FileStoreSummary](#).|

|Parameter|Type|Description|
|:--------|:---|:----------|
|FileId|String|The file identifier.|
|Name|String|The file name.|
|Size|String|The file size.|
|UtcCreatedOn|String|The time when the file was created.|

## Examples {#section_drn_l5f_2hb .section}

**Sample request**

```
https://iot.cn-shanghai.aliyuncs.com/?Action=QueryDeviceFileList
&ProductKey=al********
&DeviceName=deviceName1
&PageSize=10
&CurrentPage=1
&Common request parameters
```

**Sample responses**

-   JSON format

    ```
    {
      "PageCount": 1, 
      "Data": {
        "FileStoreSummary": [
          {
            "Name": "testFile2.txt", 
            "FileId": "xL0G67MBLBDtkR7GCfT******", 
            "UtcCreatedOn": "2019-03-21T08:45:42.000Z", 
            "Size": "102400"
          }, 
          {
            "Name": "testFile3.txt", 
            "FileId": "6UCo1SqbqnQEoh9aKqD******", 
            "UtcCreatedOn": "2019-03-21T08:45:42.000Z", 
            "Size": "102400"
          }, 
          {
            "Name": "testFile1.txt", 
            "FileId": "IhXXww3Eeu6uzSOSCyu******", 
            "UtcCreatedOn": "2019-03-21T08:45:40.000Z", 
            "Size": "102400"
          }
        ]
      }, 
      "PageSize": 10, 
      "RequestId": "7C7BA526-826D-46AA-A45E-55D21E6D1583", 
      "CurrentPage": 1, 
      "Success": true, 
      "Total": 3
    }
    ```

-   XML format

    ```
    <? xml version="1.0" encoding="utf-8"? >
    <QueryDeviceFileListResponse>
     <PageCount>1</PageCount>
     <Data>
       <FileStoreSummary>
         <Name>testFile2.txt</Name>
         <FileId>xL0G67MBLBDtkR7GCfT******</FileId>
         <UtcCreatedOn>2019-03-21T08:45:42.000Z</UtcCreatedOn>
         <Size>102400</Size>
       </FileStoreSummary>
       <FileStoreSummary>
         <Name>testFile3.txt</Name>
         <FileId>6UCo1SqbqnQEoh9aKqD******</FileId>
         <UtcCreatedOn>2019-03-21T08:45:42.000Z</UtcCreatedOn>
         <Size>102400</Size>
       </FileStoreSummary>
       <FileStoreSummary>
         <Name>testFile1.txt</Name>
         <FileId>IhXXww3Eeu6uzSOSCyu******</FileId>
         <UtcCreatedOn>2019-03-21T08:45:40.000Z</UtcCreatedOn>
         <Size>102400</Size>
       </FileStoreSummary>
     </Data>
     <PageSize>10</PageSize>
     <RequestId>BF06F7FD-B199-4B90-9128-8416F975135E</RequestId>
     <CurrentPage>1</CurrentPage>
     <Success>true</Success>
     <Total>3</Total>
    </QueryDeviceFileListResponse>
    ```


