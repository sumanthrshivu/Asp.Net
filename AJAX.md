# AJAX (Asynchronous JavaScript and XML)
* Ajax is “the method of exchanging data with a server, and updating parts of a web page – without reloading the entire page.” 
![Screenshot (33)](https://user-images.githubusercontent.com/74582120/131965336-ed1185b7-c8d1-4db5-8277-21a08b9b1e19.png)

## There are 4 main benefits of using Ajax in web applications:
### Callbacks:
* Ajax is used to perform a callback, making a quick round trip to and from the server to retrieve and/or save data without posting the entire page back to the server. 
### Making Asynchronous Calls: 
* Ajax allows you to make asynchronous calls to a web server. This allows the client browser to avoid waiting for all data to arrive before allowing the user to act once more.
### User-Friendly: 
* Because a page postback is being eliminated, Ajax enabled applications will always be more responsive, faster and more user-friendly.
### Increased Speed:
* The main purpose of Ajax is to improve the speed, performance and usability of a web application, since the data from user will be saved to their database without waiting for the page to refresh or reload.

## Basic Controls of ASP.NET AJAX

### 1) ScriptManager

* ScriptManager is a server-side control.The ScriptManager control is central to Ajax functionality in ASP.NET. <br/>
* The ScriptManager manages all ASP.NET AJAX resources on a web page. It renders the AJAX library to the browser and supports partial page rendering. <br/>
* It provide access to web service method from script by registering Web services with the ScriptManager control, Without script manager we can't use AJAX controls on the web page.
 
### 2) UpdatePanel
* The UpdatePanel control specifies a part of a Web page which can be updated or refreshed partially based on the update condition. <br/>
*  Refreshing a specific part of a Web page is referred as partial-page update. <br/>
*  You can also add one or more UpdatePanel control in the Web page. <br/>
* The UpdatePanel control uses the AJAX library to support the partial-page rendering. <br/>

 **WebForm1.aspx**
```C#
    <form id="form1" runat="server">
         <div>
           <asp:ScriptManager ID="ScriptManager1" runat="server"></asp:ScriptManager>
            <asp:UpdatePanel ID="UpdatePanel1" runat="server">
            <ContentTemplate>
              <asp:Timer ID="Timer1" runat="server" Interval="1000" OnTick="Timer1_Tick"></asp:Timer>
              <asp:Label ID="Label1" runat="server" ></asp:Label>  
            </ContentTemplate>
            </asp:UpdatePanel>
        </div>
    </form>
```
**WebForm1.aspx.cs**
```C#
    protected void Timer1_Tick(object sender, EventArgs e)
        {
            Label1.Text = DateTime.Now.ToLongTimeString();
        }
```        
