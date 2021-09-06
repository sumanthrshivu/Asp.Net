# Data Binding  in Asp.Net 
* Data binding is the process of retrieving data from a source and dynamically associating it to a property of a visual element.<br/>
## There are two types of data binding
* Simple Data Binding
* Declarative Data Binding.
### Simple Data Binding
* Simple data binding involves the read-only selection lists. These controls can bind to an array list or fields from a database.
* Selection lists takes two values from the database or the data source; one value is displayed by the list and the other is considered as the value corresponding to the display.
### The controls capable of simple data binding are derived from the ListControl abstract class and these controls are:
* BulletedList
* CheckBoxList
* DropDownList
* ListBox
* RadioButtonList
##  Declarative Data Binding.
* controls can bind records, lists, or columns of data into their structure through a DataSource control. These controls derive from the BaseDataBoundControl class. This is called declarative data binding.
### List of controls in Declarative Data Binding
1) ListView
2) Gridview
3) FormView
4) DataPager
5) Repeater

## 1) ListView
   * Listview enables to bind to data items that are returned from a data source and display.
   * The items can be displayed individually or as a group.
   * User can edit insert and delete data using listview.

## 2) Gridview
   * Gridview is a control in asp.net, displays the values of a data source( sql server database) in a tabular format.
   * GridView shows multiple records at once .
   * Each column represents  a field and each row represents a record. 
   * The GridView control also, enables you to select, sort, and edit these items.

## 3) FormView
   * The FormView control is used to display a single record at a time from a data source.
   * It will not show data in tabular format.
   * selecting editing and deleting data can be done using formview .
## 4) Repeater
   * The Repeater control is used to display a repeated list of items that are bound to the control. 
   * The Repeater control may be bound to a database table, an XML file, or another list of items.

## 5) DataPager
   * DataPager Allows paging through data in listview control.
   * Data pager can be put inside or outside of listview control.


     
