# Page Life Cycle in ASP.Net

|                 Page Life Cycle Events                        |                        Description                                                                             |                                         
|---------------------------------------------------------------|---------------------------------------------------------------------------------------------------- |
| PreInit                                                       | This event happens just before page initialisation event starts .Is postback, Is callback and Is cross page postback properties are set at this stage.this event allows us to set the master page andtheme of webapplication dynamically.|
| Init                                                          | page init, event occurs after the init event of all the individual controls on the web form.Use this event to read or initialize control properties. the server controls are loaded and initialized from the web forms viewstate.|                                                      |
| InitComplete                                                  | This event occurs immediately after page initialization.Use this event for processing tasks that require all initialization to be complete.|                                                                                                                                          
| PreLoad                                                       | This event occurs just before the page load event.Loads ViewState: ViewState data are loaded to controls Loads Postback data: Postback data are now handed to the page controls.|                                                                                                                                           
| Load                                                          | This is the first place in the page lifecycle that all values are restore. page load event occurs before the load event of all individual controls on that web form|                                                                                                                                          
| Control Events                                                | After the page load event the control events like on button click, dropdown list events are raised  |                                                                                                                                         
| Load Complete                                                 | This event occurs after the control events are handled.Use this event for tasks that require that all other controls on the page be loaded.|                                                                                                                                        
| PreRender                                                     | This event occurs before the rendering stage of the page.This event takes place before saving ViewState, so any changes made here are saved.|                                                                                                                                         
| PreRenderComplete                                             | This event occurs immediately after the prerender event.                                            |                                                                                                                                           
| Unload                                                        | This event occurs for each control and then for the page. At this stage the page is unloaded from memory.|        
### Example 
**WebForm1.aspx**<br />
```C#

 <form id="form1" runat="server">
            <div>
            <asp:Label ID="Label1" runat="server" Text="Label"></asp:Label><br />
            </div>
 </form>
 
 ```` 
 **WebForm1.aspx.cs**<br />
 
```C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

namespace PageLifeCycle
{
    public partial class PageLifeCycleEvents : System.Web.UI.Page
    {
        protected void Page_PreInit(object sender, EventArgs e)
        {
            Label1.Text = Label1.Text + "<br/>" + "PreInit";
        }
        protected void Page_Init(object sender, EventArgs e)
        {
            Label1.Text = Label1.Text + "<br/>" + "Init";
        }
        protected void Page_InitComplete(object sender, EventArgs e)
        {
            Label1.Text = Label1.Text + "<br/>" + "InitComplete";
        }
        protected override void OnPreLoad(EventArgs e)
        {
            Label1.Text = Label1.Text + "<br/>" + "PreLoad";
        }
        protected void Page_Load(object sender, EventArgs e)
        {
            Label1.Text = Label1.Text + "<br/>" + "Load";
        }
        protected void btnSubmit_Click(object sender, EventArgs e)
        {
            TextBox1.Text = TextBox1.Text + "<br/>" + "btnSubmit_Click";
        }
        protected void Page_LoadComplete(object sender, EventArgs e)
        {
            Label1.Text = Label1.Text + "<br/>" + "LoadComplete";
        }
        protected override void OnPreRender(EventArgs e)
        {
            Label1.Text = Label1.Text + "<br/>" + "PreRender";
        }
        protected override void OnSaveStateComplete(EventArgs e)
        {
            Label1.Text = Label1.Text + "<br/>" + "SaveStateComplete";
        }
        protected void Page_UnLoad(object sender, EventArgs e)
        {
            Label1.Text = Label1.Text + "<br/>" + "UnLoad";
        }
    }
}                                                                                                                                   
```
