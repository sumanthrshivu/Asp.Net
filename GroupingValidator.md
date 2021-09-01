 # Gruping validation in Asp.Net
 
 ```C#
 <form id="form1" runat="server">
        <div>
            Firt Name: <asp:TextBox ID="txtOne" runat="server"></asp:TextBox>
                <asp:RequiredFieldValidator ID="RequiredFieldValidator1" runat="server" ControlToValidate="txtOne" ErrorMessage="Required" ValidationGroup="One"></asp:RequiredFieldValidator>

            Last Name: <asp:TextBox ID="txtTwo" runat="server"></asp:TextBox>
                <asp:RequiredFieldValidator ID="RequiredFieldValidator2" runat="server" ControlToValidate="txtTwo" ErrorMessage="Required" ValidationGroup="One"></asp:RequiredFieldValidator>

                <asp:Button ID="Button1" runat="server" Text="groupone" ValidationGroup="One" /><br /><br />
                  
            Designation: <asp:TextBox ID="TextBox1" runat="server"></asp:TextBox>
                <asp:RequiredFieldValidator ID="RequiredFieldValidator3" runat="server" ControlToValidate="TextBox1" ErrorMessage="Required" ValidationGroup="two"></asp:RequiredFieldValidator>

            place: <asp:TextBox ID="TextBox2" runat="server"></asp:TextBox>
                <asp:RequiredFieldValidator ID="RequiredFieldValidator4" runat="server" ControlToValidate="TextBox2" ErrorMessage="Required" ValidationGroup="two"></asp:RequiredFieldValidator>

                <asp:Button ID="Button2" runat="server" Text="grouptwo" ValidationGroup="two" /><br /><br />
    </div>
 </form> 
