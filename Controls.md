# Validation Controls      <br/>

Validation is important part of any web application. User's input must always be validated before sending across different layers of the application.


## Validation is of two types:<br/>
 1. Client Side
2. Serve Side<br/>

### Client Side Control :
* Client side validation is good but we have to be dependent on browser and scripting language support.
* Client side validation is considered convenient for users as they get instant feedback.
* The main advantage is that it prevents a page from being postback to the server until the client validation is executed successfully.
* For developer point of view serve side is preferable because it will not fail, it is not dependent on browser and scripting language.
* We can use ASP.NET validation, which will ensure client, and server validation. It work on both end; 
  first it will work on client validation and than on server validation. At any cost server validation will work always whether client validation is executed or not.
 So we have a safety of validation check.

### Validation Controls in ASP.NET :

|                                           Validation Controls |                                                  Description                                      |
|---------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| RequiredFieldValidation                                       | Makes an input control a required field                                                           |
| CompareValidator	                                        | Compares the value of one input control to the value of another input control or to a fixed value     |                                                                        |
| RangeValidator                                                | Checks that the user enters a value that falls between two values                                 |
| RegularExpressionValidator	                                | Ensures that the value of an input control matches a specified pattern                            |
| CustomValidator	                                        | Allows you to write a method to handle the validation of the value entered                        |
| ValidationSummary	                                        | Displays a report of all validation errors occurred in a Web page                                 |

#### Examples: 
**WebForm1.aspx**
```C#
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="register.aspx.cs" Inherits="WebApplication1.register" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title></title>
</head>
<body>
     <form id="form1" runat="server">
         <div>
             <div>
                 <asp:Label ID="Label1" runat="server" Text="UserId"></asp:Label>
                 <asp:TextBox ID="TextBox1" runat="server"></asp:TextBox>
                 <asp:RequiredFieldValidator ID="RequiredFieldValidator1" runat="server" ErrorMessage="UserId is mandatory"
                 ControlToValidate="TextBox1" ForeColor="Black" 
                 SetFocusOnError="True"></asp:RequiredFieldValidator><br />
            </div>
            <div>
                <asp:Label ID="Label2" runat="server" Text="Password"></asp:Label>
                <asp:TextBox ID="TextBox2" runat="server"></asp:TextBox>
                <asp:CustomValidator ID="CustomValidator1" runat="server" ControlToValidate="TextBox2" Display="Dynamic" 
                ErrorMessage="Password must contain 5 letters" ForeColor="Black" OnServerValidate="CustomValidator1_ServerValidate"
                SetFocusOnError="True" ValidateEmptyText="True">Invalid Password</asp:CustomValidator>
                <br />
            </div>
            <div>
                <asp:Label ID="Label3" runat="server" Text="Confirm Password"></asp:Label>
                <asp:TextBox ID="TextBox3" runat="server"></asp:TextBox>
                <asp:CompareValidator ID="CompareValidator1" runat="server" ControlToValidate="TextBox3" Display="Dynamic" 
                ErrorMessage="password and confirm password
                is not same" ForeColor="Black" SetFocusOnError="True" ControlToCompare="TextBox2">Password Mismatched</asp:CompareValidator>
                <br />
                <br />
            </div>
            <div>
                <asp:Label ID="Label4" runat="server" Text="Email"></asp:Label>
                <asp:TextBox ID="TextBox4" runat="server"></asp:TextBox>
                <asp:RegularExpressionValidator ID="RegularExpressionValidator1" runat="server" 
                ErrorMessage="Email id is incorrect" ControlToValidate="TextBox4"Display="Dynamic" ForeColor="Black" SetFocusOnError="True" 
                ValidationExpression="\w+([-+.']\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*">Invalid EmailId
                </asp:RegularExpressionValidator>
                <br />
            </div>
            <div>
                <asp:Label ID="Label5" runat="server" Text="Mobile Number"></asp:Label>
                <asp:TextBox ID="TextBox5" runat="server"></asp:TextBox>
                <asp:CustomValidator ID="CustomValidator2" runat="server" ControlToValidate="TextBox5" 
                ErrorMessage="enter correct number" OnServerValidate="CustomValidator2_ServerValidate">enter correct number</asp:CustomValidator>
                <br />
            </div>
            <div>
                <asp:Label ID="Label6" runat="server" Text="DOB"></asp:Label>
                <asp:TextBox ID="TextBox6" runat="server"></asp:TextBox>
                <asp:RangeValidator ID="RangeValidator1" runat="server" ControlToValidate="TextBox6" 
                Display="Dynamic" ErrorMessage="Age must be between 18 and 35" 
                ForeColor="Black" SetFocusOnError="True" Type="Date">Age not in range</asp:RangeValidator>
                <br />
                <br />
            </div>
            <asp:Button ID="Button1" runat="server" Text="Submit" OnClick="Button1_Click" />
        </div>
    </form>
</body>
</html>

```
 **WebForm1.aspx.cs**
```C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

namespace WebApplication1
{
    public partial class register : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e)
        {
         
        }

      
        protected void CustomValidator1_ServerValidate(object source, ServerValidateEventArgs args)
        {
            int len = args.Value.Length;
            if (len >= 8 && len <= 15)
            {
                args.IsValid = true;

            }
            else
            {
                args.IsValid = false;
            }
        }

        protected void CustomValidator2_ServerValidate(object source, ServerValidateEventArgs args)
        {
            int len = args.Value.Length;
            if (len==10)
            {
                args.IsValid = true;

            }
            else
            {
                args.IsValid = false;
            }
        }

        protected void Button1_Click(object sender, EventArgs e)
        {
            RangeValidator1.MinimumValue = DateTime.Now.AddYears(-45).ToShortDateString();
            RangeValidator1.MaximumValue = DateTime.Now.AddYears(-10).ToShortDateString();

        }
    }
}
```
 
