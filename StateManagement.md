# StateManagement in Asp.Net
State management is a technique that is used to manage a state of an object on different request. 
It is very important to manage state in any web application. There are two types of state management systems in ASPNET.
| Client-Side State Management  | Server-Side State Management | 
 |:--- |:-----|
 |Client-Side| Server-Side |
 | ViewState |SessionState-->In-proc,State server,Sql server |
 | Hidden field | ApplicationState|
 | Cookies-->Persistent & Non-Persistent Cookie | 
 | Control State |  
 | Query Strings |  
 
 
 # Client-Side StateManagement
 ### Viewstate : 
 * It is the method that the ASP.NET page framework uses to preserve page and control values between round trips(requests).
 * ViewState data is serialized into base64-encoded strings, and is stored in Hidden input fields.<br />

 **Example : WebForm1.aspx**
 ```C#
 <%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="ViewState_Demo.WebForm1" %>
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title></title>
</head>
<body>
    <form id="form1" runat="server">
        number:
        <asp:TextBox ID="TextBox1" runat="server"></asp:TextBox>
        <asp:Button ID="Button1" runat="server" Text="Add 1more" OnClick="Button1_Click" />
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

namespace ViewState_Demo
{
    public partial class WebForm1 : System.Web.UI.Page
    {
        int clicks_Count = 1;
        protected void Page_Load(object sender, EventArgs e)
        {
            if (!IsPostBack)
            {
                TextBox1.Text = "0";
            }
        }

        protected void Button1_Click(object sender, EventArgs e)
        {
            if (ViewState["click"] != null)
            {
                clicks_Count = Convert.ToInt32(ViewState["click"]) + 1;
            }
            TextBox1.Text = clicks_Count.ToString();
            ViewState["click"] = TextBox1.Text;
        }
    }
}
````
---

 ### Hidden field : 
 * It is used for storing small amounts of data on the client side. In most simple words it's just a container of some
    objects but their result is not rendered on our web browser. It is invisible in the browser.<br /><br />
    **Example : WebForm1.aspx**
 ```C#
 <%@ Page Language="C#" AutoEventWireup="true" CodeBehind="DateHiddenValue.aspx.cs" Inherits="HiddenField.WebForm1" %>
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title></title>
</head>
<body>
    <form id="form1" runat="server">
        <asp:HiddenField ID="HiddenField1" runat="server" />
        <asp:Label ID="Label1" runat="server" Text="Label"></asp:Label>
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

namespace HiddenField
{
    public partial class WebForm1 : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e)
        {
            HiddenField1.Value = DateTime.Now.ToString();
            Label1.Text = Convert.ToString(HiddenField1.Value);
        }
    }
}
```
---

  ### Cookies  :
  * It is a small piece of information stored on the client machine. This file is located on client machines path.  
    Its is used to store user preference information like Username, Password,City and PhoneNo etc on client machines.<br/>
    **1.Persistant Cookie :** A cookie has not have expired time Which is called as Persist Cookie<br />
    **2.Non-Persist Cookie :** A cookie has expired time Which is called as Non-Persist Cookie.<br />
    **Example : WebForm1.aspx**
```C#
     <%@ Page Language="C#" AutoEventWireup="true" CodeBehind="StudentCookie.aspx.cs" Inherits="Cookies.Persistent" %>
      <!DOCTYPE html>
      <head runat="server">
        <title></title>
      </head>
     <body>
     <form id="form1" runat="server">
        <div>
            <asp:TextBox ID="TextBox1" runat="server"></asp:TextBox>
            <asp:Button ID="Button1" runat="server" Text="Button" OnClick="Button1_Click" /><br />
           fetched cookie: <asp:Label ID="Label1" runat="server" Text=""></asp:Label>
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

namespace Cookies
{
    public partial class Persistent : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e)
        {
            HttpCookie co_Val = Request.Cookies["student"];
            if (co_Val != null)
            {
                Label1.Text = co_Val["name"];
            }
        }

        protected void Button1_Click(object sender, EventArgs e)
        {
            HttpCookie cookie = new HttpCookie("student");

            cookie["name"] = TextBox1.Text;
            cookie.Expires = DateTime.Now.AddDays(5);//persistent cookie
            Response.Cookies.Add(cookie);
        }
    }
}


```
---

 *  **Control State** : Used for enabling the View State Property,It defines a custom control(Load Control State & Save Control State) and it Can't be modified,
                   It can Accessed directly or disabled. <br />
  ### Query String : 
  * It is one of the techniques in Web applications to send data from one webform to another through the URL.
  * A query string consists of two parts, field and value, and each of pair separated by ampersand (&).<br />
   **Example : WebForm1.aspx**
```C#
    <form id="form1" runat="server">
        <asp:TextBox ID="TextBox1" runat="server"></asp:TextBox>
        <asp:Button ID="Button1" runat="server" Text="Button" OnClick="Button1_Click" />
    </form>
```
**WebForm1.aspx.cs**
```C#
 	 protected void Button1_Click(object sender, EventArgs e)
        {
            Response.Redirect("WebForm2.aspx?Name=" + TextBox1.Text);
        }
```  
 **Example : WebForm2.aspx**
```C#
    <form id="form1" runat="server">
        Name:<asp:Label ID="Label1" runat="server" Text="Label"></asp:Label>
    </form>
```
**WebForm2.aspx.cs**
```C#
 	 protected void Page_Load(object sender, EventArgs e)
        {
            if (!IsPostBack)
            {
                if (Request.QueryString["Name"] != null && Request.QueryString["Name"] != string.Empty)
                    Label1.Text = Request.QueryString["Name"];
            }
        }
```  
 ---
 # Server-Side StateManagement
 * **Session State** : Enables you to store and retrieve values for a user as the user navigates ASP.NET pages in a Web application.<br />
  **a**, **InProc mode:** which stores session state in memory on the Web server. This is the default.<br />
   **Example : WebForm1.aspx**
```C#
  <form id="form1" runat="server">
       
        <asp:TextBox ID="TextBox1" runat="server"></asp:TextBox>
        <asp:Button ID="Button1" runat="server" Text="Button" OnClick="Button1_Click" />
    </form>
    protected void Button1_Click(object sender, EventArgs e)
        {
            
            Session["name"] = TextBox1.Text;
            Response.Redirect("page2.aspx");
        }
 ```       
  **WebForm2.aspx**
```C#
 <form id="form1" runat="server">
          Name:  <asp:Label ID="Label1" runat="server" Text="Label"></asp:Label>
    </form>
    
    protected void Page_Load(object sender, EventArgs e)
        {
            if (Session["name"] != null)
            {
                Label1.Text = Session["name"].ToString();
            }
        }
 ```      
  **b**, **StateServer mode:** which stores session state in a separate process called the ASP.NET state service. 
          This ensures that session state is preserved if the Web application is restarted and also makes session
          state available to multiple Web servers in a Web farm.<br />
```C#
    <sessionState mode="StateServer" stateConnectionString="tcpip=localhost:44389" timeout="20">
    </sessionState>
```    
  **c**, **SQLServer** : mode stores session state in a SQL Server database. This ensures that session state is preserved 
          if the Web application is restarted and also makes session state available to multiple Web servers in a Web farm(web application deployed on multiple server).<br />
 * **Application State** : which stores variables that can be accessed by all users of an ASP.NET application.
   
