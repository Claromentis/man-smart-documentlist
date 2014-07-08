# Documents Component and Smart Object

======================
Displays a list of documents from a given Folder ID.


## Installation

### Component
This method is used when you need to display a document inside Claromentis, it is rendered on the server-side by Claromentis' PHP template engine.

    <component class="DocsSmartComponent" name="component1">

*Note: You can see a component example after the Parameters section below*

### Smart Object
The alternative to Components, a Smart Object allows you to display the document list using client-side code which can be placed on any page, even pages outside of Claromentis.

If using smart objects outside of Claromentis, it's important to remember that permissions will need to be given to guest users.

This method inserts an iframe into the page at the same location where the javascript file 'show_smartdocuments.js' is included.

    <script type="text/javascript">
    <!—
      var smart_docs_list = {
        name    : 'test_object',
        width   : 800,
        height  : 300,
        columns : 'title,owner'
      };
    //-->
    </script>
 
    <script type="text/javascript" src="/intranet/documents/show_smartdocuments.js"></script>
    
*Note: You can see a smart object example after the Parameters section below*

## Parameters
Note that parameters have a default value so any of them can be ommitted.

**name** : The object name which must be unique for all components on the page. It's also strongle recommended that it is unique for the whole system as PHP session variables are distinguished by this object name.

**width** : Frame width in pixels. (Default: 1000).

**height** : Frame height in pixels. (Default: 400).

**scrolling** : Frame scrolling. (Default: auto. *Options*: auto, yes, no).

**columns** : Define which columns to display as a comma delimited list: icon_info,title,description,owner,size.

**folder_id** : ID of the folder to show the content of (Default: 0 = root)

**show_subfolder** : Show subfolders or not (Default: 1. *Options*: 1 or 0).

**show_documents** : (Default: 1. *Options*: 1 or 0).

**show_tree** : Show the document tree (Default: 1. *Options*: 1 or 0).

**show_headers** : Show column headers for the documents list (Default: 1. *Options*: 1 or 0).

**link_new_window** : Open links in new window (Default: 1. *Options*: 1 or 0).

**page_size** : Number of documents to display per page. Use –1 to show all documents.

**show_trace_path** : show trace path or not (Default: 1. *Options*: 1 or 0)

**sort** : Column to sort by (Default: date_last_modified, title, owner).

**sort_dir** : Sorting direction (Default: desc, asc).

**use_iframe** : Is used only for templater component. If set to 1, templater generates JS-code (given above), which creates iframe and loads documents list in it. If set to 0 - templater produces html-code of documents list framed by DIV.

**truncation_length** : How long a file or folder name can be before it trimmed for display. This number does not include the '…' characters which will follow a trimmed string. The default if left out is 37 which matches the behaviour before this parameter was introduced.

### CSS Styles
These allow you to add a class to the main table, pagination container and trace path

**css_file** : (Default: '/interface_default/common/style.css')

**css_main_table** : (Default: 'table_docs')

**css_paging_table** : (Default: 'table_options')

**css_trace_path** : (Defaults: 'plain_text')

## Examples

### Component

A simple component example, in this case we're not displaying the document tree but are displaying common fields such as the icon, title and last modified date.

    <component class="DocsSmartComponent"
      name="docs_list_1"
      use_iframe="0"
      width="300"
      height="400"
      scrolling = "no"
      columns = "icon_info,title,date_last_modified"
      folder_id="0"
      show_subfolders="1"
      show_documents="1"
      show_tree="0"
      show_headers="0"
      link_new_window="1"
      page_size="5"
      show_trace_path="0"
      sort="date_last_modified"
      sort_dir="desc"
      css_main_table="table_docs"
      css_paging_table="table_options"
      css_trace_path="plain_text" />

### Smart Object

Usage example:

    <script type="text/javascript">
    <!--
    var smart_docs_list = {
      name              : 'test_obj',
      width             : 1000,
      height            : 400,
      scrolling         : "auto",
      columns           : "icon_info,title,description,owner,size",
      folder_id         : 0,
      page_size         : 10,
      sort              : "title",
      sort_dir          : "desc",
      css_paging_table  : "pagination",
      css_file          : "http://host.domain/interface_default/common/style.css"
      truncation_length : 50
    }
    //-->
    </script>
 
    <script type="text/javascript" src="/intranet/documents/show_smartdocuments.js"></script>

## Change Log
0.1 -- 8 July 2014

 * Initial commit based on the original article at : http://dev.claromentis.com/wiki/configuration_and_customization:smart_objects:documents_list



