 # Introduction
 <html>
<body>
 
# XListComponent📝
<!--StartFragment--><p><strong>The XListComponent is utilized in our project to dynamically render and manage lists within various components. It</strong> is typically used in child components to display data in a tabular format.</p>
<h2>🛠️Code Structure:</h2>
<pre><code class="language-jsx">this.component = XListEditComponent;

this.injector = Injector.create({

providers: [

{

provide: XListParamProvider,

useValue: new XListParam(this.xListInput),

},

],

parent: this.inj,

});
</code></pre>
<ul>
<li>
<p>The <code>this.component</code> assignment sets the component type to , indicating that this is the component to be rendered.</p>
<p>XListEditComponent</p>
</li>
<li>
<p><strong>Injector Creation</strong>: An <code>Injector</code> instance is created to provide dependencies for the</p>
<p>XListEditComponent.</p>
</li>
<li>
<p>Providers: A provider is defined to supply an instance of</p>
<p>XListParamProvider.</p>
</li>
<li>
<p>XListParamProvider:

An abstract class used as a base for providing list parameters in the component. It holds the<code>xListInput</code> object, which contains configuration and data for list management.</p>
</li>
<li>
<p>XListParam:

A concrete class extending<code>XListParamProvider</code>. It provides a specific implementation of the <code>XListParamProvider</code> service, initialized with <code>xListInput</code>. This class is used to pass list configuration to the component.</p>
</li>
<li>
<p>xListInput:  An interface defining the structure and properties required for list management, including entity details, list items, and various settings. It is used to configure the list and control its behavior in the component.</p>
</li>
</ul>
<h2>🛠️Properties of xListInput:</h2>
 
Property | Type | Function

-- | -- | --

entityName | string | Specifies the entity the component will interact with. It is used to determine the appropriate backend API endpoints for data fetching.

items | any[] | Array of data objects representing the rows in the list. Each object in the array is a row, with its structure defined by the columns and properties configured in the component.

parentEntity | string | Specifies the entity name of the parent item.

parentId | string | Holds the identifier of the parent item.

parentPageMode | PageMode | Specifies the mode of the parent page, which can be 'create', 'update', or 'read'.

parentItem | any | Holds the entire parent item object.

parentProp | any | - -

onInit | (instance: any) => void | A callback function that is executed when the component is initialized. It provides access to the component instance, allowing for custom initialization logic.

init | (instance: any) => void | - -

save | (items: any[]) => void | - -

onListChange | () => void | A callback function that is triggered when there is a change in the list data. It allows for custom logic to be executed in response to modifications in the list, such as updating data, filtering items, or adjusting UI elements based on the new state of the list.

detailsComp | Type<any> | Specifies a component used for displaying the editable or action-oriented view of an entity. This component allows users to modify, edit, or perform actions related to the entity.

header | TemplateRef<any> | - -

replaceListTpl | TemplateRef<any> | - -

replaceHeaderTpl | TemplateRef<any> | - -

listMode | boolean | - -

columns | Property[] | Defines an array of Property objects that specify additional configurations and customizations for each property of the entity to be displayed as a column. This includes specifying custom templates (cellTemplate), custom names (name), and other configurations like hiding columns (hidden).

disableActiveFilter | boolean | Determines whether the active filter functionality is disabled. When set to true, the active filter will be disabled.

paginator | boolean | Enables pagination in the UI. When set to true, a paginator is displayed, allowing users to navigate through multiple pages of data.

paginatorright | TemplateRef<any> | Template reference for custom pagination controls placed on the right side of the paginator. This allows for the inclusion of additional buttons or controls, such as "Save" or "Cancel", to be displayed alongside the paginator.

nextBtnText | string | Defines the text to be displayed on the "Next" button. This property customizes the button's label.

isDialogEdit | boolean | - -

  |   |  
 
 
## Output:
 
The `XListComponent` is a crucial component designed to facilitate the display and management of a list of items within a table format. In the context of the Agent Mapping page, it allows users to view and manage agent-related data efficiently.
 
 
![XListEditComponent](../Images/Xlist.png)
 
1. **Data Display:** The component organizes and displays agent mapping records, such as agent names, countries, and ports, in a structured table, enhancing data accessibility and readability.

2. **Actions:** Users can perform actions like editing and viewing details for each agent directly within the table, improving interactivity and usability.

3. **Filtering and Sorting:** The component supports filtering and sorting of records based on various columns, enabling users to easily navigate and find specific data.

4. **Pagination:** The component includes pagination controls, allowing users to efficiently browse through large sets of records.
 
In this particular implementation, the `XListComponent` is integrated into the parent component managing the Agent Mapping page. It provides a user-friendly interface for maintaining agent-related data, ensuring that users can efficiently view, edit, and manage this information.
 