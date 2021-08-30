|                 Page Life Cycle Events                        |                        Description                                                                             |                                         
|---------------------------------------------------------------|---------------------------------------------------------------------------------------------------- |
| PreInit                                                       | This event happens just before page initialisation event starts .Is postback, Is callback and Is cross page postback properties are set at this stage.this event allows us to set the master page andtheme of webapplication dynamically.|
| Init                                                          | page init, event occurs after the init event of all the individual controls on the web form.Use this event to read or initialize control properties. the server controls are loaded and initialized from the web forms viewstate.|                                                      |
| InitComplete                                                  | This event occurs immediately after page initialization.                                            |                                                                                                                                          
| PreLoad                                                       | This event occurs just before the page load event.                                                  |                                                                                                                                           
| Load                                                          | page load event occurs before the load event of all individual controls on that web form            |                                                                                                                                          
| Control Events                                                | After the page load event the control events like on button click, dropdown list events are raised  |                                                                                                                                         
| Load Complete                                                 | This event occurs after the control events are handled.                                             |                                                                                                                                        
| PreRender                                                     | This event occurs before the rendering stage of the page.                                           |                                                                                                                                         
| PreRenderComplete                                             | This event occurs immediately after the prerender event.                                            |                                                                                                                                           
| Unload                                                        | This event occurs for each control and then for the page. At this stage the page is unloaded from memory.|        
### Example 

```C#

 <form id="form1" runat="server">
            <div>
            <asp:Label ID="Label1" runat="server" Text="Label"></asp:Label><br />
            </div>
 </form>
 
 ````       

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
            //Work and It will assign the values to label.  
            Label1.Text = Label1.Text + "<br/>" + "PreInit";
        }
        protected void Page_Init(object sender, EventArgs e)
        {
            //Work and It will assign the values to label.  
            Label1.Text = Label1.Text + "<br/>" + "Init";
        }
        protected void Page_InitComplete(object sender, EventArgs e)
        {
            //Work and It will assign the values to label.  
            Label1.Text = Label1.Text + "<br/>" + "InitComplete";
        }
        protected override void OnPreLoad(EventArgs e)
        {
            //Work and It will assign the values to label.  
            //If the page is post back, then label contrl values will be loaded from view state.  
            //E.g: If you string str = lblName.Text, then str will contain viewstate values.  
            Label1.Text = Label1.Text + "<br/>" + "PreLoad";
        }
        protected void Page_Load(object sender, EventArgs e)
        {
            //Work and It will assign the values to label.  
            Label1.Text = Label1.Text + "<br/>" + "Load";
        }
        protected void btnSubmit_Click(object sender, EventArgs e)
        {
            //Work and It will assign the values to label.  
            TextBox1.Text = TextBox1.Text + "<br/>" + "btnSubmit_Click";
        }
        protected void Page_LoadComplete(object sender, EventArgs e)
        {
            //Work and It will assign the values to label.  
            Label1.Text = Label1.Text + "<br/>" + "LoadComplete";
        }
        protected override void OnPreRender(EventArgs e)
        {
            //Work and It will assign the values to label.  
            Label1.Text = Label1.Text + "<br/>" + "PreRender";
        }
        protected override void OnSaveStateComplete(EventArgs e)
        {
            //Work and It will assign the values to label.  
            //But "SaveStateComplete" values will not be available during post back. i.e. View state.  
            Label1.Text = Label1.Text + "<br/>" + "SaveStateComplete";
        }
        protected void Page_UnLoad(object sender, EventArgs e)
        {
            //Work and it will not effect label contrl, view stae and post back data.  
            Label1.Text = Label1.Text + "<br/>" + "UnLoad";
        }
    }
}                                                                                                                                   
```
