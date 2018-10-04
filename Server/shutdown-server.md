{{{
  "title": "ShutdownServer",
  "date": "2-7-2013",
  "author": "Luke Bakken",
  "attachments": []
}}}

Shuts down the operating system and then powers off server.

<div class="alert alert-warning">
<h2>V2 API Available</h2>
There is an equivalent V2 API that should be used instead. Please use the Power Operations | <a href="../v2/#power-operations-shut-down-server">Shut Down Server</a> API.
</div>

## URL

    REST: https://api.ctl.io/REST/Server/ShutdownServer/&lt;format&gt;
    SOAP: https://api.ctl.io/SOAP/Server.asmx?op=ShutdownServer

## Request

### Attributes

| Name | Type | Description | Req. |
| --- | --- | --- | --- |
| AccountAlias | String | The alias of the account that owns the server. If not provided it will assume the account to which the API user is mapped. Providing this value gives you the ability to access servers in your sub accounts | No |
| Name | String | The name of the Server to shut down. | Yes |

### Examples

#### JSON

    {
      "AccountAlias": "UNK",
      "Name": "SERVER01"
    }

#### XML

    <ServerRequest>
      <AccountAlias>ACCT</AccountAlias>
      <Name>SERVER01</Name>
    </ServerRequest>

## Response

### Attributes

| Name | Type | Description |
| --- | --- | --- |
| Success | Boolean | True if the request was successful, otherwise False. |
| Message | String | A description of the result. The contents of this field does not contain any actionable information, it is purely intended to provide a human readable description of the result. |
| StatusCode | Int | This value will help to identify any errors which were encountered while processing the request. The value of '0' indicates success, all non-zero StatusCodes indicate an error state. |
| RequestID | Int | The ID of the Queued request. Status of the request can be obtained by calling the [Get Deployment Status](../Blueprint/get-deployment-status.md) method. |

### Examples

#### JSON

    {
      "RequestID:1,
      "Success":true,
      "Message":"Success",
      "StatusCode":0
    }

#### XML

    <QueuedItemResponse Success="true" Message="Success" StatusCode="0">
        <RequestID>1</RequestID>
    </QueuedItemResponse>

### Status Codes

| Status Code | Description |
| --- | --- |
| 0 | Request was successfully processed |
| 2 | Unknown Error.  An application error occurred processing your request, contact support to resolve the issue. |
| 3 | Invalid Request Format. This value indicates that the XML or JSON requests do not match the expected format. |
| 5 | Resource Not Found.  A Server with the specified Name cannot be found. |
| 6 | Invalid Operation.  Server must be in an active state. |
| 100 | Authentication Failed.  You must logon to the API prior to calling this method. |
| 1410 | Name required.  The name parameter must be specified. |