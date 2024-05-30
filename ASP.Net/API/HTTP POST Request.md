## Model Part
```c#
public class MemberRegistration
{
     [Key]
     public int id { get; set; }

     public string member_name { get; set; }
     public string spouse_name { get; set; }
     public string father_name { get; set; }
     public string mother_name { get; set; }
     public string nationality { get; set; }
     public string number_of_son { get; set; }
 }
```
## Controller Part
```c#
[HttpPost("memberRegistrationOnline")]
[ProducesResponseType(StatusCodes.Status200OK)]
[ProducesResponseType(StatusCodes.Status404NotFound)]
[ProducesResponseType(StatusCodes.Status400BadRequest)]
public async Task<ActionResult<ResponseDTO>> MemberRegistrationOnline(MemberRegistration request)
{
    // Bad Request check
    if (string.IsNullOrEmpty(request.member_name))
    {
        return BadRequest();
    }

    ResponseDTO response = new ResponseDTO();
    SqlConnection con = new SqlConnection(sqlCon);

    SqlTransaction transaction = null;
    int tempId = 0;

    try
    {
        await con.OpenAsync();

        //con.Open();
        transaction = con.BeginTransaction("memberRegistrationOnline");
        string sql = "insert into tbMemberRegistration " +
            "(member_name,spouse_name,father_name,mother_name,nationality,number_of_son)" +
            "values" +
            "(@member_name,@spouse_name,@father_name,@mother_name,@nationality,@number_of_son)";
        SqlCommand cmd2 = new SqlCommand(sql, con, transaction);
        cmd2.Parameters.AddWithValue("@member_name", request.member_name);
        cmd2.Parameters.AddWithValue("@spouse_name", request.spouse_name);
        cmd2.Parameters.AddWithValue("@father_name", request.father_name);
        cmd2.Parameters.AddWithValue("@mother_name", request.mother_name);
        cmd2.Parameters.AddWithValue("@nationality", request.nationality);
        cmd2.Parameters.AddWithValue("@number_of_son", request.number_of_son);
        
        cmd2.ExecuteNonQuery();
        transaction.Commit();
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
        if (transaction != null)
        {
            transaction.Rollback();
        }
        con.Close();
        response.status = 500;
        response.isFound = false;
        response.message = "Internal System Error.! Please try again leter.";
        return response;
    }
    finally
    {
        con.Close();
    }
    response.isFound = true;
    response.status = 200;
    response.message = "Member Registration success. your Traking id is: "+ tempId;

    return response;
}
```