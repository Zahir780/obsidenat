```csharp
[HttpGet("GetAll")]
public async Task<ResponseDTO> GetTestConnection()
{
    ResponseDTO response = new ResponseDTO();
    response.status = 200;
    response.message = "Ok";

    SendSMS("11", "Asaduzzaman", "11", "8801837591722", "Test Message, SCBA", "Testing SMS");

    return response;
}
```
