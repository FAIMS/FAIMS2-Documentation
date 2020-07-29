FAIMS Mobile Platform Documentation (FAIMS): FAIMS Data, UI and Logic Cook-Book
===============================================================================

::: {style="font-size:70%; color:#444; font-style: italic"}
Created: Former user (Deleted) () - 2013-08-19T17:56:17.479Z

Last Updated: Brian Ballsun-Stanton (brian\@faims.edu.au) -
2019-05-06T05:27:56.333Z
:::

<div>

FAIMS Data, UI and Logic Cook-Book {#FAIMSData,UIandLogicCook-Book-FAIMSData,UIandLogicCook-Book}
==================================

Use this guide to help create your own modules by following the examples
below.

\

::: {.toc-macro .client-side-toc-macro .conf-macro .output-block data-numberedoutline="true" data-headerelements="H1,H2,H3,H4,H5,H6,H7" data-hasbody="false" data-macro-name="toc" data-macro-id="47760a17-2c86-41c9-8c3d-57adb7609bc5"}
:::

Module Creation {#FAIMSData,UIandLogicCook-Book-ModuleCreation}
===============

When creating module there are some files that are needed to create the
module such as:

1.  data schema
2.  ui schema
3.  ui logic

In addition there are some optional files such as:

1.  properties file (or multiple properties files)
2.  validation schema
3.  android style css

Below is the example of a creation for simple module by providing
required files

### Simple Module {#FAIMSData,UIandLogicCook-Book-SimpleModule}

This is an example of a simple module that renders a single text view

**data\_schema.xml**

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="9ea872b0-ca68-40f4-81ea-55b3b843dde6"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<?xml version="1.0" ?>
<?xml-stylesheet type="text/xsl" href="data_schema.xsl"?>
<dataSchema name="SimpleModule" preparer="Your Name">
</dataSchema>
```
:::
:::

**ui\_schema.xml**

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="179c38f0-709f-4bcb-a2db-a3d145c47ba6"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<h:html xmlns="http://www.w3.org/2002/xforms"
        xmlns:h="http://www.w3.org/1999/xhtml"
        xmlns:ev="http://www.w3.org/2001/xml-events"
        xmlns:xsd="http://www.w3.org/2001/XMLSchema"
        xmlns:jr="http://openrosa.org/javarosa">
  <h:head>
    <h:title>Simple Example</h:title>

    <model>
      <instance>
        <faims id="simple_example">
          <tabgroup1>
             <tab1>g
               <text></text>
             </tab1>
          </tabgroup1>
        </faims>
      </instance>
      <bind nodeset="/faims/tabgroup1/tab1/text" type="string"/>
    </model>
  </h:head>

  <h:body>
    <group ref="tabgroup1">
      <label></label>
      <group ref="tab1">
         <label>{tab_name}</label>
         <input ref="text">
            <label>Text:</label>
         </input>
      </group>
    </group>
  </h:body>
</h:html>
```
:::
:::

**ui\_logic.bsh**

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="799268a8-7a29-43b6-bf4b-84944b9807c5"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
setFieldValue("tabgroup1/tab1/text", "Hello World!");
```
:::
:::

### How it works {#FAIMSData,UIandLogicCook-Book-Howitworks}

-   Use the module files to create a module on the server. Then download
    the module onto the android app.
-   The data\_schema.xml specifies what archaeological entities and
    relationships to store. This data schema is empty as we are not
    saving any data at the moment.
-   The ui\_schema.xml specifies how the ui should render. More
    information on how to construct these will be provided in later
    examples. Currently this specifies a single tabgroup, a single tab
    and a single text view.
-   The ui\_logic.bsh specifies how ui elements interact on screen and
    with the database. Current this example simply sets the value of the
    text view to \"Hello World!\".

### Data Schema Construction {#FAIMSData,UIandLogicCook-Book-DataSchemaConstruction}

This section will explain about the structure of the data schema. An
example of data schema:

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="3c8a0ea8-4403-445f-ae89-c33461c5665d"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<?xml version="1.0" ?>
<?xml-stylesheet type="text/xsl" href="sampleDataXML.xsl"?>
<dataSchema name="SyncExample" preparer="Nobody">
    
   <RelationshipElement name="AboveBelow" type="hierarchy">
    <description>
      Indicates that one element is above or below another element.
    </description>
    <parent>
      Above
    </parent>
    <child>
      Below
    </child>
    <property type="string" name="relationship" isIdentifier="true">
    </property>
     <property type="string" name="name">
    </property>
    <property type="dropdown" name="location">
      <lookup>
        <term>Location A</term>
        <term>Location B</term>
        <term>Location C</term>
        <term>Location D</term>
      </lookup>
    </property>
  </RelationshipElement>
  
  <ArchaeologicalElement name="small">
    <description>
      An small entity
    </description>
    <property type="string" name="entity" isIdentifier="true">
    </property>
    <property type="string" name="name">
    </property>
    <property type="integer" name="value">
    </property>
    <property type="file" name="filename">
    </property>
    <property type="file" name="picture">
    </property>
    <property type="file" name="video">
    </property>
    <property type="file" name="audio">
    </property>
    <property type="timestamp" name="timestamp">
    </property>
    <property type="dropdown" name="location">
      <lookup>
        <term>Location A</term>
        <term>Location B</term>
        <term>Location C</term>
        <term>Location D</term>
      </lookup>
    </property>
  </ArchaeologicalElement>  
</dataSchema>
```
:::
:::

There are 2 types of elements for the data schema namely
RelationshipElement and ArchaeologicalElement. Relationship element
defines the schema of a relationship while archaeological element
defines the schema of a archaeological entity.

### Relationship Element {#FAIMSData,UIandLogicCook-Book-RelationshipElement}

A relationship element has both name and type attributes. Type states
the nature of the relationship of which there are three which are
hierarchy, bidirectional and container. There are also child elements
contained in a relationship element:

1.  description: describes the relationship element
2.  parent: defines the verb for the parent entity
3.  child: defines the verb for the child entity
4.  property: a data attribute of a relationship; properties have both
    name and type attributes:

-   -   bundle: ?
    -   lookup: list vocabulary terms for the property

### Archaeological Element {#FAIMSData,UIandLogicCook-Book-ArchaeologicalElement}

An archaeological element has a type attribute. There are also child
elements contained in a archaeological element:

1.  description: the description of the archaeological element
2.  property: a data attribute of the archaeological entity; properties
    have both name and type attributes:

-   -   bundle: ?
    -   lookup: list vocabulary terms for the property

Static UI {#FAIMSData,UIandLogicCook-Book-StaticUI}
---------

The following examples of UI elements demonstrate how these UI elements
(known as views) can be statically embedded within the ui\_schema.xml
file.

### Constructing a UI {#FAIMSData,UIandLogicCook-Book-ConstructingaUI}

This example will teach you how to construct a ui and bind it with
logic.

The faims android apps dynamic ui is comprised of tabgroups, tabs and
views. The full list of supported views are:

-   Text View
-   DropDown
-   Checkbox Group
-   Radiobox Group
-   List View
-   Date Picker
-   Time Picker
-   Map View
-   Picture Gallery
-   Camera Gallery
-   Video Gallery
-   Files List
-   Button
-   Table
-   Web View

### Creating a Text View {#FAIMSData,UIandLogicCook-Book-CreatingaTextView}

The ui\_schema.xml is used to define what to render on screen. There are
two parts to the ui schema. The first part defines the overall structure
of the ui and second part defines the elements on screen to render.

Look at this example ui\_schema.xml where each part is labeled as
comments.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="2312ca80-d1f2-48a5-ad84-17ac6f04c3f6"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<h:html xmlns="http://www.w3.org/2002/xforms"
        xmlns:h="http://www.w3.org/1999/xhtml"
        xmlns:ev="http://www.w3.org/2001/xml-events"
        xmlns:xsd="http://www.w3.org/2001/XMLSchema"
        xmlns:jr="http://openrosa.org/javarosa">
  <h:head>
    <h:title>Simple Example</h:title>

    <model>
      <instance>
        <faims id="simple_example">
          <!-- PART 1: Define ui structure -->
          <tabgroup1>
             <tab1>
               <text></text>
             </tab1>
          </tabgroup1>
        </faims>
      </instance>
      <bind nodeset="/faims/tabgroup1/tab1/text" type="string"/>
    </model>
  </h:head>

  <h:body>
    <!-- PART 2: Define ui elements -->
    <group ref="tabgroup1">
      <label></label>
      <group ref="tab1">
         <label>Tab 1</label>
         <input ref="text">
            <label>Text:</label>
         </input>
      </group>
    </group>
  </h:body>
</h:html>
```
:::
:::

In this example part 1 defines a tabgroup called \"tabgroup1\", a tab
inside the tabgroup called \"tab1\" and a text element inside the tab
called \"text\".

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="cbe9b82e-4e7d-4f37-8e9f-9d39a1f47f72"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
The names for the tabgroup, tab and element can be called anything that
is valid xml.
:::
:::

In the second part it defines how the structure is to be rendered.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="bd760faa-01a9-4ea8-97bc-68c98b0107ea"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<group ref="tabgroup1">
  <label></label>
```
:::
:::

These lines in the xml document define a group element \"tabgroup1\"
(referenced using the ref attribute) which will be used to render it as
a tabgroup. The label is currently not used but is needed to ensure a
valid ui schema.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="5d5005fc-6ac4-4106-8db9-9bc5c355156b"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<group ref="tab1">
  <label>Tab 1</label>
```
:::
:::

These lines in the xml document nested inside the parent group define a
group element \"tab1\" which will be used to rendered it as a tab. The
label is used to label the tab in the ui.

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="5969621e-4ba7-4f66-83fa-823e312ed2a5"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
The faims android app ui must use tabgroups and tabs in this way or else
the app will not recognise the xml as valid. Also be aware that both
group elements define label elements which is a requirement
:::
:::

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="35494caa-85a7-4143-b657-81805925f68a"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<input ref="text">
  <label>Text:</label>
</input>
```
:::
:::

Finally these lines of code define an input element for text. The label
is used to label the text element.

### Creating a Number Text View {#FAIMSData,UIandLogicCook-Book-CreatingaNumberTextView}

Following from the previous example the example below defines an
additional text view \"number\" that is of decimal format.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="22daff5b-d0c2-4413-817d-0fcc6946ea19"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
        <faims id="simple_example">
          <!-- PART 1: Define ui structure -->
          <tabgroup1>
             <tab1>
               <text></text>
               <number></number>
             </tab1>
          </tabgroup1>
        </faims>
      </instance>
      <bind nodeset="/faims/tabgroup1/tab1/text" type="string"/>
      <bind nodeset="/faims/tabgroup1/tab1/number" type="decimal"/>
...

...
      <group ref="tab1">
         <label>Tab 1</label>
         <input ref="text">
            <label>Text:</label>
         </input>
         <input ref="number">
            <label>Number:</label>
         </input>
      </group>
...
```
:::
:::

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="3c224cfc-d21b-4d61-857e-2b396e79b635"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<bind nodeset="/faims/tabgroup1/tab1/number" type="decimal"/>
```
:::
:::

This line in the ui schema lets the renderer know to render this text
view as a number only text view. Notice that the nodeset value follows
the ordering of the xml elements. This is used to ref number text view
uniquely.

### Creating a Dropdown {#FAIMSData,UIandLogicCook-Book-CreatingaDropdown}

This example creates a drop down.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="5588ea8b-c63d-402f-822b-364f9ec01790"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
        <faims id="simple_example">
          <!-- PART 1: Define ui structure -->
          <tabgroup1>
             <tab1>
               <text></text>
               <number></number>
               <itemList></itemList>
             </tab1>
          </tabgroup1>
        </faims>
      </instance>
      <bind nodeset="/faims/tabgroup1/tab1/text" type="string"/>
      <bind nodeset="/faims/tabgroup1/tab1/number" type="decimal"/>
...

...
      <group ref="tab1">
         <label>Tab 1</label>
         <input ref="text">
            <label>Text:</label>
         </input>
         <input ref="number">
            <label>Number:</label>
         </input>
         <select1 ref="itemList">
            <label>Item List:</label>
            <item>
                <label>Item A</label>
                <value>0</value>
            </item>
            <item>
                <label>Item B</label>
                <value>1</value>
            </item>
            <item>
                <label>Item C</label>
                <value>2</value>
            </item>
            <item>
                <label>Item D</label>
                <value>3</value>
            </item>
         </select1>
      </group>
...
```
:::
:::

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="d596c01a-ab02-47c0-87a8-37a2cb60814f"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<item>
  <label>Item A</label>
  <value>0</value>
</item>
```
:::
:::

These lines in the ui schema define a single item of the dropdown. The
label is the text that shows up in the drop down and value is the value
using logic calls (more on that later).

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="60c8316d-6faf-413c-9336-c87f954ae1f0"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Drop downs or any list views must include at least 1 item in ui schema
even if later in ui logic you remove them.
:::
:::

### Creating a Checkbox Group {#FAIMSData,UIandLogicCook-Book-CreatingaCheckboxGroup}

This example creates a checkbox group.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="013c4fe7-011f-4968-b250-9c4dab5bfe45"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
         <select ref="itemList">
            <label>Item List:</label>
            <item>
                <label>Item A</label>
                <value>0</value>
            </item>
            <item>
                <label>Item B</label>
                <value>1</value>
            </item>
            <item>
                <label>Item C</label>
                <value>2</value>
            </item>
            <item>
                <label>Item D</label>
                <value>3</value>
            </item>
         </select>
...
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="ff3cb1ec-8632-42f6-a525-41f8f5f70db4"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Notice that select is used instead of select1.
:::
:::

### Creating a RadioButton Group {#FAIMSData,UIandLogicCook-Book-CreatingaRadioButtonGroup}

This example creates a radio button group.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="c174c753-4107-4297-9d0f-f394246d5082"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
         <select1 ref="itemList" appearance="full">
            <label>Item List:</label>
            <item>
                <label>Item A</label>
                <value>0</value>
            </item>
            <item>
                <label>Item B</label>
                <value>1</value>
            </item>
            <item>
                <label>Item C</label>
                <value>2</value>
            </item>
            <item>
                <label>Item D</label>
                <value>3</value>
            </item>
         </select1>
...
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="be8ebc8d-64de-493b-b946-f8d7f4573e8f"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Notice that the select1 has appearance set to full.
:::
:::

### Creating a List View {#FAIMSData,UIandLogicCook-Book-CreatingaListView}

This example creates a list view.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="e995f806-035f-4351-b7fe-971f9898a25b"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
     <group ref="tab1" faims_scrollable="false">
       <label>Tab 1</label>
...
         <select1 ref="itemList" appearance="compact">
            <label>Item List:</label>
            <item>
                <label>Item A</label>
                <value>0</value>
            </item>
            <item>
                <label>Item B</label>
                <value>1</value>
            </item>
            <item>
                <label>Item C</label>
                <value>2</value>
            </item>
            <item>
                <label>Item D</label>
                <value>3</value>
            </item>
         </select1>
...
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="89494151-7249-4d31-ae4e-e4d9e5878069"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Notice that the select1 has appearance set to compact.
:::
:::

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="9797f495-65a2-4f36-8c68-1203930a0b41"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<group ref="tab1" faims_scrollable="false">
 <label>Tab 1</label>
```
:::
:::

Since list are scrollable views they cannot be placed into normal tabs
as tabs themselves are scrollable. Therefore you set tabs to not scroll
by using the faims\_scrollable attribute to make a tab not scroll.

### Creating a Date Picker {#FAIMSData,UIandLogicCook-Book-CreatingaDatePicker}

This example creates a date picker.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="01693bba-b5cd-4640-a15b-1c37f8f8a1b9"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
        <faims id="simple_example">
          <!-- PART 1: Define ui structure -->
          <tabgroup1>
             <tab1>
               <date>
             </tab1>
          </tabgroup1>
        </faims>
      </instance>
      <bind nodeset="/faims/tabgroup1/tab1/date" type="date"/>
...

...
      <group ref="tab1">
         <label>Tab 1</label>
         <input ref="date">
            <label>Date:</label>
         </input>
      </group>
...
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="3c83d27a-cd7e-4b4c-814a-17afeab5afcb"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Notice the binding of date to type date.
:::
:::

### Creating a Time Picker {#FAIMSData,UIandLogicCook-Book-CreatingaTimePicker}

This example creates a time picker.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="c7976972-92ad-444c-ab09-ed26fe2fb691"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
        <faims id="simple_example">
          <!-- PART 1: Define ui structure -->
          <tabgroup1>
             <tab1>
               <time>
             </tab1>
          </tabgroup1>
        </faims>
      </instance>
      <bind nodeset="/faims/tabgroup1/tab1/time" type="time"/>
...

...
      <group ref="tab1">
         <label>Tab 1</label>
         <input ref="time">
            <label>Time:</label>
         </input>
      </group>
...
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="05547ab1-e0a3-4444-a9f2-d2f2f6041c25"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Notice the binding of time to type time.
:::
:::

### Creating a Map View {#FAIMSData,UIandLogicCook-Book-CreatingaMapView}

This example creates a map view.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="ca4e45a4-5b69-4f54-bc38-593c3a1835ef"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
        <faims id="simple_example">
          <!-- PART 1: Define ui structure -->
          <tabgroup1>
             <tab1>
               <map>
             </tab1>
          </tabgroup1>
        </faims>
      </instance>
...

...
      <group ref="tab1">
         <label>Tab 1</label>
         <input ref="map" faims_map="true">
            <label>Map:</label>
         </input>
      </group>
...
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="38d4b405-8591-4f40-8109-85d014ad0516"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Notice set faims\_map to true to make it a map view.
:::
:::

### Creating a Picture Gallery {#FAIMSData,UIandLogicCook-Book-CreatingaPictureGallery}

This example creates a picture gallery.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="1a77cae0-4661-466c-bd3c-6bbe4e7bf926"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
        <faims id="simple_example">
          <!-- PART 1: Define ui structure -->
          <tabgroup1>
             <tab1>
               <pictures>
             </tab1>
          </tabgroup1>
        </faims>
      </instance>
...

...
      <group ref="tab1">
         <label>Tab 1</label>
         <select1 ref="picture" type="image">
            <label>Picture:</label>
            <item>
                <label>dummy</label>
                <value>dummy</value>
            </item>
        </select1>
      </group>
...
```
:::
:::

### Creating a Camera Gallery {#FAIMSData,UIandLogicCook-Book-CreatingaCameraGallery}

This example creates a camera gallery slider.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="8b72f163-2f3b-4f15-9419-a0bd1c500202"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
        <faims id="simple_example">
          <!-- PART 1: Define ui structure -->
          <tabgroup1>
             <tab1>
               <gallery>
             </tab1>
          </tabgroup1>
        </faims>
      </instance>
...

...
      <group ref="tab1">
         <label>Tab 1</label>
         <select ref="gallery" type="camera">
            <label>Gallery:</label>
            <item>
                <label>dummy</label>
                <value>dummy</value>
            </item>
        </select>
      </group>
...
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="ec8afc1d-03c6-4e1e-b673-6ccd7908dcad"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Notice that the camera and is a select not select1 as the picture
gallery
:::
:::

### Creating a Video Gallery {#FAIMSData,UIandLogicCook-Book-CreatingaVideoGallery}

This example creates a video gallery slider.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="53a1e8ef-0618-4f1d-bfe1-17fbc180b079"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
        <faims id="simple_example">
          <!-- PART 1: Define ui structure -->
          <tabgroup1>
             <tab1>
               <gallery>
             </tab1>
          </tabgroup1>
        </faims>
      </instance>
...

...
      <group ref="tab1">
         <label>Tab 1</label>
         <select ref="gallery" type="video">
            <label>Gallery:</label>
            <item>
                <label>dummy</label>
                <value>dummy</value>
            </item>
        </select>
      </group>
...
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="dbb79d08-aa21-4d45-9624-7d37f2236290"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Notice that the video and is a select not select1 as the picture gallery
:::
:::

### Creating a Files List {#FAIMSData,UIandLogicCook-Book-CreatingaFilesList}

This example creates a files list.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="033acbed-d794-4308-b4b1-24b27008e80b"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
         <select ref="files" type="file">
            <label>Files:</label>
            <item>
                <label>Item A</label>
                <value>0</value>
            </item>
            <item>
                <label>Item B</label>
                <value>1</value>
            </item>
            <item>
                <label>Item C</label>
                <value>2</value>
            </item>
            <item>
                <label>Item D</label>
                <value>3</value>
            </item>
         </select>
...
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="c8ba8bf0-f9d0-475b-ae9b-e1b5a1590906"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Notice that select is used instead of select1.
:::
:::

### Creating a Button {#FAIMSData,UIandLogicCook-Book-CreatingaButton}

This example creates a button.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="68ae7210-0057-4d9a-9a0c-c59e2da9f433"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
        <faims id="simple_example">
          <!-- PART 1: Define ui structure -->
          <tabgroup1>
             <tab1>
               <button />
             </tab1>
          </tabgroup1>
        </faims>
      </instance>
...

...
      <group ref="tab1">
         <label>Tab 1</label>
         <trigger ref="button">
           <label>Click Me</label>
         </trigger>
      </group>
...
```
:::
:::

### Creating a Table {#FAIMSData,UIandLogicCook-Book-CreatingaTable}

This example creates a table.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="58ed1b1c-0efc-4043-9d7d-48199df884f3"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
        <faims id="simple_example">
          <!-- PART 1: Define ui structure -->
          <tabgroup1>
             <tab1>
               <table />
             </tab1>
          </tabgroup1>
        </faims>
      </instance>
...

...
      <group ref="tab1">
         <label>Tab 1</label>
         <input ref="table" faims_table="true">
           <label>Table</label>
         </input>
      </group>
...
```
:::
:::

### Creating a Web View {#FAIMSData,UIandLogicCook-Book-CreatingaWebView}

This example creates a web view

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="81b0bcab-e2c7-473b-8aed-071a7462c2cd"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
        <faims id="simple_example">
          <!-- PART 1: Define ui structure -->
          <tabgroup1>
             <tab1>
               <web />
             </tab1>
          </tabgroup1>
        </faims>
      </instance>
...

...
      <group ref="tab1">
         <label>Tab 1</label>
         <input ref="web" faims_web="true">
           <label>Web Page</label>
         </input>
      </group>
...
```
:::
:::

[\
]{style="color: rgb(255,51,0);"}

Dynamic UI {#FAIMSData,UIandLogicCook-Book-DynamicUI}
----------

The following shows how to create dynamic UI in the module via logic.

::: {.aui-message .hint .shadowed .information-macro}
[\
]{.aui-icon .icon-hint}

::: {.message-content}
Note: Any attributes for dynamic views that are to be autosaved with a
tabgroup need to be present when that tabgroup is first saved. If an
attribute is added after the tab group is first saved, then it won\'t
auto save and will need to be added to the entity attributes each time
saving occurs. To avoid this ensure that all dynamic views are present
when the tabgroup is first saved, or do a manual first save of the
entity with all static and dynamic (view) attributes set to null.
:::
:::

[CreateView]{style="font-size: 16.0px;font-weight: bold;line-height: 1.5;"}

First to make any changes to ui by either creating or removing views you
must first run these commands inside a view task. Then to create a view
you must pass in a view definition object which describe what the view
is and its configuration options.

e.g. below shows how to execute a view task and create a view def with
some options

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="fd2f59fe-831e-4685-b05e-4987e2cc514a"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
executeViewTask(new ViewTask() {
    doTask() {
        viewDef = createViewDef();
        viewDef.createTextField().          // create a textfield
            setLabel("Text1").              // set the label for the view
            setAttributeName("text1").      // set attribute name for the view
            setAttributeType("freetext").   // set the attribute type for the view (freetext, measure, vocab, certainty)
            setAnnotationEnabled(true).     // enable or disable annotation. default is false
            setCertaintyEnabled(true).      // enable or disable certainty. default is false
            setInfoEnabled(true).           // enable or disable info. default is false
            setReadOnly(true).              // enable or disable readonly. default is false. only for textfields
            setStyleCss("input-text")       // add a custom css styling class for the view
            addChoice("opt1", "val1");      // add default options (name, value). only for checkboxes, radiobuttons, dropdowns
        createView("tabgroup1/tab1/text1", viewDef);
    }
});
```
:::
:::

### Create TextField {#FAIMSData,UIandLogicCook-Book-CreateTextField}

Use the following to create a textfield.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="c898a115-624d-450e-b1fe-f9109837ef25"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
// to create a normal textfield  
textDef = createViewDef().createTextField();
// to create integer textfield
textDef = createViewDef().createTextField("integer");
// to create decimal textfield
textDef = createViewDef().createTextField("decimal");
// to create (int) long textfield
textDef = createViewDef().createTextField("long");
// to create text area
textDef = createViewDef().createTextField("string");
...
createView("tabgroup1/tab1/text", textDef);
 
```
:::
:::

### Create DatePicker {#FAIMSData,UIandLogicCook-Book-CreateDatePicker}

Use the following to create a date picker.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="dd567d73-270b-4e5a-9e6b-d99aaf7af389"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
dateDef = createViewDef().createDatePicker();
createView("tabgroup1/tab1/date", dateDef);
```
:::
:::

### Create TimePicker {#FAIMSData,UIandLogicCook-Book-CreateTimePicker}

Use the following to create a time picker.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="912e374a-0cc2-44d5-bce1-faea091def45"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
timeDef = createViewDef().createTimePicker();
createView("tabgroup1/tab1/time", timeDef);
```
:::
:::

### Create Picture Gallery {#FAIMSData,UIandLogicCook-Book-CreatePictureGallery}

Use the following to create a picture gallery.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="630dc70a-0f8d-4c63-bc2d-751c604facdc"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
galleryDef = createViewDef().createPictureGallery();
createView("tabgroup1/tab1/gallery", galleryDef);
```
:::
:::

### Create RadioGroup {#FAIMSData,UIandLogicCook-Book-CreateRadioGroup}

Use the following to create a radio group.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="c20c2c80-1b1e-42cd-99dc-0b7617b7573f"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
radioDef = createViewDef().createRadioGroup();
createView("tabgroup1/tab1/radio", radioDef);
```
:::
:::

### Create DropDown {#FAIMSData,UIandLogicCook-Book-CreateDropDown}

Use the following to create a dropdown.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="c99dafeb-6f9c-411a-be08-7e425b89626d"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
dropDef = createViewDef().createDropDown();
createView("tabgroup1/tab1/drop", dropDef);
```
:::
:::

### Create Checkbox Group {#FAIMSData,UIandLogicCook-Book-CreateCheckboxGroup}

Use the following to create a checkbox group.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="67f9ea1a-314e-4d8a-bb25-dc98b727f716"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
checkDef = createViewDef().createCheckboxGroup();
createView("tabgroup1/tab1/check", checkDef);
```
:::
:::

### Create Camera Gallery {#FAIMSData,UIandLogicCook-Book-CreateCameraGallery}

Use the following to create a camera gallery.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="a10f943b-61db-4f35-a8dc-24b7110378bc"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
cameraDef = createViewDef().createCameraGallery();
createView("tabgroup1/tab1/camera", cameraDef);
```
:::
:::

### Create Video Gallery {#FAIMSData,UIandLogicCook-Book-CreateVideoGallery}

Use the following to create a video gallery.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="8c302f00-ef59-4b5b-b7a2-cb38d62779b3"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
videoDef = createViewDef().createVideoGallery();
createView("tabgroup1/tab1/video", videoDef);
```
:::
:::

### Create File Group {#FAIMSData,UIandLogicCook-Book-CreateFileGroup}

Use the following to create a file group.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="419b2907-60e6-4b65-a5c8-9d701c1ac084"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
fileDef = createViewDef().createFileGroup();
createView("tabgroup1/tab1/file", fileDef);
```
:::
:::

### Create Button {#FAIMSData,UIandLogicCook-Book-CreateButton}

Use the following to create a button.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="89f8ef15-4966-431c-8b1f-f7f37b0d694e"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
buttonDef = createViewDef().createButton();
createView("tabgroup1/tab1/button", buttonDef);
```
:::
:::

### Create List {#FAIMSData,UIandLogicCook-Book-CreateList}

Use the following to create a list.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="73024732-4c1a-40cd-baeb-e4ec66077a8c"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
listDef = createViewDef().createList();
createView("tabgroup1/tab1/list", listDef);
```
:::
:::

### Create Map {#FAIMSData,UIandLogicCook-Book-CreateMap}

Use the following to create a map.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="3e490371-ce87-4b7e-8274-0c8f69ce9968"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
mapDef = createViewDef().createMap();
createView("tabgroup1/tab1/list", mapDef);
```
:::
:::

### Create Table {#FAIMSData,UIandLogicCook-Book-CreateTable}

Use the following to create a table.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="bb6e4a79-cc46-4966-a290-8e2eab77e7e4"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
tableDef = createViewDef().createTable();
createView("tabgroup1/tab1/table", tableDef);
```
:::
:::

### Create Web View {#FAIMSData,UIandLogicCook-Book-CreateWebView}

Use the following to create a web view.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="fe61a981-45f1-4ed9-b4bb-69cdaa0c647b"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
webDef = createViewDef().createWebView();
createView("tablegroup1/tab1/web", webDef);
```
:::
:::

### Create Container {#FAIMSData,UIandLogicCook-Book-CreateContainer}

Containers allow views to be group inside a layout. Use the following to
create a container with styling to group some views together. You can
reference containers just like views using the normal path string.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="924e3514-ee08-4a4e-a65f-f187aee1fad7"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
style1 = "orientation";
style2 = "even";
createContainer("tabgroup1/tab1/container", "orientation");
createContainer("tabgroup1/tab1/sub_container1", "even", "tabgroup1/tab1/container"); // container within another container
createContainer("tabgroup1/tab1/sub_container2", "even", "tabgroup1/tab1/container");
createView("tabgroup1/tab1/text1", createViewDef().createTextField(), "tabgroup1/tab1/sub_container1"); // create view inside sub container 1
createView("tabgroup1/tab1/text2", createViewDef().createTextField(), "tabgroup1/tab1/sub_container2"); // create view inside sub container 2
```
:::
:::

### Remove View {#FAIMSData,UIandLogicCook-Book-RemoveView}

To remove views that have been created dynamically use the following.
Note: you cannot remove views create via the ui schema.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="30845fef-de18-472b-83f9-e587add4bb9a"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
removeView("tabgroup1/tab1/text1");
```
:::
:::

### Remove Container {#FAIMSData,UIandLogicCook-Book-RemoveContainer}

To remove containers that have been created dynamically use the
following. Note: you cannot remove containers created via the ui schema.
Also removing a container does not remove the views inside the container
you will have to remove those views as well.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="7ecd0ecf-c41a-4d04-9588-7b2c6173a232"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
removeContainer("tabgroup1/tab1/container");
```
:::
:::

### Clear All Dynamic Views and Containers {#FAIMSData,UIandLogicCook-Book-ClearAllDynamicViewsandContainers}

To remove all dynamic views and containers in a tab group use the
following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="2d898eb3-8a3b-4bfa-963c-24d211183421"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
removeAllViewsAndContainers("tabgroup1");
```
:::
:::

### Update CSS Styling for a Tab Group {#FAIMSData,UIandLogicCook-Book-UpdateCSSStylingforaTabGroup}

When dynamically creating views you will need to use the following API
call to update styling for the tabgroup and apply any styling to the
newly added views. 

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="557d2cc5-5468-4867-b49f-b5fe43f0fd32"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
refreshTabgroupCSS("tabgroup1");
```
:::
:::

[\
]{style="color: rgb(255,51,0);"}

[Customising the UI]{style="color: rgb(255,51,0);"} {#FAIMSData,UIandLogicCook-Book-CustomisingtheUI}
---------------------------------------------------

Now that you know how to construct the UI here are some examples on how
to customise the ui so you can facilitate automatic loading of data from
the database, hiding tabs, making readonly elements etc

### Hiding labels {#FAIMSData,UIandLogicCook-Book-Hidinglabels}

Labels can be hidden for views by creating an empty label node. You must
include an empty label node for the ui schema to be valid.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="e9679d6d-44c2-45f5-8fa6-d8663783bd08"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
      <input ref="text">
         <label></label>
```
:::
:::

### Tab Scrolling {#FAIMSData,UIandLogicCook-Book-TabScrolling}

Tabs are set to scroll by default but to make them stop scrolling then
set the faims\_scrollable attribute in the tab group element to false.
e.g.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="cf007c0f-5355-4900-bdcb-d2045a08dd13"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
      <group ref="tab1" faims_scrollable="false">
         <label>Tab 1</label>
```
:::
:::

### Hiding Tabs {#FAIMSData,UIandLogicCook-Book-HidingTabs}

To hide tabs when they are first shown you can use the faims\_hidden
attribute to make tabs hidden. By default tabs are visible.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="ff5188b8-18a1-4d8b-a657-26cdf3121159"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<group ref="tab1" faims_hidden="true">
```
:::
:::

### Making Text Views readonly {#FAIMSData,UIandLogicCook-Book-MakingTextViewsreadonly}

Text views can be made readonly by setting faims\_readonly attribute to
true.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="f7ddb1fa-b5b4-4db5-b2fe-d836aad63e28"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
<input ref="text" faims_read_only="true">
  <label>Text:</label>
</input>
...
```
:::
:::

### Binding Tabgroup to Arch Entity {#FAIMSData,UIandLogicCook-Book-BindingTabgrouptoArchEntity}

Binding a TabGroup to an arch entity allows you to do automatic loading
and saving of the entity defined within a TabGroup via the logic script.
To tell which entity type the TabGroup belongs to you can use the
faims\_archent\_type attribute to specify the entity type.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="2114bc6a-64fe-412e-84f1-156098fb76f5"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<group ref="tabgroup1" faims_archent_type="simple">
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="b36c8891-438f-4c96-acc3-3b761ba36518"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
The entity type must match an entity type defined in the data schema.
This will be shown in the saving and loading entities example.
:::
:::

### Binding Tabgroup to Relationship {#FAIMSData,UIandLogicCook-Book-BindingTabgrouptoRelationship}

Binding a TabGroup to a relationship allows you to do automatic loading
and saving of the relationship defined within a TabGroup via the logic
script. To tell which relationship type the TabGroup belongs to you can
use the faims\_rel\_type attribute to specify the entity type.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="24eb35c0-e93b-4702-b52e-051490ecf88b"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<group ref="tabgroup1" faims_rel_type="abovebelow">
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="75914247-f205-4320-9fb2-3866e000030e"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
The relationship type must match an relationship type defined in the
data schema. This will be shown in the saving and loading relationships
example.
:::
:::

### Binding Views to Entity/Relationship Attributes {#FAIMSData,UIandLogicCook-Book-BindingViewstoEntity/RelationshipAttributes}

Once a TabGroup is bound to an entity/relationship type you need to
specify how the views map to the attributes of the entity/relationship.
You can do this by specifying the faims\_attribute\_name and
faims\_attribute\_type.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="99fcce44-f03c-447d-ae3e-c68a27a0e393"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<input ref="text" faims_attribute_name="name" faims_attribute_type="freetext">
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="1727a8c8-e003-475e-aa56-490760ce82e1"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Here text view maps to the name attribute which will store in the
attributes freetext. Attributes for entities have 4 values freetext,
vocab, measure and certainty while attributes for relationships are
freetext, vocab and certainty. More on this in the saving and loading
entities/relationships example.
:::
:::

### Disabling Certainty Buttons on views {#FAIMSData,UIandLogicCook-Book-DisablingCertaintyButtonsonviews}

By default all views in TabGroups that are bound to entities or
relationships show an certainty button. This button allows views to set
certainty values to them. If you want to disable them you can simply set
the faims\_certainty attribute of the view to false.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="a5bf7265-3b45-4529-84c1-0560923dc1bb"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<input ref="text" faims_certainty="false">
```
:::
:::

### Disabling Annotation Buttons on views {#FAIMSData,UIandLogicCook-Book-DisablingAnnotationButtonsonviews}

By default all non-text views in TabGroups that are bound to entities or
relationships show an annotation button. This button allows views to set
annotation values to them. If you want to disable them you can simply
set the faims\_annotation attribute of the view to false.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="ea305b88-307b-4194-8744-0d8a363049b1"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<input ref="text" faims_annotation="false">
```
:::
:::

### Syncing files {#FAIMSData,UIandLogicCook-Book-Syncingfiles}

For view that are bound to attributes that a file type then you can
specify a faims\_sync attribute to indicate if those files are to sync
to the server only or other apps as well.  More on this in the saving
and loading entities/relationships example.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="6d66bdc5-c62a-4c80-aca1-10e2411e6dee"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<select ref="files" type="file" faims_attribute_name="files" faims_attribute_type="freetext" faims_sync="true">
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="4e9cec90-be27-4426-9e81-fb9673f9f5a7"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
A sync attribute must also be added to the data schema. This is for the
webapp side to indicate whether files uploaded on the server should be
synced to devices or not.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="9c974d57-1a4b-4af1-8481-7e95c6c05d93"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<property type="something" name="pictures" file="true" thumbnail="true" sync="true">
  <bundle>DOI</bundle>
</property>
```
:::
:::
:::
:::

### Styling {#FAIMSData,UIandLogicCook-Book-Styling}

The styling can be defined and applied from the ui schema. It needs to
be defined at the top of the tabgroup definition.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="867eed76-a12a-46a8-8361-65ad3e954441"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
    <faims id="simple_example">
        <style>
            <orientation>
                <orientation></orientation>
            </orientation>
            <even>
                <layout_weight></layout_weight>
            </even>
        </style>
        <tabgroup1>
            <tab1>
                <container1>
                    <child1>
                        <name></name>
                        <value></value>
                    </child1>
                    <child2>
                        <timestamp></timestamp>
                        <location></location>
                    </child2>
                </container1>
 
...
 
    <group ref="style">
        <label></label>
        <group ref="orientation">
            <label></label>
            <input ref="orientation">
                <label>horizontal</label>
            </input>
        </group>
        <group ref="even">
            <label></label>
            <input ref="layout_weight">
                <label>1</label>
            </input>
        </group>
    </group>
    <group ref="tabgroup1" faims_archent_type="small">
      <label></label>
      <group ref="tab1" faims_hidden="false">
        <label>Save Entity</label>
        <group ref="container1" faims_style="orientation">
          <label></label>
          <group ref="child1" faims_style="even">
            <label></label>
            <input ref="name" faims_attribute_name="name" faims_attribute_type="freetext">
              <label>Name:</label>
            </input>
            <input ref="value" faims_attribute_name="value" faims_attribute_type="measure">
                <label>Value:</label>
            </input>
          </group>
          <group ref="child2" faims_style="even">
            <label></label>
            <input ref="timestamp" faims_attribute_name="timestamp" faims_attribute_type="freetext" faims_read_only="true" faims_certainty="false">
              <label>Timestamp:</label>
            </input>
            <select ref="location" faims_attribute_name="location" faims_attribute_type="vocab">
                <label>Location:</label>
                <item>
                    <label>dummy</label>
                    <value>dummy</value>
                </item>
            </select>
          </group>
        </group>
```
:::
:::

The example of styling shows that we can define a style for making a
container with certain orientation and certain layout weight to divide
it even. The styling should be applied to the using the attribute
faims\_style to the group tag.

Using Logic {#FAIMSData,UIandLogicCook-Book-UsingLogic}
===========

This section will provide examples on how to the logic file to add
interaction between ui logic and data storage.

### Saving/Loading Arch Entity {#FAIMSData,UIandLogicCook-Book-Saving/LoadingArchEntity}

Define a archaeological entity in the data schema.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="92c2434a-e5fe-42bc-b355-21b9a14e1804"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<?xml version="1.0" ?>
<?xml-stylesheet type="text/xsl" href="data_schema.xsl"?>
<dataSchema name="SimpleModule" preparer="Your Name">
  <ArchaeologicalElement name="Simple">
    <description>
      An simple entity
    </description>
    <property type="string" name="name" isIdentifier="true">
      <bundle>DOI</bundle>
    </property>
    <property type="real" name="value" isIdentifier="true">
      <bundle>DOI</bundle>
    </property>
  </ArchaeologicalElement>
</dataSchema>
```
:::
:::

This data schema defines a single archaeological entity called
\"Simple\" with two properties name and value.

Now we define a ui schema to save this entity.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="64fa2d9f-d218-4280-8201-04f4307393e6"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<h:html xmlns="http://www.w3.org/2002/xforms"
        xmlns:h="http://www.w3.org/1999/xhtml"
        xmlns:ev="http://www.w3.org/2001/xml-events"
        xmlns:xsd="http://www.w3.org/2001/XMLSchema"
        xmlns:jr="http://openrosa.org/javarosa">
  <h:head>
    <h:title>Simple Example</h:title>

    <model>
      <instance>
        <faims id="simple_example">
          <tabgroup1>
             <tab1>
               <name></name>
               <value></value>
               <save></save>
               <clear></clear>
             </tab1>
             <tab2>
               <entity></entity>
               <load></load>
             </tab2>
          </tabgroup1>
        </faims>
      </instance>
      <bind nodeset="/faims/tabgroup1/tab1/name" type="string"/>
      <bind nodeset="/faims/tabgroup1/tab1/value" type="decimal"/>
    </model>
  </h:head>

  <h:body>
    <group ref="tabgroup1" faims_archent_type="Simple">
      <label></label>
      <group ref="tab1">
         <label>Tab 1</label>
         <input ref="name" faims_attribute_name="name" faims_attribute_type="freetext">
            <label>Name:</label>
         </input>
         <input ref="value" faims_attribute_name="value" faims_attribute_type="measure">
            <label>Value:</label>
         </input>
         <trigger ref="save">
           <label>Save</label>
         </trigger>
         <trigger ref="clear">
           <label>Clear</label>
         </trigger>
      </group>
      <group ref="tab2">
         <label>Tab 2</label>
         <select1 ref="entity">
           <label>Entity:</label>
           <item>
             <label>dummy</label>
             <value>dummy</value>
           </item>
         </select1>
         <trigger ref="load">
           <label>Load</label>
         </trigger>
      </group>
    </group>
  </h:body>
</h:html>
```
:::
:::

Now let use the logic to save and load an arch entity to and from the
database.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="108f2ea1-94c8-4469-92dd-29468ee81590"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
// add click events for buttons
onEvent("tabgroup1/tab1/save", "click", "saveEntity()");
onEvent("tabgroup1/tab1/clear", "click", "clearEntity()");
onEvent("tabgroup1/tab2/load", "click", "loadEntity()");

update() {
  fetchAll("select uuid, uuid from archentity where uuid || aenttimestamp in ( select uuid || max(aenttimestamp) from archentity group by uuid having deleted is null);", new FetchCallback() {
    onFetch(result) {
      populateDropDown("tabgroup1/tab2/entity", result);
    }   
  });
}

entity_id = null;
saveEntity() {
  saveTabGroup("tabgroup1", entity_id, null, null, new SaveCallback() {
    onSave(uuid, newRecord) {
      entity_id = uuid;
      showToast("saved entity " + entity_id);
      if(newRecord) {
        showToast("New record created");-
      }
      update();
    }
  });
}

loadEntity() {
  entity_id = getFieldValue("tabgroup1/tab2/entity");
  showTabGroup("tabgroup1", entity_id, new FetchCallback() {
    onFetch(result) {
      entity = result;
      showToast("Loaded entity " + entity.getId());
  });
}

clearEntity() {
  newTabGroup("tabgroup1");
  entity_id = null;
}

update();
```
:::
:::

### How it works {#FAIMSData,UIandLogicCook-Book-Howitworks.1}

-   The data schema has defined a archaeological entity with two
    attributes name and value. These are specified using property
    elements.
-   The ui schema defines a ui with a single tab group and 2 tabs. The
    first tab contains a name text view and a value text view. These are
    mapped to the Simple archaeological element using the
    faims\_arch\_ent\_type attribute and faims\_attribute\_name &
    faims\_attribute\_type attributes.
-   The ui logic now uses the api calls
    provided [here](/wiki/pages/resumedraft.action?draftId=3014726) to
    save the data to the database and load data back from the database.

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="ebfe86b1-733e-4c3c-8b08-4f5f97468592"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Note that the saveTabGroup api call only triggers a save if the value of
one of the TabGroup fields have been changed since that TabGroup was
last saved. To force the TabGroup to save, even if the field values have
not been changed, use the saveArchEnt api call.
:::
:::

\

### Saving/Loading Relationships {#FAIMSData,UIandLogicCook-Book-Saving/LoadingRelationships}

Define a relationship in the data schema.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="55c69f25-f5c5-4181-904b-2f311e970b97"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<?xml version="1.0" ?>
<?xml-stylesheet type="text/xsl" href="data_schema.xsl"?>
<dataSchema name="SimpleModule" preparer="Your Name">
  <RelationshipElement name="AboveBelow" type="hierarchy">
    <description>
      Indicates that one element is above or below another element.
    </description>
    <parent>
      Above
    </parent>
    <child>
      Below
    </child>
     <property type="string" name="name" isIdentifier="true">
      <bundle>DOI</bundle>
    </property>
  </RelationshipElement>
</dataSchema>
```
:::
:::

This data schema defines a single relationship called \"Simple\" with
one attribute called name.

Now we define a ui schema to save this relationship.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="062f9823-5f1f-422a-88d3-6389a423efd0"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<h:html xmlns="http://www.w3.org/2002/xforms"
        xmlns:h="http://www.w3.org/1999/xhtml"
        xmlns:ev="http://www.w3.org/2001/xml-events"
        xmlns:xsd="http://www.w3.org/2001/XMLSchema"
        xmlns:jr="http://openrosa.org/javarosa">
  <h:head>
    <h:title>Simple Example</h:title>

    <model>
      <instance>
        <faims id="simple_example">
          <tabgroup1>
             <tab1>
               <name></name>
               <save></save>
               <clear></clear>
             </tab1>
             <tab2>
               <relationship></relationship>
               <load></load>
             </tab2>
          </tabgroup1>
        </faims>
      </instance>
      <bind nodeset="/faims/tabgroup1/tab1/name" type="string"/>
    </model>
  </h:head>

  <h:body>
    <group ref="tabgroup1" faims_rel_type="AboveBelow">
      <label></label>
      <group ref="tab1">
         <label>Tab 1</label>
         <input ref="name" faims_attribute_name="name" faims_attribute_type="freetext">
            <label>Name:</label>
         </input>
         <trigger ref="save">
           <label>Save</label>
         </trigger>
         <trigger ref="clear">
           <label>Clear</label>
         </trigger>
      </group>
      <group ref="tab2">
         <label>Tab 2</label>
         <select1 ref="relationship">
           <label>Relationship:</label>
           <item>
             <label>dummy</label>
             <value>dummy</value>
           </item>
         </select1>
         <trigger ref="load">
           <label>Load</label>
         </trigger>
      </group>
    </group>
  </h:body>
</h:html>
```
:::
:::

Now let use the logic to save and load relationship to and from the
database.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="05f8dec9-d328-44c9-b062-f847001c731f"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
// add click events for buttons
onEvent("tabgroup1/tab1/save", "click", "saveRelationship()");
onEvent("tabgroup1/tab1/clear", "click", "clearRelationship()");
onEvent("tabgroup1/tab2/load", "click", "loadRelationship()");

update() {
  fetchAll("select relationshipid, relationshipid from relationship where uuid || relntimestamp in ( select relationshipid || max(relntimestamp) from relationship group by relationshipid having deleted is null);", new FetchCallback() {
    onFetch(result) {
      populateDropDown("tabgroup1/tab2/relationship", result);
    }
  });
}

rel_id = null;
saveRelationship() {
  saveTabGroup("tabgroup1", rel_id, null, null, new SaveCallback() {
    onSave(uuid, newRecord) {
      rel_id = uuid;
      showToast("saved relationship " + rel_id);
      update();
    }
  });
}

loadRelationship() {
  rel_id = getFieldValue("tabgroup1/tab2/relationship");
  showTabGroup("tabgroup1", rel_id, new FetchCallback() {
    onFetch(result) {
      rel = result;
      showToast("loaded relationship " + rel.getId());
    }
  });
}

clearRelationship() {
  newTabGroup("tabgroup1");
  rel_id = null;
}

update();
```
:::
:::

### Automated TabGroup Saving {#FAIMSData,UIandLogicCook-Book-AutomatedTabGroupSaving}

With automated saving you don\'t require the users to manually click a
button to call the saveTabGroup api call. You just need to call the
automated saving api once and the TabGroup will automatically save
when inputs are changed or the TabGroup is cleared, hidden or changed.
Automated saving will automatically dismiss when the TabGroup is
cleared, hidden or changed.

Use the following to turn on automated saving.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="4c93488d-13c7-4578-ac0e-63757c103792"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
enable_autosave = true
saveTabGroup("tabgroup1", entity_id, null, null, callback, enable_autosave);
```
:::
:::

### Keep Changes in TabGroup {#FAIMSData,UIandLogicCook-Book-KeepChangesinTabGroup}

With autosaving you might sometimes set default inputs for the fields
your tabgroup and not want to save the tabgroup unless the user makes a
change. To do this you can call the keep changes api so autosave will
ignore the current state of the tabgroup.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="01410b95-f070-4f17-8740-e28eb2cd9d2e"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
keepTabGroupChanges("tabgroup1");
```
:::
:::

### Fetching Entities and Relationships {#FAIMSData,UIandLogicCook-Book-FetchingEntitiesandRelationships}

To load entities manually use the following.

e.g. fetchArchEnt

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="3a43ae8c-aa2f-42df-a0cb-c34617c28cbf"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
fetchArchEnt("10000112441409729", new FetchCallback() {
  onFetch(result) {
    entity = result;
    // useful methods on entity
    id = entity.getId();
    type = entity.getType();
    attributes = entity.getAttributes();
    geometry_list = entity.getGeometryList();
    has_conflict = entity.isForked();
  }
  
  onError(message) {
    showToast(message);
  }
});
```
:::
:::

In the example, the function will return an archaeological entity with
uuid 10000112441409729 if the uuid exists or null.

To load relationships manually use the following.

e.g. fetchRel

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="074c5687-49cc-4dc4-a3b8-12f52011e53d"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
fetchRel("10000112441409730", new FetchCallback() {
  onFetch(result) {
    rel = result;
    // useful methods on relationship
    id = rel.getId();
    type = rel.getType();
    attributes = rel.getAttributes();
    geometry_list = rel.getGeometryList();
    has_conflict = rel.isForked();
  }  

  onError(message) {
    showToast(message);
  }
});
```
:::
:::

In the example, the function will return a relationship with
relationshipid 10000112441409730 if the relationshipid exists or null.

To query the database use the following api.

e.g. fetchOne

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="03479a65-635a-4d00-bd83-b382983a9c72"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
fetchOne("select vocabid, vocabname from vocabulary left join attributekey using (attributeid) where attributename = 'type';", new FetchCallback() {
  onFetch(result) {
    // do something
  }
 
  onError(message) {
    showToast(message);
  }
});
```
:::
:::

FetchOne will only return one row from the query even though the query
may return more than one result.

e.g. fetchAll

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="c3cb83f2-91ff-40d5-878f-b5096a28e0c6"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
fetchAll("select vocabid, vocabname from vocabulary left join attributekey using (attributeid) where attributename = 'type';", new FetchCallback() {
  onFetch(results) {
    // do something
  }
 
  onError(message) {
    showToast(message);
  }
});
```
:::
:::

FetchAll will return all values from the query.

e.g. fetchEntityList

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="0f2fe1fe-f82c-4f35-938d-44d41f0b8d19"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
fetchEntityList("small", new FetchCallback() {
  onFetch(entities) {
    // do something
  }
 
  onError(message) {
    showToast(message);
  }
});
```
:::
:::

This will return a list of entities of a particular type with each row
having the first item equal the id of the entity and the second item
equal the identifier of the entity. This is useful to populate list and
dropdowns etc.

e.g. fetchRelationshipList

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="df2af1db-7f4a-4bfb-925c-ee2d95752a59"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
fetchRelationshipList("abovebelow", new FetchCallback() {
  onFetch(relationships) {
    // do something
  }
 
  onError(message) {
    showToast(message);
  }
});
```
:::
:::

This will return a list of relationships of a particular type with each
row having the first item equal the id of the relationship and the
second item equal the identifier of the relationship. This is useful to
populate list and dropdowns etc.

### Saving Archaeological Entities and Relationships {#FAIMSData,UIandLogicCook-Book-SavingArchaeologicalEntitiesandRelationships}

To save entities manually use the following.

e.g. saveArchEnt

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="fece3380-f825-40fc-a6ae-5aa09d2ddece"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
attributes = createAttributeList();
entityId = null;
name = "name";
text = "some text";
vocab = null;
measure = null;
certainty = null;
geometry = null;
attributes.add(createEntityAttribute(name, text, vocab, measure, certainty));
saveArchEnt(entityId, "small", geometry, attributes, new SaveCallback() {
  onSave(uuid, newRecord) {
    // do something
  }
 
  onError(message) {
    showToast(message);
  }
}); 
```
:::
:::

To save relationships manually use the following.

e.g saveRel

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="2fe047c3-c6ac-4989-ad51-ecc8aa298a7d"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
attributes = null;
relationshipId = null;
name = "name";
text = "some text";
vocab = null;
certainty = null;
geometry = null;
# attributes are deprecated for relationships
# attributes.add(createRelationshipAttribute(name, text, vocab, certainty));
saveRel(relationshipId, "abovebelow", geometry, attributes, new SaveCallback() {
  onSave(uuid, newRecord) {
    // do something
  }
 
  onError(message) {
    showToast(message);
  }
}); 
```
:::
:::

### Deleting Archaeological Entities and Relationships {#FAIMSData,UIandLogicCook-Book-DeletingArchaeologicalEntitiesandRelationships}

There are a couple of apis to delete entities and relationships from the
database.

e.g. deleteArchEnt

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="bf96c9c5-0ccf-4ec0-a98d-fb7ea29599ee"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
deleteArchEnt('10000112441409729', new DeleteCallback() {
  onDelete(uuid) {
    // do something
  }
 
  onError(message) {
    showToast(message);
  }
});
```
:::
:::

This will delete the archaelogical entity with uuid 10000112441409729

e.g. deleteRel

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="1b74b100-074f-4ee8-a472-8a76a97ae792"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
deleteRel('10000112441409730', new DeleteCallback() {
  onDelete(uuid) {
    // do something
  }
 
  onError(message) {
    showToast(message);
  }
});
```
:::
:::

This will delete the relationship with relationshipid 10000112441409730

### Deleting Attributes {#FAIMSData,UIandLogicCook-Book-DeletingAttributes}

To delete a particular attribute of an entity or relationship you can
used the overloaded createEntityAttribute and
createRelationshipAttribute to specifiy that the attributes to be saved
are deleted.

e.g. createEntityAttribute

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="c4be1501-c7cb-4600-8822-aa55a10e668a"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
attribute = createEntityAttribute('name', null, null, null, null, true);
```
:::
:::

This will create an attribute for \'name\' with deleted set to true. Add
this to the attribute list when you save the entity and it will mark the
name attribute as deleted.

e.g. createRelationshipAttribute

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="6497aff6-eb99-4039-94d9-ce393731c0c3"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
attribute = createRelationshipAttribute('name', null, null, null, true);
```
:::
:::

This will create an attribute for \'name\' with deleted set to true. Add
this to the attribute list when you save the relationship and it will
mark the name attribute as deleted.

### Relating Entities {#FAIMSData,UIandLogicCook-Book-RelatingEntities}

To add an existing entity to an existing relationship use the addReln
api.

e.g. addReln

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="3a49bf47-23b4-4f8a-9374-6c5f9147c599"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
addReln('10000112441409729', '10000112441409730', 'Above', new SaveCallbac() {
  onSaveAssociation(entityId, relId) {
    // do something
  }
 
  onError(message) {
    showToast(message);
  }
});
```
:::
:::

This will add entity with uuid 10000112441409729 to relationship with
relationshipid 10000112441409730 with the verb \'Above\'.

### Getting Field Values, Annotations and Certainty {#FAIMSData,UIandLogicCook-Book-GettingFieldValues,AnnotationsandCertainty}

Given the saving and loading examples provided getting field values,
annotations and certainty are done by using the api calls getFieldValue,
getFieldAnnotation and getFieldCertainty.

e.g. getFieldValue

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="f4f34fb5-26c5-4254-aeb4-c140e982f2bb"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
String value = getFieldValue("tabgroup1/tab1/name");

List pairs = getFieldValue("tabgroup1/tab1/pictures");
for (NameValuePair pair : pairs) {
    value = pair.getName();
}
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="9ff7a2bc-8f17-429c-860c-c19b8b271a4f"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
For views like checkbox group, files list, camera picture gallery and
video picture gallery the returned value is not a string but a list of
name value pairs.
:::
:::

e.g. getFieldAnnotation

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="557af65f-dbd8-4e04-9404-9f3ff2bda06f"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
getFieldAnnotation("tabgroup1/tab1/name")
```
:::
:::

e.g. getFieldCertainty

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="3a525f85-1f63-408f-92d8-005cffff25dd"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
getFieldCertainty("tabgroup1/tab1/name")
```
:::
:::

The input string references the view in the ui schema. The path matches
\<tabgroup\>/\<tab\>/\<name\>. For more information on what these
functions do please refer to the api calls
provided [here](https://wiki.intersect.org.au/display/FAIMS/Program+Logic+Support#ProgramLogicSupport-FieldValues){.external-link}.

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="7b1601b9-3220-44f3-ad65-e7c568796bb4"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Note that since not all fields supports certainty and annotation, all
calls to the fields that do not support the certainty and annotation
will result in showing a warning dialog.
:::
:::

### Setting Field Values, Annotations and Certainty {#FAIMSData,UIandLogicCook-Book-SettingFieldValues,AnnotationsandCertainty}

The value of the fields can also be set by using  the logic by calling
setFieldValue, setFieldAnnotation, and setCertainty.

e.g. setFieldValue

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="8d10326a-713e-49f3-a94f-885698aedb82"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
setFieldValue("tabgroup1/tab1/name","value1")

List pairs = new ArrayList();
pairs.add(new NameValuePair("value1", true);
pairs.add(new NameValuePair("value2", false);
setFieldValue("tabgroup1/tab1/pictures, pairs);
```
:::
:::

e.g. setFieldAnnotation

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="ce97f7d4-045e-4d99-a1c0-afecf2da250c"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
setFieldAnnotation("tabgroup1/tab1/name","value1")
```
:::
:::

e.g. setFieldCertainty

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="7d6f3155-ce5c-4c1b-9d4a-07fd31bafcc4"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
setFieldCertainty("tabgroup1/tab1/name","0.5")
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="7516da06-564a-4b01-b656-faa7dbddaa28"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Note that since not all fields supports certainty and annotation, all
calls to the fields that do not support the certainty and annotation
will result in showing a warning dialog.
:::
:::

### Event Handling {#FAIMSData,UIandLogicCook-Book-EventHandling}

Referring to the saving / loading examples provided above adding events
to the ui are done using the following.

e.g. onEvent

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="bd27bb52-483e-4559-94b8-b6406295e02d"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
onEvent("tabgroup1/tab1/save", "click", "saveEntity()");
```
:::
:::

OnEvent supports delayclick, click, load, select and show events. In the
example, it shows that when \"tabgroup1/tab1/save\" is clicked, the
saveEntity will be called. The click event is dispatched when a view is
touched, the load event is dispatched when a tabgroup is first shown,
the select event is dispatched when an item in the view is
selected/changed and the show event is dispatched when everytime a
tabgroup is shown. The delay click is a special click event that will
only be executed every one second.

e.g. onFocus

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="c186466b-ad5b-4818-8238-a21bc98716bd"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
onFocus("tabgroup1/tab1/name","showWarning(\"focus\",\"it is focus\")", "showWarning(\"blur\",\"it is blur\")");
```
:::
:::

OnFocus supports focus and blur events. The example shows that when the
field \"tabgroup1/tab1/name\" is focused, the warning dialog \"focus\"
will appear, meanwhile when it is blurred, the warning dialog \"blur\"
will appear.

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="6b3d9137-e57c-4ef5-9a64-bb9bf8b1e46a"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Note that if the focus callback or blur callback is not defined, the
callback would not be executed.
:::
:::

### Customising the Action Bar Menu {#FAIMSData,UIandLogicCook-Book-CustomisingtheActionBarMenu}

The menu in the action bar at the top right of the app can be customised
with dynamic items. They can be either single ever-present items or
toggle items. Both examples can be seen below:

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="caf5ddb2-5e32-4bb5-bd75-ddac02106eca"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
// standard item
addActionBarItem("about", new ActionButtonCallback() {
    actionOnLabel() {
        "About";
    }
    
    actionOn() {
        showWarning("Test Module", "This module was created merely for test purposes. Use it as you will");
    }
});
 
 
// Toggle item
addActionBarItem("sync", new ToggleActionButtonCallback() {
    actionOnLabel() {
        "Turn Sync off";
    }
    actionOn() {
        setSyncEnabled(false);
    }
    isActionOff() {
        isSyncEnabled();
    }
    actionOffLabel() {
        "Turn Sync on";
    }
    actionOff() {
        setSyncEnabled(true);
    }
});
```
:::
:::

The first example is the standard item and uses an ActionButtonCallback,
which is used to specify the item label and the callback action to be
executed on click.

The second example is the toggle item and uses a
ToggleActionButtonCallback which is used to specify two item labels and
corresponding callback actions as well as a boolean expression to
determine which of the two states to show. In this example, it checks
whether sync is enabled and shows a \"Turn on\" or \"Turn off\" action
item as required

### Customising the Navigation Drawer Menu {#FAIMSData,UIandLogicCook-Book-CustomisingtheNavigationDrawerMenu}

To add custom actions to the navigation drawer use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="c61142a3-7b0d-4f5c-a97c-9ebbbfe982d0"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
// Primary Buttons (blue color)
addNavigationButton("test1", new ActionButtonCallback() {
  actionOnLabel() {
    "{primary.button}";
  }
  actionOn() {
    showToast("{primary.message}");
  }
}, "primary");
// Success Buttons (green color)
addNavigationButton("test2", new ActionButtonCallback() {
  actionOnLabel() {
    "{success.button}";
  }
  actionOn() {
    showToast("{success.message}");
  }
}, "success");
// Danger Buttons (red color)
addNavigationButton("test3", new ActionButtonCallback() {
  actionOnLabel() {
    "{danger.button}";
  }
  actionOn() {
    showToast("{danger.message}");
  }
}, "danger");
// Default Buttons (grey color)
addNavigationButton("test4", new ActionButtonCallback() {
  actionOnLabel() {
    "{default.button}";
  }
  actionOn() {
    showToast("{default.message}");
  }
}, "default");
```
:::
:::

### Alert, Toast, Busy and Warning {#FAIMSData,UIandLogicCook-Book-Alert,Toast,BusyandWarning}

Alert, toast, and warning are useful to show information to the user.

e.g. showAlert

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="5082e9a7-17a9-4f0b-b1fa-30e7ab066d30"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
showAlert("alert", "Do you want to navigate to the next page?", "goToNextPage()", "stayInCurrentPage()")
```
:::
:::

The example shows that show alert could be useful in the scenario of
moving page. The user would see a dialog asking for moving page, when
the user press OK, the goToNextPage() function will be executed while
pressing Cancel will result in calling the stayInCurrentPage() function.
Note that the goToNextPage() and stayInCurrentPage() are not part of api
calls and depends on ui designer to create them.

e.g. showToast

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="6c991bf2-26bf-472d-9758-64e78ff53ee8"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
showToast("Starting GPS")
```
:::
:::

ShowToast is usefull to show a short period toast to the user with
certain message. It does not block the user unlike the alert dialog or
warning dialog.

e.g. showWarning

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="fe664916-8996-4e2c-887c-dba839dbfcb0"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
showWarning("warning","This is a warning")
```
:::
:::

When showWarning is called, a warning dialog will appear and shows the
title and message as specified in the function. The user then needs to
press OK button to dismiss the dialog.

e.g showBusy

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="b501fc3b-6124-4a2d-b47e-bbd7308ec452"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
dialog = showBusy("loading module", "please wait")
...
dialog.dismiss(); // to close the dialog
```
:::
:::

When showBusy is called, a busy dialog will appear and shows the title
and message as specified in the function. The user can only close the
dialog by dismissing it in the logic.

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="cf689c1a-8c81-40ac-8de1-a6330285bcf3"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
::: {.message-content}
Note that by default the busy dialog can be cancelled by user events
such as clicking elsewhere on the screen. To make the dialog
non-cancellable use the following:

::: {.syntaxhighlighter .nogutter .java}
\

::: {.table-wrap}
+-----------------------------------------------------------------------+
| ::: {.container title="Hint: double-click to select code"}            |
| ::: {.line .number1 .index0 .alt2}                                    |
| `dialog = showBusy(`{.java .plain}`"loading module"`{.java            |
| .string}`, `{.java .plain}`"please wait"`{.java .string}`)`{.java     |
| .plain}                                                               |
| :::                                                                   |
|                                                                       |
| ::: {.line .number2 .index1 .alt1}                                    |
| `dialog.setCancelable(`{.java .plain}`false`{.java                    |
| .keyword}`);`{.java .plain}                                           |
| :::                                                                   |
|                                                                       |
| ::: {.line .number3 .index2 .alt2}                                    |
| `...`{.java .plain}                                                   |
| :::                                                                   |
|                                                                       |
| ::: {.line .number4 .index3 .alt1}                                    |
| `dialog.dismiss(); `{.java .plain}`// to close the dialog`{.java      |
| .comments}                                                            |
| :::                                                                   |
| :::                                                                   |
+-----------------------------------------------------------------------+
:::
:::
:::
:::
:::

e.g showTextAlert

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="0219ec57-fc09-495f-980c-58c5eb03c4dc"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
showTextAlert("Alert", "Entity to Load:", "loadAlertEntity()", "showToast(\"Dialog cancelled\")")
...
loadAlertEntity() {
  entityId = getLastTextAlertInput();
  loadEntity(entityId);
}
```
:::
:::

When showTextAlert is called, a dialog will appear and shows the title
and message as specified and have an input field for the user to enter
some text. The function call also takes two callbacks, one for the
\"OK\" button of the dialog and one for the \"Cancel\" button. The first
callback can then use the getLastTextAlertInput() api call to get the
input entered and do something with it. Note that the cancel callback
cannot get access to the input entered

 

e.g showDateAlert

 

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="658752e8-b0b9-4e3d-bb85-069eee65ce46"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
showDateAlert("Alert", "Set Date:", "showToast(getLastDateAlertInput())", "showToast(\"Dialog cancelled\")")
```
:::
:::

This behaves similar to showTextAlert.

e.g showTimeAlert

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="7ef0db45-216f-4fb6-8a19-7e68daab9587"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
showTimeAlert("Alert", "Set Time:", "showToast(getLastTimeAlertInput())", "showToast(\"Dialog cancelled\")")
```
:::
:::

This behaves similar to showTextAlert.

### Drop Downs, Radio Button Groups, CheckBox Groups, Lists, Picture Gallery, Tables, WebViews {#FAIMSData,UIandLogicCook-Book-DropDowns,RadioButtonGroups,CheckBoxGroups,Lists,PictureGallery,Tables,WebViews}

The api populateDropDown, populateRadioGroup,  populateCheckBoxGroup,
populateTableRaw, populateTablePivot adds the ability to set selection
options from the database or from the logic.

e.g. populateDropDown

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="06a9e3b4-47fe-4eb8-9ba2-688b633f5b57"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
fetchAll("select uuid, uuid from archentity where uuid || aenttimestamp in ( select uuid || max(aenttimestamp) from archentity group by uuid having deleted is null);", new FetchCallback() {
  onFetch(entities) {
    populateDropDown("tabgroup1/tab1/entities", entities);
  } 
});

 
fetchAll("select uuid, uuid from archentity where uuid || aenttimestamp in ( select uuid || max(aenttimestamp) from archentity group by uuid having deleted is null);", new FetchCallback() {
  onFetch(entities) {
    // populate with null option
    populateDropDown("tabgroup1/tab1/entities", entities, true);
  } 
});
 
populateHierarchicalDropDown("tabgroup1/tab1/rocks", "rocks");
 
populateHierarchicalDropDown("tabgroup1/tab1/rocks", "rocks", true); // populate with null option
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="b972ce2a-0ac1-4293-95ea-ca3e3ea509bc"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
You can no longer populate dropdowns via the ui schema instead you must
populate via the logic script. Here is an example of populating a simple
dropdown with values

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="ae4dff38-9e9f-4112-b60d-7fc54748692c"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
list = new ArrayList();
list.add("Item 1");
list.add("Item 2");
list.add("Item 3");
populateDropDown("tabgroup1/tab1/items", list);
```
:::
:::
:::
:::

e.g. populateRadioGroup

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="fcdb5a16-9deb-4154-874b-8682767e456b"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
fetchAll("select vocabid, vocabname from vocabulary left join attributekey using (attributeid) where attributename = 'type';", new FetchCallback() {
  onFetch(types) {
    populateRadioGroup("tabgroup1/tab1/types",types);
  }
});
```
:::
:::

e.g. populateCheckBoxGroup

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="2b0d7042-001e-474b-8661-14cac658dc86"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
fetchAll("select vocabid, vocabname from vocabulary left join attributekey using (attributeid) where attributename = 'location';", new FetchCallback() {
  onFetch(locations) {
    populateCheckBoxGroup("tabgroup1/tab1/locations",locations);
  }
});
```
:::
:::

e.g. populateList and getListItemValue

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="e8651c2a-ae2b-4775-a53c-9e049b9c4d06"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
fetchAll("select userid,(fname || ' ' || lname) as name from user where userdeleted is NULL;", new FetchCallback() {
  onFetch(users) {
    populateList("user/tab1/userlist",users);
  }
});

onEvent("user/tab1/userlist","click","showToast(\"getListItemValue()\")"
```
:::
:::

The example shows how to fetch users from the database and populate a
list. By binding the click event to the list, when clicking on the list,
it will execute the callback which in this case show a toast containing
the value of the clicked by calling the getListItemValue.

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="bb8b0a5e-2ed7-4c49-a4c3-14c6f01ea7d9"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
getListItemValue returns the last selected item on the clicked list.
:::
:::

e.g. populateCursorList

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="0e0f1de2-c0be-4632-816b-184ee5a5d496"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
populateCursorList("user/tab1/users", "select uuid, freetext from latestNonDeletedArchentIdentifiers limit ? offset ?;", 25);
```
:::
:::

This example is how to populate a cursor list. This originally populates
the list with a number of items as specified specified by the limit, in
this case 25 items, then whenever the list is scrolled to the bottom, a
further 25 items are appended dynamically. The query passed into the api
needs to specify limit and offset as above.

::: {.confluence-information-macro .confluence-information-macro-note .conf-macro .output-block data-hasbody="true" data-macro-name="note" data-macro-id="da875d41-5fe0-4c84-b4dd-8fb6f4ab0a12"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-warning
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
If the module has css styling and lists are being called to populate
multiple times, a call should be made to refresh the tabgroup\'s CSS

e.g.

        populateList("user/tab1/userlist",users);

     refreshTabgroupCSS("user");
:::
:::

To populate a picture gallery from a query use the following.

e.g. populatePictureGallery

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="3e7d59bd-54d3-4dd8-9f89-0e70d2613841"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
fetchAll("select vocabid, vocabname, pictureurl from vocabulary left join attributekey using (attributeid) where attributename = 'picture';", new FetchCallback() {
  onFetch(pictures) {
    populatePictureGallery("tabgroup1/tab1/picture", pictures);
  }
});

 
fetchAll("select vocabid, vocabname, pictureurl from vocabulary left join attributekey using (attributeid) where attributename = 'picture';", new FetchCallback() {
  onFetch(pictures) {
    populateHierarchicalPictureGallery("tabgroup1/tab1/picture", pictures);
  }
});
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="e1f6d7da-39e9-4bc4-b674-27cfa66a6578"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
::: {.message-content}
Note: The picture gallery is populated in the same order that the vocab
id\'s are retrieved. To ensure that the pictures in the picture gallery
have the same order as defined in the data\_schema, the query needs to
me be modified to preserve a specific order.

::: {.syntaxhighlighter .nogutter .java}
\

::: {.table-wrap}
+-----------------------------------------------------------------------+
| ::: {.container title="Hint: double-click to select code"}            |
| ::: {.line .number1 .index0 .alt2}                                    |
| `fetchAll(`{.java                                                     |
| .plain}`"select vocabid, vocabname, pictureurl from vocabulary left j |
| oin attributekey using (attributeid) where attributename = 'picture'  |
| order by vocabcountorder;"`{.java                                     |
| .string}`, `{.java .plain}`new`{.java .keyword}                       |
| `FetchCallback() {`{.java .plain}                                     |
| :::                                                                   |
|                                                                       |
| ::: {.line .number2 .index1 .alt1}                                    |
| `  `{.java .spaces}`onFetch(pictures) {`{.java .plain}                |
| :::                                                                   |
|                                                                       |
| ::: {.line .number3 .index2 .alt2}                                    |
| `    `{.java .spaces}`populatePictureGallery(`{.java                  |
| .plain}`"tabgroup1/tab1/picture"`{.java .string}`, pictures);`{.java  |
| .plain}                                                               |
| :::                                                                   |
|                                                                       |
| ::: {.line .number4 .index3 .alt1}                                    |
| `  `{.java .spaces}`}`{.java .plain}                                  |
| :::                                                                   |
|                                                                       |
| ::: {.line .number5 .index4 .alt2}                                    |
| `});`{.java .plain}                                                   |
| :::                                                                   |
|                                                                       |
| <div>                                                                 |
|                                                                       |
| ``{.java .plain}                                                      |
|                                                                       |
| </div>                                                                |
| :::                                                                   |
+-----------------------------------------------------------------------+
:::
:::
:::
:::
:::

\

For this to work you need to add the picture urls to the vocab in the
data schema as follows. The picture urls are relative to the modules
root directory.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="5cdb3f7b-6de9-46fc-831d-5783b1da2019"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
<property type="dropdown" name="picture" minCardinality="1" maxCardinality="1">
      <bundle>DOI</bundle>
      <lookup>
        <term pictureURL="pictures/cugl69808.jpg">cugl69808.jpg</term>
        <term pictureURL="pictures/cugl69807a.jpg">cugl69807a.jpg</term>
        <term>None</term>
...
    </property>
...
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="2df382bc-af3d-4a32-94d9-bb0d33676e49"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Note that the collection pictures should contain of the vocabid,
vocabname, and picture url in order to work.
:::
:::

To populate a file list use the following.

eg. populateFileList

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="eecedcd6-acbf-4f1c-b35d-9fa333eb0bee"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
ArrayList files = new ArrayList();
files.add(getAttachedFilePath("attachment1.xml"));
populateFileList("tabgroup1/tab1/files", files);
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="fca86971-96f2-4e44-b111-1a3c62f2d9cf"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Note that the file paths need to be full paths
:::
:::

\

To populate a camera or video gallery use the following.

e.g. populateCameraPictureGallery and populateVideoGallery

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="ca75db19-13df-45e2-b1c8-c5d68d301693"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
photos = new ArrayList();
photos.add(photoUrl);
populateCameraPictureGallery("tabgroup1/tab1/photos", photos);


videos = new ArrayList();
videos.add(videoUrl);
populateVideoGallery("tabgroup1/tab1/videos", videos);
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="a1e13f2b-6ca8-449c-a3f7-5edaa31c4dcc"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
The photo and video urls need to be absolute path urls. For a better
example look at the file attachment examples below.
:::
:::

\

To populate a table from sql use the following

e.g. populateTableRaw

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="7fa84090-f778-4f9e-a031-8f7a7a812380"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
query = "select ...";
headers = new ArrayList();
headers.add("header1");
...
populateTableRaw("tabgroup1/tab1/table", query, headers, null, -1, null);
```
:::
:::

\

To populate a table from sql and pivot the table use the following.
Remember the pivot sql must be return columns in order as id, name,
value which will then render the table as id, name1, name2, etc

e.g. populateTablePivot

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="c395e297-9576-42e9-a7d7-f5c8d7c6a0c8"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
query = "select ...";
headers = new ArrayList();
headers.add("header1");
...
populateTablePivot("tabgroup1/tab1/table", query, headers, "Click Me", 2, "onClicked()");
```
:::
:::

\

To populate a web view with data from a html file or html string use the
following. The html file can be attached as part of the module

e.g. populateWebView, populateWebViewHtml

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="8013dfee-3191-4c80-86e5-79afa506b45d"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
htmlFile = getAttachedFilePath("files/data/webfile.html");
populateWebView("tabgroup1/tab1/web", htmlFile);
...
populateWebViewHtml("tabgroup1/tab1/web", "<h2>Module Info</h2><p>This module has been created by ...</p>");
```
:::
:::

### Table Events {#FAIMSData,UIandLogicCook-Book-TableEvents}

To use table actions use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="650ba01d-c19d-4c90-984b-289de5e1ed72"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
query = "select ...";
headers = new ArrayList();
headers.add("header1");
...
actionName = "ClickMe";
actionColumn = 2;
actionCallback = "onClicked()"
populateTablePivot("tabgroup1/tab1/table", query, headers, actionName, actionColumn, actionCallback);
 
onClicked() {
    row = getTableRow();
    value = getTableValue();
}
```
:::
:::

### Web View Events {#FAIMSData,UIandLogicCook-Book-WebViewEvents}

A web view can be called to navigate back (emulating a browser\'s back
button)

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="4ece597d-b378-4408-8499-830ab2fda4bb"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
onEvent("tabgroup1/tab2/back", "click", "navigateWebViewBack(\"tabgroup1/tab2/web\")");
```
:::
:::

### Dropdown and Picture Gallery Select Events {#FAIMSData,UIandLogicCook-Book-DropdownandPictureGallerySelectEvents}

Dropdowns and picture galleries (and their hierarchical counterparts)
and radio groups all support \"select events\" e.g.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="d978c901-75ae-4406-bee9-d088cb8c22cf"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
onEvent("tabgroup1/tab1/gallery", "select", "selectEvent()");
```
:::
:::

This is different to a click event in that the event is only executed
when an option is selected and then changed. i.e It will not execute if
the the selected option is selected again

### Showing Tabs & Tab Groups {#FAIMSData,UIandLogicCook-Book-ShowingTabs&TabGroups}

To show tabs or tab groups use the following apis.

e.g. newTab

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="77ce4b6e-90fd-4cf9-86a6-16ba14235354"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
newTab("tabgroup1/tab2")
```
:::
:::

The newTab will open the tab specified in the path
\<tabgroupname\>/\<tabname\> and clear out the values if it has been
answered.

e.g. newTabGroup

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="4f5859d0-d55f-4960-898c-7627100c5066"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
newTabGroup("tabgroup1")
```
:::
:::

The newTabGroup will open the tab group specified in the path
\<tabgroupname\> and clear out the values if it has been answered.

e.g. showTab

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="d40b8e2b-f95b-400e-9674-446d72c300cb"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
showTab("tabgroup1/tab1")
```
:::
:::

The showTab will open the tab specified in the path
\<tabgroupname\>/\<tabname\> and reserve the values for each fields if
it has been answered.

e.g. showTab with uuid

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="96515637-f857-4599-bc6c-b3491a9a7ef7"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
showTab("tabgroup1/tab1","100001242124")
```
:::
:::

The showTab with uuid will open the tab specified in the path
\<tabgroupname\>/\<tabname\> and load the values from the records
specified by the id to the related fields in the tab. So it would not
change the value in other tabs.

e.g. showTabGroup

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="ca56f430-ea1a-43c0-a807-95361e35ab8e"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
showTabGroup("tabgroup1")
```
:::
:::

The showTabGroup will open the tab group specified in the path
\<tabgroupname\> and reserve the values for each fields if it has been
answered.

e.g. showTabGroup with uuid

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="e319d3bc-a8ab-4445-84fb-3accb4a216aa"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
showTabGroup("tabgroup1","100001242124", new FetchCallback() {
  onFetch(result) {
    entity = result
    // do something
  } 
 
  onError(message) {
    showToast(message);
  } 
})
```
:::
:::

The showTabGroup with uuid will open the tab group specified in the path
\<tabgroupname\> and load the values from the records specified by the
id to the related fields in the tabgroup.

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="e7b32b54-0e32-4aed-8009-d0782228e055"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Tab showing and closing actions generally should be embedded within an
event handler for that tab, as rendering doesn\'t occur immediately
after the code is read.

e.g.

::: {.code .panel .pdl style="white-space: normal;"}
::: {.codeContent .panelContent .pdl}
::: {.syntaxhighlighter .nogutter .java style="width: 570.0px;font-size: 1.0em;"}
\

::: {.table-wrap}
+-----------------------------------------------------------------------+
| ::: {.container style="float: none;width: auto;height: auto;vertical- |
| align: baseline;" title="Hint: double-click to select code"}          |
| ::: {.line .number1 .index0 .alt2 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `onEvent(`{.java .plain                                               |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}`"tabgroup"`{.java            |
| .string                                                               |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,51,102);"}`, `{.java                 |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}`"show"`{.java                |
| .string                                                               |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,51,102);"}`, `{.java                 |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}`"onShow()"`{.java            |
| .string                                                               |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,51,102);"}`);`{.java                 |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}                              |
| :::                                                                   |
|                                                                       |
| ::: {.line .number2 .index1 .alt1 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
|                                                                       |
| :::                                                                   |
|                                                                       |
| ::: {.line .number3 .index2 .alt2 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `onShow() {`{.java .plain                                             |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}                              |
| :::                                                                   |
|                                                                       |
| ::: {.line .number4 .index3 .alt1 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `  `{.java .spaces                                                    |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;"}`// ...`{.java                                  |
| .comments                                                             |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,130,0);"}                            |
| :::                                                                   |
|                                                                       |
| ::: {.line .number5 .index4 .alt2 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `  `{.java .spaces                                                    |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;"}`showTab(`{.java                                |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}`"tabgroup/tab"`{.java        |
| .string                                                               |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,51,102);"}`);`{.java                 |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}                              |
| :::                                                                   |
|                                                                       |
| ::: {.line .number6 .index5 .alt1 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `  `{.java .spaces                                                    |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;"}`// ...`{.java                                  |
| .comments                                                             |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,130,0);"}                            |
| :::                                                                   |
|                                                                       |
| ::: {.line .number7 .index6 .alt2 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `  `{.java .spaces                                                    |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;"}`cancelTab(`{.java                              |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}`"tabgroup/tab"`{.java        |
| .string                                                               |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,51,102);"}`, `{.java                 |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}`true`{.java                  |
| .keyword                                                              |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;font-weight: bold;color: rgb(51,102,153);"}`);`{. |
| java                                                                  |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}                              |
| :::                                                                   |
|                                                                       |
| ::: {.line .number8 .index7 .alt1 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `  `{.java .spaces                                                    |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;"}`// ...`{.java                                  |
| .comments                                                             |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,130,0);"}                            |
| :::                                                                   |
|                                                                       |
| ::: {.line .number9 .index8 .alt2 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `}`{.java .plain                                                      |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}                              |
| :::                                                                   |
| :::                                                                   |
+-----------------------------------------------------------------------+
:::
:::
:::
:::
:::
:::

### Closing Tabs and Tab Groups {#FAIMSData,UIandLogicCook-Book-ClosingTabsandTabGroups}

To close tabs and tabgroups the cancelTab and cancelTabGroup apis are
available.

e.g. cancelTab

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="24fdfb23-de0f-44e9-9873-0ec5ccf81d2b"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
cancelTab("tabgroup1/tab1", true)
```
:::
:::

The cancelTab will close the tab specified in the path
\<tabgroupname\>/\<tabname\>. If the warn argument is set to true and if
there are any new changes to the fields (value, annotation, certainty) a
dialog will pop up asking whether the user wants to cancel the tab or
not. If the user chooses OK then the tab will close else it remains
open. If the warn argument is set to false then tab will be closed
regardless of any changes in the tab.

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="88a139f9-e3c6-4838-964b-8dea72103368"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Its best practice after calling cancelTab to use showTab to open a new
tab for the user
:::
:::

e.g. cancelTabGroup

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="d069e5b7-e473-48d5-bd32-0d94de60d9f5"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
cancelTabGroup("tabgroup1", true)
```
:::
:::

The cancelTabGroup will close the tab group specified in the path
\<tabgroupname\>. It works similar to cancelTab but instead of closing
the tab it closes the entire tab group.

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="edba0baa-a725-4988-a26d-3414432fec7c"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Tab showing and closing actions generally should be embedded within an
event handler for that tab, as rendering doesn\'t occur immediately
after the code is read.

e.g.

::: {.code .panel .pdl style="white-space: normal;"}
::: {.codeContent .panelContent .pdl}
::: {.syntaxhighlighter .nogutter .java style="width: 570.0px;font-size: 1.0em;"}
\

::: {.table-wrap}
+-----------------------------------------------------------------------+
| ::: {.container style="float: none;width: auto;height: auto;vertical- |
| align: baseline;" title="Hint: double-click to select code"}          |
| ::: {.line .number1 .index0 .alt2 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `onEvent(`{.java .plain                                               |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}`"tabgroup"`{.java            |
| .string                                                               |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,51,102);"}`, `{.java                 |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}`"show"`{.java                |
| .string                                                               |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,51,102);"}`, `{.java                 |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}`"onShow()"`{.java            |
| .string                                                               |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,51,102);"}`);`{.java                 |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}                              |
| :::                                                                   |
|                                                                       |
| ::: {.line .number2 .index1 .alt1 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
|                                                                       |
| :::                                                                   |
|                                                                       |
| ::: {.line .number3 .index2 .alt2 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `onShow() {`{.java .plain                                             |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}                              |
| :::                                                                   |
|                                                                       |
| ::: {.line .number4 .index3 .alt1 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `  `{.java .spaces                                                    |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;"}`// ...`{.java                                  |
| .comments                                                             |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,130,0);"}                            |
| :::                                                                   |
|                                                                       |
| ::: {.line .number5 .index4 .alt2 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `  `{.java .spaces                                                    |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;"}`showTab(`{.java                                |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}`"tabgroup/tab"`{.java        |
| .string                                                               |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,51,102);"}`);`{.java                 |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}                              |
| :::                                                                   |
|                                                                       |
| ::: {.line .number6 .index5 .alt1 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `  `{.java .spaces                                                    |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;"}`// ...`{.java                                  |
| .comments                                                             |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,130,0);"}                            |
| :::                                                                   |
|                                                                       |
| ::: {.line .number7 .index6 .alt2 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `  `{.java .spaces                                                    |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;"}`cancelTab(`{.java                              |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}`"tabgroup/tab"`{.java        |
| .string                                                               |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,51,102);"}`, `{.java                 |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}`true`{.java                  |
| .keyword                                                              |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;font-weight: bold;color: rgb(51,102,153);"}`);`{. |
| java                                                                  |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}                              |
| :::                                                                   |
|                                                                       |
| ::: {.line .number8 .index7 .alt1 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `  `{.java .spaces                                                    |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;"}`// ...`{.java                                  |
| .comments                                                             |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,130,0);"}                            |
| :::                                                                   |
|                                                                       |
| ::: {.line .number9 .index8 .alt2 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `}`{.java .plain                                                      |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}                              |
| :::                                                                   |
| :::                                                                   |
+-----------------------------------------------------------------------+
:::
:::
:::
:::
:::
:::

\

### Date & Time {#FAIMSData,UIandLogicCook-Book-Date&Time}

There is a special method to show the current time to the ui that can be
specified from the logic by calling getCurrentTime. GetCurrentTime
returns a string containing current time in the format of \'YYYY-MM-dd
hh:mm:ss

e.g. getCurrentTime

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="b6527dd6-de3c-4c2c-b953-79ec78183d43"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
time = getCurrentTime();
setFieldValue("tabgroup5/tab3/lastsuccess", time);
```
:::
:::

The example shows that we can set a field with the current time and the
field should have faims\_read\_only attribute set to be true since the
current time should not be editable by the user.

### Module Metadata {#FAIMSData,UIandLogicCook-Book-ModuleMetadata}

Module metadata can be shown on the UI by calling the following apis.

e.g. Module metadata example

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="939c658a-e813-40d6-97b4-9d310c0e7367"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
setFieldValue("tabgroup1/tab1/name", getModuleName());
setFieldValue("tabgroup1/tab1/version", getModuleVersion());
setFieldValue("tabgroup1/tab1/id", getModuleId());
setFieldValue("tabgroup1/tab1/season", getModuleSeason());
setFieldValue("tabgroup1/tab1/description", getProjectDescription());
setFieldValue("tabgroup1/tab1/permit_no", getPermitNo());
setFieldValue("tabgroup1/tab1/permit_holder", getPermitHolder());
setFieldValue("tabgroup1/tab1/contact_address", getContactAndAddress());
setFieldValue("tabgroup1/tab1/participants", getParticipants());
setFieldValue("tabgroup1/tab1/permit_issued_by", getPermitIssuedBy());
setFieldValue("tabgroup1/tab1/permit_type", getPermitType());
setFieldValue("tabgroup1/tab1/copyright_holder", getCopyrightHolder());
setFieldValue("tabgroup1/tab1/client_sponsor", getClientSponsor());
setFieldValue("tabgroup1/tab1/land_owner", getLandOwner());
setFieldValue("tabgroup1/tab1/has_sensitive_data", hasSensitiveData());
setFieldValue("tabgroup1/tab1/module_srid", getModuleSrid());
```
:::
:::

In the example, the module metadata is obtained and shown on the fields.
It is important to give the field faims\_read\_only attribute to be true
since we do not want the user to be able to edit the module metadata on
the device.

The server will have the ability to edit the module metadata.

### Connected Server {#FAIMSData,UIandLogicCook-Book-ConnectedServer}

The currently connected server can be obtained by using the following
call. It will return something similar to
\"[demo.fedarch.org](http://demo.fedarch.org){.external-link}:3000\"

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="0edbdd3f-f6a8-4b33-bbff-74a92959da6d"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
getConnectedServer();
```
:::
:::

NOTE: This is the server currently specified in the settings as being
connected, it does not check whether it is active i.e if connection
signal has been lost etc.

Maps and GIS {#FAIMSData,UIandLogicCook-Book-MapsandGIS}
============

The following examples will show how to render maps, vectors and draw
geometry.

### Rendering map {#FAIMSData,UIandLogicCook-Book-Renderingmap}

Given the following map view defined in the ui schema. 

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="961b8800-6350-4275-8af4-76088bded377"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
   <tab1>
     <map></map>
   </tab1>
...
  <group ref="tab1" faims_scrollable="false">
   <input ref="map" faims_map="true">
     <label>Map:</label>
   </input>
  </group>
...
```
:::
:::

### Saving and loading map from config {#FAIMSData,UIandLogicCook-Book-Savingandloadingmapfromconfig}

To save the current map view configuration (i.e. orientation, layers,
tool styles, selections, global style) use the following. It will save
all the configuration as a json file as specified in the API call:

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="88456b7e-ea2c-4315-9720-42e0581c2d4d"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
file = getAttachedFilePath("files/data/saved_config.json");
saveMapViewConfiguration("main/map/map", file, "showToast(\"Saved map configuration\")");
```
:::
:::

Note: This will not save canvas layer geometries and it will not save
tracklog preferences.

To load a map view up with an existing configuration use the following:

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="390b99c5-3c03-4976-98ef-cb9db4255671"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
jsonFile = getAttachedFilePath("files/data/saved_config.json");
loadMapViewConfiguration("main/map/map", jsonFile, "showToast(\"Loaded map configuration\")");
```
:::
:::

### Add base map {#FAIMSData,UIandLogicCook-Book-Addbasemap}

To add a base raster layer use the following. There can only be a single
base layer.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="45e5d556-deb9-4833-a59f-113aa4fdaaf9"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
showBaseMap("tabgroup1/tab1/map", "raster map" "map.tif");
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="7cdf3297-4335-4567-b18b-9b393e1d01a4"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
The raster map must be in projection EPSG:3857
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="ec79eadf-3aa2-4844-995a-b33d39bc0f88"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
map.tif url is relative to the root of the modules folder
:::
:::

### Add raster map {#FAIMSData,UIandLogicCook-Book-Addrastermap}

To add a raster layer use the following. You can have multiple raster
layers.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="91b3ac28-e34a-47d7-b201-d93e7aa43a5f"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
showRasterLayer("tabgroup1/tab1/map", "raster map" "map.tif");
```
:::
:::

### Add shape vector layer {#FAIMSData,UIandLogicCook-Book-Addshapevectorlayer}

::: {.confluence-information-macro .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="f40c2558-5078-4a35-9783-aa8ca4aa6502"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-error
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
This has been deprecated by spatial layer
:::
:::

\

To add a shape vector layer use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="7e9fc746-c39d-408a-8d08-22f95e6fd935"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
ps = createPointStyle(10, Color.BLUE, 0.2f, 0.5f);
ls = createLineStyle(10, Color.GREEN, 0.05f, 0.3f, null);
pos = createPolygonStyle(10, Color.parseColor("#440000FF"), createLineStyle(10, Color.parseColor("#AA000000"), 0.01f, 0.3f, null));
ts = createTextStyle(10, Color.WHITE, 40, Typeface.SANS_SERIF);
showShapeLayer("tabgroup1/tab1/map", "Shape Layer", "shape.shp", ps, ls, pos, ts);
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="6605711f-ddb8-4bda-8f04-39ad843c668a"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
The shape file must be in projection EPSG:3857
:::
:::

### Add spatial vector layer {#FAIMSData,UIandLogicCook-Book-Addspatialvectorlayer}

To add a spatial vector layer use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="305f11c5-9986-4f2a-9b5c-26478903934a"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
ps = createPointStyle(10, Color.BLUE, 0.2f, 0.5f);
ls = createLineStyle(10, Color.GREEN, 0.05f, 0.3f, null);
pos = createPolygonStyle(10, Color.parseColor("#440000FF"), createLineStyle(10, Color.parseColor("#AA000000"), 0.01f, 0.3f, null));
ts = createTextStyle(10, Color.WHITE, 40, Typeface.SANS_SERIF);
table = // specify table in database
idcolumn = // specify id column name
labelcolumn = // specify label column name
showSpatialLayer("tabgroup1/tab1/map", "Spatial Layer", "spatial.sqlite", table, idcolumn, labelcolumn, ps, ls, pos, ts);
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="c9451f72-a261-4505-a89e-3940d89291a1"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
The spatial database must be in projection EPSG:3857
:::
:::

### Add database vector layer {#FAIMSData,UIandLogicCook-Book-Adddatabasevectorlayer}

To add a database vector layer use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="a13c967b-14f5-40f0-84b5-003097b82716"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
ps = createPointStyle(10, Color.BLUE, 0.2f, 0.5f);
ls = createLineStyle(10, Color.GREEN, 0.05f, 0.3f, null);
pos = createPolygonStyle(10, Color.parseColor("#440000FF"), createLineStyle(10, Color.parseColor("#AA000000"), 0.01f, 0.3f, null));
ts = createTextStyle(10, Color.WHITE, 40, Typeface.SANS_SERIF);
isEntity = // specify where to load entity or relationships
queryName = // specify the name of the sql query
querySql = // specify the query sql to run against the database
showDatabaseLayer("tabgroup1/tab1/map", "Database Layer", isEntity, queryName, querySql, ps, ls, pos, ts);
```
:::
:::

### Add canvas layer {#FAIMSData,UIandLogicCook-Book-Addcanvaslayer}

You can create canvas layers to draw geometry onto using the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="88e8994f-45c1-425a-9e02-fd0f63e56847"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
layerId = createCanvasLayer("tabgroup1/tab1/map", "Canvas Layer");
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="87fb8965-07d4-4503-8e71-ecb1f0331811"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Keep a reference to the layerId returned by createVectorLayer. This can
be used to draw points onto the layer or removing the layer entirely.
:::
:::

### Map Controls {#FAIMSData,UIandLogicCook-Book-MapControls}

To set the map focus point use the following:

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="061cdf4d-1a73-4f11-896b-2c346988493e"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
// australia
lon = 151.23f
lat = -33.58f
setMapFocusPoint("tabgroup1/tab1/map", lon, lat);
```
:::
:::

Value could be double or float.

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="2ac48282-b6e1-486a-91f5-d496fe231f46"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
The point must be in module projection.
:::
:::

To set the map rotation use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="ff9cb7fb-694a-460e-910b-98af6676d002"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
setMapRotation("tabgroup1/tab1/map", 90.0f);
```
:::
:::

To set the map tilt use the following

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="e13a9100-6c2f-4ea9-9107-c2764be2ac02"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
setMapTilt("tabgroup1/tab1/map", 90.0f);
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="2957fe5e-b2a3-4ea9-9e5b-002ac1fee118"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
The minimum tilt is 30.0f
:::
:::

To set the map zoom use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="c916f53c-fb85-435c-99e1-f7abea36ed8e"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
setMapZoom("tabgroup1/tab1/map", 17.0f);
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="96fa390b-c264-4bf8-81bc-7654a77f2f71"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
There are 18 levels of zoom defined for the raster map therefore zoom
levels above 18 might not rendered as well.
:::
:::

### Center map using GPS {#FAIMSData,UIandLogicCook-Book-CentermapusingGPS}

To center the map the GPS position use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="e284caed-9c47-4691-b8a3-05dcacfc9652"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
centerOnCurrentPosition("tabgroup1/tab1/map");
```
:::
:::

### Locking / Unlocking the map {#FAIMSData,UIandLogicCook-Book-Locking/Unlockingthemap}

Locking the map keeps the map at a 2D perspective. This is useful when
drawing geometry on to the map. To lock the map use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="cdab9487-5dfe-493f-8897-9bea74ba2f58"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
lockMapView("tabgroup1/tab1/map", true);
```
:::
:::

To unlock the map use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="65ae6c79-2069-4906-8da6-4819bb299867"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
lockMapView("tabgroup1/tab1/map", false);
```
:::
:::

### Adding map event listeners {#FAIMSData,UIandLogicCook-Book-Addingmapeventlisteners}

To be able to draw points on the map or select geometry on the map you
can add a map event listener. To add click and select listener to the
map use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="59c6971c-78cc-4564-9da6-c70ed9e9adf7"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
onMapEvent("tabgroup1/tab1/map", "clickCallback()", "selectCallback()");

clickCallback() {
  point = getMapPointClicked();
...
}

selectCallback() {
  geomId = getMapGeometrySelected();
...
}
```
:::
:::

The getMapPointClicked method will hold the last clicked value on the
map and the getMapGeometrySelected method will hold the last selected
geometry on the map.

### Styling Vectors {#FAIMSData,UIandLogicCook-Book-StylingVectors}

Styling is used when loading vector layers or creating geometry. Use the
following to create point, line, polygon and text styles.

e.g. point style

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="1ee35138-5979-4c93-a739-c4f8484e2b83"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
minZoom = 10;
color = Color.RED;
size = 0.1f;
pickingSize = 0.3f;
pointStyle = createPointStyle(minZoom, color, size, pickingSize);
```
:::
:::

e.g. line style

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="c242e61b-7f5f-4e27-b1dc-5810617942dc"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
minZoom = 10;
color = Color.RED;
width = 0.1f;
pickingWidth = 0.3f;
lineStyle = createLineStyle(minZoom, color, with, pickingWidth, pointStyle); // note: point style can be null
```
:::
:::

e.g. polygon style

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="12e34cae-be40-4eaa-a58d-44eefd35b5d8"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
minZoom = 10;
color = Color.RED;
pointStyle = createPolygonStyle(minZoom, color, lineStyle); // note: line style can be null
```
:::
:::

e.g. text style

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="00f637bd-1fd4-450b-86b4-e44f59069384"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
minZoom = 10;
color = Color.RED;
fontSize = 40;
font = Typeface.SANS_SERIF;
textStyle = createTextStyle(minZoom, color, fontSize, font); 
```
:::
:::

### Drawing points {#FAIMSData,UIandLogicCook-Book-Drawingpoints}

To draw a point on the map you can use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="2f50360b-d4be-4447-997a-dd08a9169441"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
lon = 151.23f
lat = -33.58f
point = createPoint(lon, lat);
geomId = drawPoint("tabgroup1/tab1/map", layerId, point, pointStyle);
```
:::
:::

Keep a reference to the geomId so you can later clear the geometry or
draw overlays for it.

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="d5d83850-a4ca-438a-aa67-60d5ab01b37d"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
The points must be in the modules projection.
:::
:::

### Drawing lines {#FAIMSData,UIandLogicCook-Book-Drawinglines}

To draw a line on the map you can use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="82ba88dd-e2a7-48da-b5d7-fd086619309b"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
points = new ArrayList();
points.add(createPoint(x1, y1));
points.add(createPoint(x2, y2));
points.add(createPoint(x3, y3));
geomId = drawLine("tabgroup1/tab1/map", layerId, points, lineStyle);
```
:::
:::

Keep a reference to the geomId so you can later clear the geometry or
draw overlays for it.

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="d27b3aee-b0f8-4fdc-ad7f-985c657192fb"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
The lines must be in the modules projection.
:::
:::

### Drawing polygons {#FAIMSData,UIandLogicCook-Book-Drawingpolygons}

To draw a polygon on the map you can use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="a8315b5c-c65a-4956-b19c-96a5a18b8ba5"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
points = new ArrayList();
points.add(createPoint(x1, y1));
points.add(createPoint(x2, y2));
points.add(createPoint(x3, y3));
drawPolygon("tabgroup1/tab1/map", layerId, points, polygonStyle);
```
:::
:::

Keep a reference to the geomId so you can later clear the geometry or
draw overlays for it.

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="bc1291d0-1747-4adc-afc5-0e1bc9993084"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
The polygons must be in the modules projection.
:::
:::

### Moving vector geometry {#FAIMSData,UIandLogicCook-Book-Movingvectorgeometry}

To move a vector on the map you must first highlight it, then call
prepareHighlightTransform, move the vector then call
doHighlightTransform.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="e53cf999-ff4c-4057-a8cc-ae6ba65a1be7"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
onMapEvent("tabgroup1/tab1/map", "onMapClick()", "onMapSelect()");

onMapSelect() {
  geomId = getMapGeometrySelected();
  addGeometryHighlight("tabgroup1/tab1/map", currentGeometryId); // add it to the highlight list
  prepareHighlightTransform("tabgroup1/tab1/map"); // prepare it for transform
}
```
:::
:::

Now you can move the map normally. This way you can adjust the size,
orientation and position of the geometry by dragging the map around.
Once you happy with the new position of the geometry you can replace the
selected geometry by replacing it using the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="80e2839c-8fa5-40ba-91f0-a3242c8e28bc"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
doHighlightTransform("tabgroup1/tab1/map"); // transform the vector to its new position
removeGeometryHighlight("tabgroup1/tab1/map", geomId) // remove the geometry highlight, or call clearGeometryHighlights("tabgroup1/tab1/map") to clear all highlights
```
:::
:::

### Clearing Geometry {#FAIMSData,UIandLogicCook-Book-ClearingGeometry}

To clear a single geometry from the map use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="1da1bfdd-7b9f-4883-8c69-c9173fad3968"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
clearGeometry("tabgroup1/tab1/map", geomId);
```
:::
:::

To clear a list of geometry use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="473ca0bd-30df-4fa9-aa4e-42b505252ff9"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
clearGeometryList("tabgroup1/tab1/map", geomIdList);
```
:::
:::

### Saving GIS to Entities / Relationships {#FAIMSData,UIandLogicCook-Book-SavingGIStoEntities/Relationships}

Referring to the save entities / relationships examples above. To save
GIS data you can use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="94481bce-4e16-4a3a-ab87-fad2e748a3e1"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
collection = getGeometryHighlights();
...
saveArchEnt(entityId, "simple", collection, attributes);
```
:::
:::

Or if you want to save the entire layer to the entity you can use the
following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="977ea097-6eb9-417b-beae-800c84f9d8b1"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
collection = getGeometryList("tabgroup1/tab1/map", layerId);
...
saveArchEnt(entityId, "simple", collection, attributes);
```
:::
:::

### Loading GIS from Entities / Relationships {#FAIMSData,UIandLogicCook-Book-LoadingGISfromEntities/Relationships}

Referring to the load entities / relationships examples above. To load
GIS data you can use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="b71e98c2-a2b7-4ec8-bc5e-2ab9fb8f5923"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
fetchArchEnt(entityId, new FetchCallback() {
  onFetch(entity) {
    geometryList = entity.getGeometryList();

    for (Geometry geomId : geometryList) {
      if (geom instanceof Polygon) {
        drawGeometry("tabgroup1/tab1/map", layerId, geomId, polygonStyleSet);
      } else if (geom instanceof Line) {
        drawGeometry("tabgroup1/tab1/map", layerId, geomId, lineStyleSet);
      } else if (geom instanceof Point) {
        drawGeometry("tabgroup1/tab1/map", layerId, geomId, pointStyleSet);
      }
    }
  }
});
```
:::
:::

### Add Database Layer Queries {#FAIMSData,UIandLogicCook-Book-AddDatabaseLayerQueries}

To add database layer queries to load database layers via the layer
manager use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="a752121b-8349-4bcf-9f28-d88b228a6807"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
isEntity = true;
queryName = "All entities";
querySQL =
    "SELECT uuid, max(aenttimestamp) as aenttimestamp\n" + 
    " FROM archentity join aenttype using (aenttypeid)\n" +
    " where archentity.deleted is null\n" + 
    "   and lower(aenttypename) != lower('gps_track')\n" + 
    " group by uuid\n" + 
    " having max(aenttimestamp)";
addDatabaseLayerQuery("control/map/map", queryName, querySQL);
```
:::
:::

### Add TrackLog layer Queries {#FAIMSData,UIandLogicCook-Book-AddTrackLoglayerQueries}

To add track log layer queries to load track log layers via the layer
manager use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="19a700fa-2d22-4604-bb85-1d112d0dc899"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
addTrackLogLayerQuery("control/map/map", "track log entities", 
    "SELECT uuid, max(aenttimestamp) as aenttimestamp\n" + 
    " FROM archentity join aenttype using (aenttypeid)\n" +
    " where archentity.deleted is null\n" + 
    "   and lower(aenttypename) = lower('gps_track')\n" + 
    " group by uuid\n" + 
    " having max(aenttimestamp)");
```
:::
:::

### Adding Selection Tool Queries {#FAIMSData,UIandLogicCook-Book-AddingSelectionToolQueries}

To add database and legacy selection queries use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="17662964-c22d-425d-8a90-208efcc20596"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
// create a query builder
queryBuilder = createQueryBuilder(
        "select uuid\n" + 
        "  from latestNonDeletedArchent\n" + 
        "  JOIN latestNonDeletedAentValue using (uuid)\n" + 
        "  join aenttype using (aenttypeid)\n" + 
        "  LEFT OUTER JOIN vocabulary using (vocabid, attributeid) \n" + 
        "  where lower(aenttypename) = lower(?) \n" + 
        "   group by uuid");
 
// add a parameter type with default argument
queryBuilder.addParameter("Type", "Structure");
 
// add the query builder 
addSelectQueryBuilder("control/map/map", "Select entity by type", queryBuilder);

// similar process for legacy data
queryBuilder = createLegacyQueryBuilder("Select PK_UID from Geology100_Sydney where PK_UID = ?");
 
queryBuilder.addParameter("ID", null);

addLegacySelectQueryBuilder("control/map/map", "Select geometry by id", "files/data/maps/sydney.sqlite", "Geology100_Sydney", queryBuilder);
```
:::
:::

### Set layer visiblility {#FAIMSData,UIandLogicCook-Book-Setlayervisiblility}

To change the visibility of a map layer use the following

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="4ce7304d-6b8a-4b0a-a6b0-9b41e034f2ab"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
 setLayerVisible("tabgroup1/tab1/map", true);
```
:::
:::

### Setting selected layer {#FAIMSData,UIandLogicCook-Book-Settingselectedlayer}

To set the currently selected layer on the map, use the following, by
passing in either the layer ID or the name of the layer

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="18396329-0a36-4571-82ab-d44ed5d3ef54"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
// By ID
setSelectedLayer("tabgroup1/tab1/map", 1);
 
// By name
setSelectedLayer("tabgroup1/tab1/map", "Data Entry Layer");
```
:::
:::

### Convert projection of points {#FAIMSData,UIandLogicCook-Book-Convertprojectionofpoints}

To convert a point from one projection to another use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="e5021a02-35b3-4b5d-95fb-26b741323ecd"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
MapPos p = new MapPos(x, y);
MapPos np = convertFromProjToProj("4326", "3875", p);
```
:::
:::

### Enable / Disable tools view {#FAIMSData,UIandLogicCook-Book-Enable/Disabletoolsview}

To enable or disable the tools bar and layers bar use the following

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="5c61b43c-e41f-44aa-95e8-e432b340a6a3"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
 setToolsEnabled(MAP_REF, true);
```
:::
:::

### Bind events to tools {#FAIMSData,UIandLogicCook-Book-Bindeventstotools}

The create point, line and polygon tools trigger the tool create event
when a geometry is created and the Load tool triggers a tool load event
when a geometry is selected. Use the following to bind callback to those
events.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="a8529ef3-2808-47fe-8cfa-08e4491c0ebd"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
onToolEvent("tabgroup1/tab1/map", "create", "onCreate");
onToolEvent("tabgroup1/tab1/map", "load", "onLoad");
 
onCreate() {
    id = getMapGeometryCreated(); // geometry id of the vector element
}
 
onLoad() {
    id = getMapGeometryLoaded(); // uuid or relationshipid of the vector element 
    type = getMapGeometryLoadedType(); // either "entity" or "relationship"
}
```
:::
:::

### Refresh map {#FAIMSData,UIandLogicCook-Book-Refreshmap}

Refreshing the map will cause all layer to re-render themselves. This is
useful if you have made changes that could effect the map.

e.g. refreshMap

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="005c53d1-a531-4a32-8ee5-b62f4e082c06"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
refreshMap("tabgroup1/tab1/map");
```
:::
:::

GPS {#FAIMSData,UIandLogicCook-Book-GPS}
===

The following examples will show how to use GPS.

### Start Internal GPS {#FAIMSData,UIandLogicCook-Book-StartInternalGPS}

To start internal GPS use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="4599d3e5-104c-41cc-ab0d-e65815d61d6a"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
startInternalGPS();
```
:::
:::

### Start External GPS {#FAIMSData,UIandLogicCook-Book-StartExternalGPS}

To start external GPS use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="5862ef12-560f-4a63-828b-728c8bff1476"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
startExternalGPS();
```
:::
:::

### Stop GPS {#FAIMSData,UIandLogicCook-Book-StopGPS}

To Start internal gps use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="9fd9f865-f41e-4f4b-a43a-258f7dcbadb5"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
stopGPS();
```
:::
:::

### Get GPS position {#FAIMSData,UIandLogicCook-Book-GetGPSposition}

To get the current GPS position use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="bfcb21a4-f494-49fc-8ad2-04946286d1e2"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
location = getGPSPosition();
lon = location.getLongitude();
lat = location.getLatitude();
```
:::
:::

To get the current GPS position using the projection selected by user,
use the following

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="e8d1a8e4-fbf5-4231-a1a7-d46689cc3c83"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
location = getGPSPositionProjected();
```
:::
:::

### Get GPS accuracy {#FAIMSData,UIandLogicCook-Book-GetGPSaccuracy}

To get the current GPS estimated accuracy use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="65495e9e-b775-4af8-8f08-54191a60f3a0"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
accuracy = getGPSEstimatedAccuracy();
```
:::
:::

or to specify which type of gps to use i.e. internal or external use the
following

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="b77e2ff3-dad7-4039-96ac-ff984a348f0d"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
accuracy = getGPSEstimatedAccuracy("internal");
```
:::
:::

### Get GPS heading {#FAIMSData,UIandLogicCook-Book-GetGPSheading}

To get the current GPS heading use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="c53d4f33-ba6a-4c24-9611-1a8bf86e3d52"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
heading = getGPSHeading();
```
:::
:::

or to specify which type of gps to use i.e. internal or external use the
following

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="c090b888-ca94-4fa2-bd14-b12d083630c0"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
heading = getGPSHeading("internal");
```
:::
:::

### Set GPS interval {#FAIMSData,UIandLogicCook-Book-SetGPSinterval}

To configure the delay between GPS updates you can use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="8b321b44-1cc7-4097-a4e7-c7c582a868fe"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
setGPSUpdateInterval(5);
```
:::
:::

### Setup Track Logs {#FAIMSData,UIandLogicCook-Book-SetupTrackLogs}

The track log allows the user to track their progression throughout the
day. The track log has two modes time and distance. The time mode allows
the user to specify the time interval (seconds) between callbacks and
the distance mode allows the user to specify the distance threshold
(meters) between callbacks.

e.g. startTrackingGPS and stopTrackingGPS

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="0a8d48fe-0be9-47da-a43e-106518b68e16"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
onEvent("controls/tab1/starttrackingtime", "click", "startTrackingGPS(\"time\", 10, \"saveTimeGPSTrack()\")");
onEvent("controls/tab1/starttrackingdistance", "click", "startTrackingGPS(\"distance\", 10, \"saveDistanceGPSTrack()\")");
onEvent("controls/tab1/stoptracking", "click", "stopTrackingGPS()");

saveTimeGPSTrack() {
    List attributes = createAttributeList();
    attributes.add(createEntityAttribute("gps_type", "time", null, null, null));
    saveGPSTrack(attributes);
}

saveDistanceGPSTrack() {
    List attributes = createAttributeList();
    attributes.add(createEntityAttribute("gps_type", "distance", null, null, null));
    saveGPSTrack(attributes);
}

saveGPSTrack(List attributes) {
    position = getGPSPosition();
    if (position == null) return;

    attributes.add(createEntityAttribute("gps_user", "" + user.getUserId(), null, null, null));
    attributes.add(createEntityAttribute("gps_timestamp", "" + getCurrentTime(), null, null, null));
    attributes.add(createEntityAttribute("gps_longitude", "" + position.getLongitude(), null, null, null));
    attributes.add(createEntityAttribute("gps_latitude", "" + position.getLatitude(), null, null, null));
    attributes.add(createEntityAttribute("gps_heading", "" + getGPSHeading(), null, null, null));
    attributes.add(createEntityAttribute("gps_accuracy", "" + getGPSEstimatedAccuracy(), null, null, null));
    
    positionProj = getGPSPositionProjected();

    Point p = new Point(new MapPos(positionProj.getLongitude(), positionProj.getLatitude()), null, (PointStyle) null, null);
    ArrayList l = new ArrayList();
    l.add(p);

    saveArchEnt(null, "gps_track", l, attributes);
}
```
:::
:::

The following example setups a time and distance track log and saves an
entity to the database each time the callback is triggered.

Bluetooth {#FAIMSData,UIandLogicCook-Book-Bluetooth}
=========

The following examples will show how to create a connect and communicate
to a paired Bluetooth device.

### Connect to Bluetooth device {#FAIMSData,UIandLogicCook-Book-ConnecttoBluetoothdevice}

Before  you can connect to a Bluetooth device you must pair the device.
Once you have paired the device use the following to create a
connection. In the following example when createBluetoothConnection is
called a dialog will show up to allow you to pick which Bluetooth device
to connect to. Then it will execute the callback whenever it receives
input from the Bluetooth device. You can pass in a delay value to
control when new reads from the device are initiated.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="2bf235f3-5cb0-43fb-bd2c-3b50a0068951"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
callback = "onBluetoothInput()";
delay = 1;
createBluetoothConnection(callback, delay);
 
onBluetoothInput() {
    message = getBluetoothMessage();
}
```
:::
:::

To turn off automatically reading Bluetooth messages from the device
pass in a delay of 0. e.g.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="886f6011-4f4b-4853-8e15-cb919d6cc5e3"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
callback = "onBluetoothInput()";
createBluetoothConnection(callback, 0);
```
:::
:::

### Read messages {#FAIMSData,UIandLogicCook-Book-Readmessages}

[ ]{style="color: rgb(255,51,0);"}To manually initiate a read from the
Bluetooth device use the following. This will trigger a read from the
device and execute the callback passed in when you created the
connection.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="9ca358a9-98c2-4d0d-8d93-e16763b94096"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
readBluetoothMessage();
```
:::
:::

### Write messages {#FAIMSData,UIandLogicCook-Book-Writemessages}

[ ]{style="color: rgb(255,51,0);"}To initiate a write to the
Bluetooth device use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="a5d4cf91-fc1f-4df0-9444-3b78a9e7502f"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
message = "This is a write message";
writeBluetoothMessage(message);
```
:::
:::

### Clear messages {#FAIMSData,UIandLogicCook-Book-Clearmessages}

[ ]{style="color: rgb(255,51,0);"}To clear messages currently in the
Bluetooth device buffer use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="9fede64c-f415-4517-9a64-0c9778da8049"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
clearBluetoothMessages();
```
:::
:::

Syncing {#FAIMSData,UIandLogicCook-Book-Syncing}
=======

The following examples will show how to sync the database and files with
the server and other apps.

### Pull database from server {#FAIMSData,UIandLogicCook-Book-Pulldatabasefromserver}

To pull the entire server database onto the app use the following api.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="b6732499-89b4-49ba-a909-8652426c387d"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
pullDatabaseFromServer("onComplete()");

 
onComplete() {
    showToast("finished pulling database");
}
```
:::
:::

### Push Database to server {#FAIMSData,UIandLogicCook-Book-PushDatabasetoserver}

To push the entire app database to the server use the following api.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="a967870e-b1e3-409d-a140-6150d4a443dc"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
pushDatabaseToServer("onComplete()");

 
onComplete() {
    showToast("finished pushing database");
}
```
:::
:::

### Database syncing {#FAIMSData,UIandLogicCook-Book-Databasesyncing}

To use database syncing you must first enable it using the following
code.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="81a81ced-69eb-4d67-9c02-79eb44525d9e"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
setSyncEnabled(true);
```
:::
:::

Now the database will be set to sync with the server. An indicator on
the top right will let you know when syncing is occuring. Green
indicates syncing is working as normal, Orange to indicate syncing is in
progress and Red indicates that syncing is not working.

To adjust sync intervals and delays use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="801bd396-f3d8-424a-aa77-c6632f06e7d2"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
setSyncMinInterval(10.0f);
setSyncMaxInterval(20.0f);
setSyncDelay(5.0f);
```
:::
:::

The min sync interval lets you configure the time between syncs. The
sync delay sets a period of time to delay the sync interval if the
previous sync has failed. e.g. if your sync interval is 10 seconds and
the sync delay is 5 seconds then if the sync fails then the next sync
will occur in 15 seconds and if it fails again the next sync will occur
in 20 secs etc. The sync max interval sets the limit for the maximum
sync interval. Once a sync completes successfully the sync interval is
reset the minimum sync interval.

### Stop syncing {#FAIMSData,UIandLogicCook-Book-Stopsyncing}

To stop syncing use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="93265afe-4a75-49c0-a068-7d6f818bce14"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
setSyncEnabled(false);
```
:::
:::

### Sync Event {#FAIMSData,UIandLogicCook-Book-SyncEvent}

To track sync progress in logic you can bind to the sync event.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="52942bb1-e720-4f88-9e48-9e3b0c3013f3"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
onSyncEvent("onSyncStart()", "onSyncSuccess()", "onSyncFailure()");

 
onSyncStart() {
    showToast("sync started");
}
 
onSyncSuccess() {
    showToast("sync success");
}
 
onSyncFailure() {
    showToast("sync failed");
}
```
:::
:::

### File syncing {#FAIMSData,UIandLogicCook-Book-Filesyncing}

To use file syncing you must first enable normal syncing and then enable
file syncing. Use the following to enable database syncing.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="a8f40706-ff01-4f3d-b9d6-a50bb182482d"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
setSyncEnabled(true);
setFileSyncEnabled(true);
```
:::
:::

File Attachments {#FAIMSData,UIandLogicCook-Book-FileAttachments}
================

To attach files, photos, videos and audios use the following apis.

### Saving Files to Records {#FAIMSData,UIandLogicCook-Book-SavingFilestoRecords}

To save files to an entity modify the data\_schema.xml to have the file
attribute set to true. e.g.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="76d4ac69-b337-479c-9605-2abf2cd6762e"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
    <property type="something" name="sketches" file="true">
      <bundle>DOI</bundle>
    </property>
```
:::
:::

### Image and Video Thumbnails {#FAIMSData,UIandLogicCook-Book-ImageandVideoThumbnails}

To generate a thumbnail for an image or video attribute set the
thumbnail attribute to true. e.g.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="5f659097-5a36-4f9a-aca5-f2bf1b63ae77"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
   <property type="something" name="pictures" file="true" thumbnail="true" sync="true">
      <bundle>DOI</bundle>
    </property>
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="68e1d9ff-6ea3-42f5-a9b6-ee874554e2c1"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
This is useful for entity attributes that are set to sync between
devices. By setting thumbnail to true it saves file transfers between
devices by sharing smaller thumbnail files instead of the full image or
video. By default the raw files are transferred between devices.
:::
:::

### Selecting files {#FAIMSData,UIandLogicCook-Book-Selectingfiles}

To select a file you need to bring up the file chooser popup.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="bca8746c-edaf-4a96-be79-9747af64879c"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
showFileBrowser("saveFile()");

saveFile() {
    filename = getLastSelectedFilename();
    filepath = getLastSelectedFilepath();
}
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="8e3721b1-7ea7-4d12-9588-2ff468217219"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
The filename contains only the files name where the filepath contains
the absolute path to the file.
:::
:::

### Taking Photos {#FAIMSData,UIandLogicCook-Book-TakingPhotos}

To take a photo use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="c1838803-51ad-4605-bf6a-ca1e57f2b0a0"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
openCamera("savePhoto()");

savePhoto() {
    url = getLastPictureFilePath();
}
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="3c57b096-92eb-4cd4-891a-75c9519f5a7e"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
The url is the absolute path to the file.
:::
:::

### Recording Video {#FAIMSData,UIandLogicCook-Book-RecordingVideo}

To record a video use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="8caae3db-45c3-448d-83f1-17bc133756e8"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
openVideo("saveVideo()");

saveVideo() {
    url = getLastVideoFilePath();
}
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="064ed8e6-ae79-4526-a9a4-a41be3a4e740"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
The url is the absolute path to the file.
:::
:::

### Recording Audio {#FAIMSData,UIandLogicCook-Book-RecordingAudio}

To record audio use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="fb736431-9eb6-40a9-805e-1f6c1230109d"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
recordAudio("saveAudio()");

saveAudio() {
    url = getLastAudioFilePath();
}
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="7eae1ac2-76e4-47c5-aafc-bcbe30579c75"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
The url is the absolute path to the file.
:::
:::

### Saving / Loading Files, Photos, Videos and Audio {#FAIMSData,UIandLogicCook-Book-Saving/LoadingFiles,Photos,VideosandAudio}

Here is an example to quickly setup saving photos, videos, audios and
files.

When saving files to an entity you must save each file to an attribute
with type \'file\'.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="a139573e-38f1-4738-be55-af2eedbc57f7"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
// attach files to file list view
onEvent("tabgroup1/tab1/attachFile", "attachFileTo(\"tabgroup1/tab1/files\");");
 
// attach audios to file list view
onEvent("tabgroup1/tab1/attachAudio", "attachAudioTo(\"tabgroup1/tab1/audios\");");
 
// attach picture to camera picture gallery
onEvent("tabgroup1/tab1/attachPicture", "attachPictureTo(\"tabgroup1/tab1/pictures\");");
 
// attach video to camera picture gallery
onEvent("tabgroup1/tab1/attachVideo", "attachVideoTo(\"tabgroup1/tab1/videos\");");
```
:::
:::

### View Attached Files {#FAIMSData,UIandLogicCook-Book-ViewAttachedFiles}

To view attached files for an entity or relationship used the following
api.

e.g. viewArchEntAttachedFiles

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="c5a1e6c6-1a0f-4fc9-99a5-97d7f5332ac9"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
viewArchEntAttachedFiles("10000112441409729");
```
:::
:::

This will show the attached files for an archaeological entity with
uuid 10000112441409729.

e.g. viewRelAttachedFiles

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="de387f1e-c9e3-49d1-a9aa-9acb4e6ef008"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
viewRelAttachedFiles("10000112441409730");
```
:::
:::

This will show the attached files for an relationship with
relationshipid 10000112441409730.

### Deleting Synced Files {#FAIMSData,UIandLogicCook-Book-DeletingSyncedFiles}

To delete files that have already been synced to the server in order to
clean up space on your device use the following:

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="997902ac-3b2e-43e6-ac86-683468298de1"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
cleanSyncedFiles();
```
:::
:::

This will bring up a dialog with options to delete all synced files or
all synced files which have thumbnails. It will also detail how much
space will be gained from deleting said files.

### Scan Barcodes and QR Codes {#FAIMSData,UIandLogicCook-Book-ScanBarcodesandQRCodes}

To scan a barcode or QR code and pass the result to a callback use the
following:

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="d5361137-5745-41f0-860c-53be9bb2adf2"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
scanCode("codeScannerCallback()");
 
codeScannerCallback() {
    contents = getLastScanContents();
    ...
}
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="0499c976-fd6d-4e09-babb-2c38364e61d6"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
contents is the result of the scan
:::
:::

Capturing Hardware Keyboard Events {#FAIMSData,UIandLogicCook-Book-CapturingHardwareKeyboardEvents}
==================================

To capture keyboard events from a USB device, use the following API
call:

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="2d75d1b7-47f8-4774-a3f3-f8290ce2f842"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
captureHardware("Microsoft Wired Keyboard 600", "\n", "showHardwareBuffer()");
 
showHardwareBuffer() {
    buffer = getHardwareBufferContents();
    showToast(buffer);
}
```
:::
:::

In the above example,  \"Microsoft Wired Keyboard 600\" is the name of
the device, \"\\n\" is the delimiter character used to recognise end of
input, and the final argument is the callback to be used. In this case,
the callback gets the contents of the buffer for the device using the
specified API call \'getHardwareBufferContents()\' and shows it as a
toast.

There are also two related API calls which help with discovering
attached devices. The first is used to obtain a list of all attached
input devices (Note: this includes device defaults such as soft
keyboard, volume buttons etc):

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="b5ca70d8-f020-45aa-b7c0-c011fe9e405a"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
getHardwareDevices()
```
:::
:::

The second turns on debug mode which displays a toast of the device name
every time an input is received. This can be used during module creation
to discover the names of attached input devices:

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="11fe6a31-0c56-4cfa-b649-f865cae4b27c"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
debugHardwareDevices(true);
```
:::
:::

The default for this is false, so only needs to be specified to turn
this feature on.

Misc {#FAIMSData,UIandLogicCook-Book-Misc}
====

### Set User {#FAIMSData,UIandLogicCook-Book-SetUser}

Use the following api to set the current user of the app.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="15bdfcdf-5725-4dc4-bfb9-eb02ca153958"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
// create a new user with id 1, with first and last names
user = new User("1", "John", "Doe", "John@john.com");
setUser(user);
```
:::
:::

### Execute code {#FAIMSData,UIandLogicCook-Book-Executecode}

Use the following to execute code.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="fd0f3ebd-99d2-4693-9a4c-4b248ca08905"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
callback = "showToast(\"this is a test\")";
execute(callback);
```
:::
:::

Users {#FAIMSData,UIandLogicCook-Book-Users}
=====

### Enabling User Signup Example {#FAIMSData,UIandLogicCook-Book-EnablingUserSignupExample}

Firstly, define the Signup UI elements in ui\_schema.xml so the \'Sign
up\' button appears in the User tab along with the \'Select User\'
dropdown.  This can be given a language specific label using the
\'Signup\' label name in the relevant Arch16n language files as shown
below.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="e681e77d-4a3f-49b9-8095-b66c27d4d7a1"}
::: {.codeHeader .panelHeader .pdl style="border-bottom-width: 1px;"}
**ui\_schema.xml**
:::

::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: xml; gutter: false; theme: Confluence" data-theme="Confluence"}
<User>
  <User>
    <Select_User/>
    <Signup/>
  </User>
</User>

...
<group ref="User">
  <label>{User}</label>
  <group ref="User">
    <label>{User}</label>
    <select1 ref="Select_User">
      <label>{Select_User}</label>
      <item>
        <label>Options not loaded</label>
        <value>0</value>
      </item>
    </select1>
    <trigger ref="Signup">
      <label>{Signup}</label>
    </trigger>
  </group>
</group>
```
:::
:::

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="d45c78c4-4f7e-4689-bd54-307339770cce"}
::: {.codeHeader .panelHeader .pdl style="border-bottom-width: 1px;"}
**english.0.properties**
:::

::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
Signup=Sign up
```
:::
:::

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="aee577de-e16b-434d-9dbd-fad05541d047"}
::: {.codeHeader .panelHeader .pdl style="border-bottom-width: 1px;"}
**spanish.0.properties**
:::

::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
Signup=Regístrate
```
:::
:::

\

Secondly, implement the logic to drive the new button element and cause
the user signup dialog to be displayed when it is clicked, as well as
re-populate the Select User dropdown if account creation is successful

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="c8bb3828-ffa2-4ac1-a001-234d6d1fb143"}
::: {.codeHeader .panelHeader .pdl style="border-bottom-width: 1px;"}
**ui\_logic.bsh**
:::

::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
addOnEvent("User/User/Signup", "click", "onClickUserSignup()");

onClickUserSignup () {
  showCreateUserDialog("populateListForUsers()");
}
```
:::
:::

\

### Enabling User Authentication Example {#FAIMSData,UIandLogicCook-Book-EnablingUserAuthenticationExample}

Add a Login button UI element to ui\_schema.xml and its related trigger
definition.  This can also be labelled via Arch16n as with the Sign Up
button in the section above using the Login label name.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="fba68594-68ef-4a58-9bac-3acfe7fb7c7a"}
::: {.codeHeader .panelHeader .pdl style="border-bottom-width: 1px;"}
**ui\_schema.xml**
:::

::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: xml; gutter: false; theme: Confluence" data-theme="Confluence"}
<User>
  <User>
    <Select_User/>
    <Login/>
    <Signup/>
  </User>
</User>
...
<group ref="User">
  <label>{User}</label>
  <group ref="User">
    <label>{User}</label>
    <select1 ref="Select_User">
      <label>{Select_User}</label>
      <item>
        <label>Options not loaded</label>
        <value>0</value>
      </item>
    </select1>
    <trigger ref="Login">
      <label>{Login}</label>
    </trigger>
    <trigger ref="Signup">
      <label>{Signup}</label>
    </trigger>
  </group>
</group>
```
:::
:::

\

In the module logic, ensure selectUser() retrieves the password and
email fields.  This will be needed by the authentication dialog to
verify the user provided password matches.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="bd8aa791-12c2-4c23-bf56-dbdf7d754131"}
::: {.codeHeader .panelHeader .pdl style="border-bottom-width: 1px;"}
**ui\_logic.bsh**
:::

::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
selectUser () {
  String userVocabId  = getFieldValue(userMenuPath);
  if (isNull(userVocabId))
    return;

  String userQ        = "SELECT userid,fname,lname,email,password FROM user " +
                        "WHERE  userid='" + userVocabId + "';";
  FetchCallback callback = new FetchCallback() {
    onFetch(result) {
      user = new User(
            result.get(0),
            result.get(1),
            result.get(2),
            result.get(3),
            result.get(4)
      );
      setUser(user);
      username = result.get(1) + " " + result.get(2);
    }
  };

  fetchOne(userQ, callback);
}
```
:::
:::

\

Additionally, implement the logic to drive the Login button and define
the callback to run when authentication is successful

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="3a8b9a3e-8ba3-4a62-a785-8fbf25ee72ec"}
::: {.codeHeader .panelHeader .pdl style="border-bottom-width: 1px;"}
**ui\_logic.bsh**
:::

::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
addOnEvent("User/User/Login", "click", "onClickUserLogin()");


onClickUserLogin () {
  showVerifyUserDialog("doUserLogin()");
}


doUserLogin () {
  newTab("Control", true);
}
```
:::
:::

\

Validation {#FAIMSData,UIandLogicCook-Book-Validation}
==========

Adding a validation schema file to the module will allow you to validate
your database records on the server and propagate them to the apps.

Here is an example of a validation schema.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="db6f3c72-6742-4102-bc29-1c174e675027"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<ValidationSchema>

     <RelationshipElement name='AboveBelow'>

        <property name='name'>

            <validator type='evaluator' cmd='spell.sh ?'>
              <cmd><![CDATA[spell.sh ?]]></cmd>
              <param type='field' value='freetext' />
            </validator>

            <!--<validator type='evaluator' cmd='spell.sh ?'>
                <param type='query' value="select freetext from relnvalue join attributekey using (attributeid) where relationshipid = ? and relnvaluetimestamp = ? and attributename = 'name';" />
            </validator>-->

            <!--<validator type='evaluator' cmd='spell.sh ? ?'>
            <param type='field' value='freetext' />
                <param type='query' value="select freetext from relnvalue join attributekey using (attributeid) where relationshipid = ? and relnvaluetimestamp = ? and attributename = 'name';" />
            </validator>-->

            <validator type='blankchecker'>
                <param type='field' value='freetext' />
            </validator>

            <!--<validator type='blankchecker'>
                <param type='query' value="select freetext from relnvalue join attributekey using (attributeid) where relationshipid = ? and relnvaluetimestamp = ? and attributename = 'name';"/>
            </validator>-->

            <!--<validator type='blankchecker'>
                <param type='field' value='freetext' />
                <param type='query' value="select freetext from relnvalue join attributekey using (attributeid) where relationshipid = ? and relnvaluetimestamp = ? and attributename = 'name';" />
            </validator>-->

            <validator type='typechecker' datatype='text'>
                <param type='field' value='freetext' />
            </validator>

            <!--<validator type='typechecker' datatype='text'>
                <param type='query' value="select freetext from relnvalue join attributekey using (attributeid) where relationshipid = ? and relnvaluetimestamp = ? and attributename = 'name';" />
            </validator>-->

            <!--<validator type='typechecker' datatype='text'>
                <param type='field' value='freetext' />
                <param type='query' value="select freetext from relnvalue join attributekey using (attributeid) where relationshipid = ? and relnvaluetimestamp = ? and attributename = 'name';" />
            </validator>-->

            <validator type='querychecker'>
              <query><![CDATA[select length(?) < 20, 'Field value is too long']]></query>
                <param type='field' value='freetext' />
            </validator>

            <!--<validator type='querychecker'>
                <query><![CDATA[select length(?) < 20, 'Field value is too long']]></query>
                <param type='query' value="select freetext from relnvalue join attributekey using (attributeid) where relationshipid = ? and relnvaluetimestamp = ? and attributename = 'name';" />
            </validator>-->

            <!--<validator type='querychecker'>
                <query><![CDATA[select length(?) < 20 AND ? like 'Test', 'Field value is too long and does not contain Test']]></query>
                <param type='field' value='freetext' />
                <param type='query' value="select freetext from relnvalue join attributekey using (attributeid) where relationshipid = ? and relnvaluetimestamp = ? and attributename = 'name';" />
            </validator>-->

        </property>

        <property name='location'>
            <validator type='blankchecker'>
                <param type='field' value='vocab' />
            </validator>
        </property>

    </RelationshipElement>

    <ArchaeologicalElement name='small'>

        <property name='name'>

            <validator type='evaluator' cmd='spell.sh ?'>
                <param type='field' value='freetext' />
            </validator>

            <!--<validator type='evaluator' cmd='spell.sh ?'>
                <param type='query' value="select freetext from aentvalue join attributekey using (attributeid) where uuid = ? and valuetimestamp = ? and attributename = 'name';" />
            </validator>-->

            <!--<validator type='evaluator' cmd='spell.sh ? ?'>
                <param type='field' value='freetext' />
                <param type='query' value="select freetext from aentvalue join attributekey using (attributeid) where uuid = ? and valuetimestamp = ? and attributename = 'name';" />
            </validator>-->

            <validator type='blankchecker'>
                <param type='field' value='freetext' />
            </validator>

            <!--<validator type='blankchecker'>
                <param type='query' value="select freetext from aentvalue join attributekey using (attributeid) where uuid = ? and valuetimestamp = ? and attributename = 'name';" />
            </validator>-->

            <!--><validator type='blankchecker'>
                <param type='field' value='freetext' />
                <param type='query' value="select freetext from aentvalue join attributekey using (attributeid) where uuid = ? and valuetimestamp = ? and attributename = 'name';" />
            </validator>-->

            <validator type='typechecker' datatype='text'>
                <param type='field' value='freetext' />
            </validator>

            <!--<validator type='typechecker' datatype='text'>
                <param type='query' value="select freetext from aentvalue join attributekey using (attributeid) where uuid = ? and valuetimestamp = ? and attributename = 'name';" />
            </validator>-->

            <!--<validator type='typechecker' datatype='text'>
                <param type='field' value='freetext' />
                <param type='query' value="select freetext from aentvalue join attributekey using (attributeid) where uuid = ? and valuetimestamp = ? and attributename = 'name';" />
            </validator>-->

            <validator type='querychecker'>
                <query><![CDATA[select length(?) < 20, 'Field value is too long']]></query>
                <param type='field' value='freetext' />
            </validator>

            <!--<validator type='querychecker' query="select length(?) < 20, 'Field value is too long'" >
                <query><![CDATA[select length(?) < 20, 'Field value is too long']]></query>
                <param type='query' value="select freetext from aentvalue join attributekey using (attributeid) where uuid = ? and valuetimestamp = ? and attributename = 'name';" />
            </validator>-->

            <!--<validator type='querychecker' query="select length(?) < 20 AND ? like 'Test', 'Field value is too long and does not contain Test'" >
                <query><![CDATA[select length(?) < 20 AND ? like 'Test', 'Field value is too long and does not contain Test']]></query>
                <param type='field' value='freetext' />
                <param type='query' value="select freetext from aentvalue join attributekey using (attributeid) where uuid = ? and valuetimestamp = ? and attributename = 'name';" />
            </validator>-->

        </property>

        <property name='value'>
            <validator type='blankchecker'>
                <param type='field' value='measure' />
                <param type='field' value='certainty' />
            </validator>

            <validator type='typechecker' datatype='real'>
                <param type='field' value='measure' />
            </validator>

            <validator type='typechecker' datatype='real'>
                <param type='field' value='certainty' />
            </validator>
        </property>

        <property name='location'>
            <validator type='blankchecker'>
                <param type='field' value='vocab' />
            </validator>
        </property>

    </ArchaeologicalElement>

</ValidationSchema>
```
:::
:::

### How it works {#FAIMSData,UIandLogicCook-Book-Howitworks.2}

To specify validation for a relationship or archaeological entity
defined in the data schema you simply need add validation on the
corresponding elements in the validation schema.

e.g. add validation for the AboveBelow relationship

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="dd97ec23-e8f4-48f4-ae08-a144cca0e9c9"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
    <RelationshipElement name='AboveBelow'>
...
```
:::
:::

e.g. add validation for the small archaeological entity

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="37899c1c-ee08-49f9-9762-a5d7bf5bcc3c"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
    <ArchaeologicalElement name='small'>
...
```
:::
:::

To add validation to a property of a relationship or archaeological
entity do the following.

e.g. add validation to the name property of relationship

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="b6a80a80-6a2d-4cf3-8f3c-d80802c1e98e"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
    <RelationshipElement name='AboveBelow'>

        <property name='name'>
...
```
:::
:::

e.g. add validation to the name property of archaeological entity

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="51870f94-1649-45ac-afe4-e970e3325330"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
    <ArchaeologicalElement name='small'>

        <property name='name'>
...
```
:::
:::

There are four type of validators you can use. To use an validator you
need to specify the type and the params for the validator 

e.g 

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="ce324e3b-6cde-43d5-a6ec-a82ff9c6e2da"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
            <validator type='evaluator' cmd='spell.sh ?'>
                <param type='field' value='freetext' />
            </validator>
...
```
:::
:::

Here the validator is an evaluator which takes a command. The ? in the
command is replaced by the param. Params can be type field which takes
freetext, certainty, vocab and measure (for archaeologial entities only)
or queries which run query to return a value. You can also specify
multiple params for a single evaluator.

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="00115a97-ea8e-4979-80a7-2572c082a44b"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Examples have been provided above in the commented our sections.
:::
:::

### Evaluator {#FAIMSData,UIandLogicCook-Book-Evaluator}

This runs a program against the given params

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="b402f345-aa95-4163-84a8-f0b8ede751b9"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Examples have been provided above in the commented out sections.
:::
:::

### Blank Checker {#FAIMSData,UIandLogicCook-Book-BlankChecker}

This checks if the values are not null, or an empty string against the
given params

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="29e3d244-606d-4f77-a181-f0631f168d4b"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Examples have been provided above in the commented out sections.
:::
:::

### Type Checker {#FAIMSData,UIandLogicCook-Book-TypeChecker}

This checks if the values are integer, real or text against the given
params.

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="1ddcc1f6-e9b4-434b-8d6c-94cfc1fc22b7"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Examples have been provided above in the commented out sections.
:::
:::

### Query Checker {#FAIMSData,UIandLogicCook-Book-QueryChecker}

This checks if the values are valid when running a query against the
given params.

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="640214d5-1a1c-4fac-948e-95190ed42e84"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
::: {.tk .Sn}
::: {.Tn}
::: {.KL}
::: {.PD .IF style="margin-left: 4.0px;"}
::: {.JL}
::: {.Mu .SP}
::: {.tL8wMe .xAWnQc}
if your query returns nothing it fails
:::
:::
:::
:::
:::
:::
:::

::: {.tk .Sn}
::: {.Tn}
::: {.KL}
::: {.PD .IF style="margin-left: 4.0px;"}
::: {.JL}
::: {.Mu .SP}
::: {.tL8wMe .xAWnQc}
you probably need to do a count
:::
:::
:::
:::
:::
:::
:::

::: {.tk .pj}
::: {.Tn}
::: {.KL}
::: {.PD .IF}
::: {.JL}
::: {.Mu .SP}
::: {.tL8wMe .xAWnQc}
it has to return something
:::
:::

::: {.Mu .SP}
::: {.tL8wMe .xAWnQc}
the second argument is the \"failure string\"
:::
:::

::: {.Mu .SP}
::: {.tL8wMe .xAWnQc}
the first argument resolve to 0 / non-zero?
:::
:::
:::
:::
:::
:::
:::

::: {.tk .Sn}
::: {.Tn}
::: {.KL}
::: {.PD .IF style="margin-left: 4.0px;"}
::: {.JL}
::: {.Mu .SP}
::: {.tL8wMe .xAWnQc}
if the first value is false then it raises an error
:::
:::

::: {.Mu .SP}
::: {.tL8wMe .xAWnQc}
or causes the validator to output the second value which is the error
string
:::
:::
:::
:::
:::
:::
:::

::: {.tk .pj}
::: {.Tn}
::: {.KL}
::: {.PD .IF}
::: {.JL}
::: {.Mu .SP}
::: {.tL8wMe .xAWnQc}
okay. And can this be in the \"inner\" query?
:::
:::

::: {.Mu .SP}
::: {.tL8wMe .xAWnQc}
or do I need to write an outer query?
:::
:::
:::
:::
:::
:::
:::

::: {.tk .Sn}
::: {.Tn}
::: {.KL}
::: {.PD .IF style="margin-left: 4.0px;"}
::: {.JL}
::: {.Mu .SP}
::: {.tL8wMe .xAWnQc}
so when you construct a validator of type queryChecker
:::
:::

::: {.Mu .SP}
::: {.tL8wMe .xAWnQc}
the query you pass needs to be column1 (with correct\|0 for not correct)
and column2 with (validation string)
:::
:::
:::
:::
:::
:::
:::

::: {.tk .pj}
::: {.Tn}
::: {.KL}
::: {.PD .IF}
::: {.JL}
::: {.Mu .SP}
::: {.tL8wMe .xAWnQc}
the query I pass with \<query\> foo \</query\> ?
:::
:::
:::
:::
:::
:::
:::

::: {.tk .Sn}
::: {.Tn}
::: {.KL}
::: {.PD .IF style="margin-left: 4.0px;"}
::: {.JL}
::: {.Mu .SP}
::: {.tL8wMe .xAWnQc}
its inputs are the param values
:::
:::
:::
:::
:::
:::
:::

::: {.tk .pj}
::: {.Tn}
::: {.KL}
::: {.PD .IF}
::: {.JL}
::: {.Mu .SP}
::: {.tL8wMe .xAWnQc}
so therefore, to pass uuid as an input, I have to do the shennagans
I\'ve already done (a param that exports the uuid)
:::
:::
:::
:::
:::
:::
:::

::: {.tk .pj}
::: {.Tn}
::: {.KL}
::: {.PD .IF}
::: {.JL}
::: {.Mu .SP}
::: {.tL8wMe .xAWnQc}
And query=\"foo\" is equivalent to the query tag
:::
:::
:::
:::
:::
:::
:::

::: {.tk .Sn}
::: {.Tn}
::: {.KL}
::: {.PD .IF style="margin-left: 4.0px;"}
::: {.JL}
::: {.Mu .SP}
::: {.tL8wMe .xAWnQc}
yes the element is better because you can use cdata which handle any
string data where as the attribute string has restrictions on it 
:::
:::
:::
:::
:::
:::
:::

::: {.tk .Sn}
::: {.Tn}
::: {.KL}
::: {.PD .IF style="margin-left: 4.0px;"}
::: {.JL}
::: {.Mu .SP}
::: {.tL8wMe .xAWnQc}
just lookup xml attribute string restrictions
:::
:::
:::
:::
:::
:::
:::

::: {.tk .pj}
::: {.Tn}
::: {.TlvAYc style="text-align: right;"}
[[Now]{.nu4ufe}]{.Lq}
:::
:::
:::
:::
:::

CSS Styling {#FAIMSData,UIandLogicCook-Book-CSSStyling}
===========

Adding a css styling file to the module will allow you to customise the
look and layout of views inside the module. 

Here is an example of a css styling file.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="019722f7-f267-4920-ae2e-4b2efef921ea"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
.gallery {
  background-color:red;
}
.gallery-item {
  background-color:green;
}
 
.button {
  background-image:url("http://images.com/sample.png");
}
 
.custom {
  width:75%
}
 
#tabgroup1/tab1/save {
  border:2px solid purple;
}
#tabgroup1/tab1/save-label {
  font-size:24px;
}
#tabgroup1/tab1/clear {
  border:2px solid #CF1B1B;
}
```
:::
:::

### Selecting views {#FAIMSData,UIandLogicCook-Book-Selectingviews}

To add styling to views you just need to add the desired styling to the
selector of the view. A view can be selected in 3 different ways:

-   class name
-   id reference
-   custom class name

e.g. by class name

Every view is designated a standard class name according to what type of
view it is. Styling a standard class name will style all views matching
this class name. The list of mappings between views and class names, and
what stylings work for each are:

::: {.table-wrap}
+-----------------------+-----------------------+-----------------------+
| Class name            | Views                 | Stylings that work    |
|                       |                       | for this view         |
+=======================+=======================+=======================+
| button                | Any standard button   | all                   |
|                       | trigger               |                       |
+-----------------------+-----------------------+-----------------------+
| label                 | Any view labels       | all                   |
+-----------------------+-----------------------+-----------------------+
| label-icon            | And                   | all except text       |
|                       | annotation/certainty/ | stylings              |
|                       | info                  |                       |
|                       | icons for labels      |                       |
|                       | (this does not        |                       |
|                       | include those for     |                       |
|                       | individual files in   |                       |
|                       | file lists/galleries) |                       |
+-----------------------+-----------------------+-----------------------+
| input-field           | text fields, integer  | all                   |
|                       | text fields etc.      |                       |
+-----------------------+-----------------------+-----------------------+
| text-area             | Text area             | all                   |
+-----------------------+-----------------------+-----------------------+
| gallery               | Picture galleries,    | backgrounds, text     |
|                       | hierarchical picture  | stylings (Note:       |
|                       | galleries             | Definitely avoid      |
|                       |                       | widths/margins, can   |
|                       |                       | cause display issues  |
|                       |                       | with galleries)       |
+-----------------------+-----------------------+-----------------------+
| gallery-item          | All items in the      | backgrounds, borders  |
|                       | galleries above       |                       |
+-----------------------+-----------------------+-----------------------+
| file-gallery          | camera galleries,     | backgrounds, text     |
|                       | video galleries       | stylings              |
+-----------------------+-----------------------+-----------------------+
| file-gallery-item     | All items in the      | backgrounds, borders  |
|                       | galleries above       |                       |
+-----------------------+-----------------------+-----------------------+
| file-list             | file lists            | backgrounds, text     |
|                       |                       | stylings              |
+-----------------------+-----------------------+-----------------------+
| file-list-item        | All items in file     | backgrounds, borders  |
|                       | lists                 |                       |
+-----------------------+-----------------------+-----------------------+
| dropdown              | Dropdowns,            | all (text stylings    |
|                       | hierarchical          | don\'t work for       |
|                       | dropdowns             | hierarchical          |
|                       |                       | dropdowns)            |
+-----------------------+-----------------------+-----------------------+
| checkbox-group        | Group of checkboxes   | backgrounds, borders, |
|                       | NB: file list groups  | text styings          |
|                       | don\'t have a class   |                       |
+-----------------------+-----------------------+-----------------------+
| checkbox              | Any checkbox inside a | backgrounds, borders, |
|                       | checkbox group or     | text stylings         |
|                       | file list group       |                       |
+-----------------------+-----------------------+-----------------------+
| radio-group           | Groups of radio       | backgrounds, borders, |
|                       | buttons               | text styings          |
+-----------------------+-----------------------+-----------------------+
| radio-button          | Any radio button      | backgrounds, borders, |
|                       | inside a radio group  | text stylings         |
+-----------------------+-----------------------+-----------------------+
| list                  | List views            | all (large paddings   |
|                       |                       | can be temperamental  |
|                       |                       | at times, heights     |
|                       |                       | should not be larger  |
|                       |                       | than tab height e.g.  |
|                       |                       | 100% with other stuff |
|                       |                       | above/below)          |
+-----------------------+-----------------------+-----------------------+
| date-picker           | Date picker views     | all                   |
+-----------------------+-----------------------+-----------------------+
| time-picker           | Time picker views     | all                   |
+-----------------------+-----------------------+-----------------------+
| web-view              | HTML web views        | margins, height,      |
|                       |                       | width                 |
+-----------------------+-----------------------+-----------------------+
| table-view            | table views. NB: This | margins, height,      |
|                       | only styles the table | width                 |
|                       | view container, not   |                       |
|                       | the table itself, see |                       |
|                       | below for styling     |                       |
|                       | tables                |                       |
+-----------------------+-----------------------+-----------------------+
:::

Examples of this can be seen in the example CSS styling file above.

\

e.g. by id reference

Views can also be individually styled using their reference id as
specified in the UI schema. This is done by a hash followed by the id,
with labels having \"-label\" appended:

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="1b955cbe-5693-439a-bff7-91830b183f6f"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
#tabgroup1/tab1/save {
  border:2px solid black
}
#tabgroup1/tab1/save-label {
  font-size:30px;
}
```
:::
:::

\

e.g. by custom class name

Views can also be assigned a class name in the UI schema. This can then
be used to style a number of different views with the same styling. A
class name can be assigned by adding a \"faims\_style\_class\" attribute
to a view. Labels for this view will have the same class name but with
\"-label\" appended:

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="82c8b358-b535-4dd2-a807-44c156ca0c83"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<trigger ref="save" faims_style_class="save">
  <label>Save</label>
</trigger>
```
:::
:::

Views can then be styled in the same way regular class names are i.e.
full stop followed by the class name:

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="3f5d2748-bbab-4e6d-a82e-52006feb9248"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
.save {
  // styling
}
 
.save-label {
  // styling
}
```
:::
:::

\

### Applying Styling {#FAIMSData,UIandLogicCook-Book-ApplyingStyling}

There are a number of different types of styling that can be applied to
a view. These are:

-   background-color, background-image
-   margin, margin-left, margin-top
-   border, border-left, border-left-color, border-left-width etc.
-   padding, padding-left, padding-top, padding-bottom, padding-right
-   height, width
-   color
-   text-align
-   text-transform(uppercase, lowercase, capitalize)
-   text-shadow
-   font-family, font-size, font-style, font-weight

### Styling Table Views {#FAIMSData,UIandLogicCook-Book-StylingTableViews}

Table views cannot be styled using the same method as above. To style a
table view, you can use the styleTable API call, passing in a css file.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="f475b7a5-47f5-4636-8e9a-587807353a06"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
css = getAttachedFilePath("files/app/table.css");
styleTable("tabgroup5/tab1/table", css);
```
:::
:::

\

Arch16n translations {#FAIMSData,UIandLogicCook-Book-Arch16ntranslations}
====================

Adding Arch16n properties file to the module will allow you to translate
reserved terms in view labels, buttons, popup messages and vocabulary.
You can add a single file or a tarball of multiple files. For multiple
arch16n properties files, each file inside the tarball must have a
\'.properties\' extension. The user will see a dropdown on the app prior
to loading the module where they can select the desired arch16n file to
use. This dropdown can be sorted by applying a sort order in the
filenames of the files in the form:
\"\<name\>.\<sort\_order\>.properties\". For example:

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="f62b71a8-2c7f-4a25-8b52-342f8e8c487b"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
orthodox.2.properties
unorthodox.3.properties
default.1.properties
```
:::
:::

The above set of arch16n files would appear in the dropdown as Default,
Orthodox, Unorthodox, based on the sort orders of 1, 2, 3

\

Below is an example of an arch16n file.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="16d224e0-27ce-4df5-8bfa-9c32b3d8c510"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
entity=Arch16n Entity
name=Arch16n Name
value=Arch16n Value
superA=Arch16n Super A
superB=Arch16n Super B
superC=Arch16n Super C
superD=Arch16n Super D
locationA=Arch16n Location A
locationB=Arch16n Location B
locationC=Arch16n Location C
locationD=Arch16n Location D
typeA=Arch16n Type A
typeB=Arch16n Type B
typeC=Arch16n Type C
typeD=Arch16n Type D
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="2f7d79e1-2229-4406-b2e8-f73d7d7cac57"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
This is a standard java properties file so make sure the left hand side
of the equals contains no spaces.
:::
:::

To replace terms in the ui schema use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="4f63b13d-1dfa-4146-b2a9-ddb7026a4be8"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
...
 <group ref="tabgroup1" faims_archent_type="simple">
      <label>Simple Entity Example</label>
      <group ref="tab1">
        <label>{entity} Tab1</label>
        <input ref="name" faims_attribute_name="name" faims_attribute_type="freetext">
          <label>{name}:</label>
        </input>
...
```
:::
:::

In this example {entity} will be replaced by Arch16n Entity and {name}
will be replaced by Arch16n name.

To replace terms in the data schema use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="82c6dad2-8734-45eb-8ca1-ec9a34480f99"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
 ...
<property type="checklist" name="type">
      <bundle>DOI</bundle>
      <lookup>
        <term>{typeA}</term>
        <term>{typeB}</term>
        <term>{typeC}</term>
        <term>{typeD}</term>
      </lookup>
    </property>
...
```
:::
:::

In this example {typeA} will be replaced by Arch16n Type A.

To replace terms in the ui logic use the following.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="a7536fe2-1815-47d9-a346-5beed8855b4f"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
setFieldValue("tabgroup1/tab1/name","{typeC}")
```
:::
:::

In this example the name field will be set the value Arch16n Type C.

Exporters {#FAIMSData,UIandLogicCook-Book-Exporters}
=========

To create an exporter to install you will need to create a tarball with
the following:

-   parent folder
    -   config.json

    <!-- -->

    -   install.sh 
    -   uninstall.sh
    -   export.sh

### config.json {#FAIMSData,UIandLogicCook-Book-config.json}

This file contains the configuration properties of the exporter
specified as json. The properties include:

-   name: A string to represent the name of the exporter (required)
-   version: An int to represent version of the exporter. Exporters can
    be upgraded using the version value. (required) 
-   key: A string to represent the unique id of the exporter (required)
-   interface: An array of items to be displayed as the exporter
    interface. The options are text, checkbox and dropdown.

e.g.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="579d07b3-01c1-47ff-8bad-a7ea935e4436"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
{
  "name":"Exporter Test",
  "version":1,
  "key":"3e4be0f3-8ba5-434c-9603-7a5962a94bd9",
  "interface":[
    {
      "type":"text",
      "label":"Label1",
      "required":true
    },
    {
      "type":"checkbox",
      "label":"Label2",
      "items":[
        "Item1",
        "Item2"
      ]
    },
    {
      "type":"dropdown",
      "label":"Label3",
      "items":[
        "Item1",
        "Item2",
        "Item3"
      ],
      "default":"Item2"
    }
  ]
}
```
:::
:::

Textboxes require just a label, and can take in an optional argument
defining if it\'s required or not

Checkboxes require a label and an array of items.

Dropdowns require a label and an array of items, and can take in an
optional argument defining the default value

The above interface could produce a JSON file akin to the following to
parse to the export script:

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="925675c7-4c72-4f28-9490-7ce8af9580ee"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
{"Label1":"some text","Label2":["Item1","Item2"],"Label3":"Item2"}
```
:::
:::

\

### install.sh {#FAIMSData,UIandLogicCook-Book-install.sh}

To add custom actions to install the exporter added them to this script.
This will be executed after the exporter is installed on the web server.

### uninstall.sh {#FAIMSData,UIandLogicCook-Book-uninstall.sh}

To add custom actions to uninstall the exporter add them to this script.
This will be executed before the exporter is uninstalled from the web
server.

### export.sh {#FAIMSData,UIandLogicCook-Book-export.sh}

This script will be called to export the module on the web server. The
script can expect the following arguments in order.

-   Module directory (this is a file path)
-   JSON file containing the inputs from the interface of the exporter
    (this is a file path)
-   Location where the exporter can copy a file which will be downloaded
    after the exporter has completed (this is a directory path, expects
    just one file to be put in here)
-   Location where the exporter can copy a file which will be rendered
    on the server using markdown after the exporter has completed (this
    is a file path)

e.g.

 

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="fbaf5d1d-0574-4443-9b3d-f4bc196c70b7"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
#!/bin/bash
 
# $1 module directory e.g. /var/www/faims/modules/b28ea04f-2e6b-421a-a3fd-8be4c6c50259
# $2 user entered data as json file e.g.  /tmp/something.json => {"Label1":"some text","Label2":["Item1","Item2"],"Label3":"Item2"} 
# $3 directory to put generated files in e.g. /tmp/exported_files
# $4 file to write markdown text into e.g. /tmp/mark_down.txt => h3. Traditional html title
 
# read json interface input file into string
json = ruby parse_json.rb $2
 
# export database to csv using json inputs and pass output into export file inside download directory
python export.py $1/db.sqlite3 json > $3/export.csv
 
# generate markup and pass output to markup file
echo "Exported **CSV**" >> $4
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="a1f31b3d-4070-4709-9434-50f483512a45"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-error
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Do not copy the db.sqlite3 file inside the module directory directly as
the database can change at any time. Please read the contents of the
database into another database via sqlite.
:::
:::

### Update Exporter {#FAIMSData,UIandLogicCook-Book-UpdateExporter}

To update an exporter just update the files and set the version number
to a higher number. Then re-tar the exporter and upload it to the
server.

### Create Self-Updating Exporter {#FAIMSData,UIandLogicCook-Book-CreateSelf-UpdatingExporter}

It is possible to create an exporter that can be updated via the
plugin-manager without the need to re-upload a new tarball.

1.  Create a public github repository for the exporter.
2.  Clone the repository using the https remote option and add your
    exporter files to it.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="7539bdc8-beb6-4ba9-9b20-f615131806d9"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
git clone https://github.com/<Account>/exporter-test.git
cd exporter-test
# add your exporter files
git commit -a -m "initial commit"
git push -u origin master
```
:::
:::

3\. Tar the exporter and upload it to the server.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="636b1845-dc99-46d5-8134-f52366f6bf30"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
cd ..
tar jcf exporter-test.tar.gz exporter-test
```
:::
:::

4\. Now you can update the exporter at anytime by pressing the update
button in the plugin-manager. This will pull from the master branch the
latest changes and re-run the installer on the exporter.

Attribute Format String {#FAIMSData,UIandLogicCook-Book-AttributeFormatString}
=======================

The attribute format string allows you to control how each attribute in
an entity is display on both the server and android. First you will need
to define an attribute format string, explained below, and set
the formatString option for the attribute in the data schema to the
format you want. e.g. In your data schema you can have the following
format string for the name attribute.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="372985a7-dcc6-494a-8594-0f359847ce41"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<property name="name" type="string">
<formatString><![CDATA[ {{ if $1 then "( $1 )" }} ]]></formatString>
</property>
```
:::
:::

Appending Character String {#FAIMSData,UIandLogicCook-Book-AppendingCharacterString}
--------------------------

For attributes that have multiple values you can specify how to append
that attributes together using the data schema as below.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="c636f41f-066a-4e40-97c5-2b944695a5d1"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<property name="name" type="string">
<formatString><![CDATA[ {{if $1 then "( $1 )" }} ]]></formatString>
<appendCharacterString><![CDATA[ & ]]></appendCharacterString>
</property>
```
:::
:::

Format String Syntax {#FAIMSData,UIandLogicCook-Book-FormatStringSyntax}
--------------------

Each attribute format string must conform to a confined syntax and
grammar. A format string is composed of a plain text combined with
conditional statements and variable substitution. Below are some
examples.

::: {.table-wrap}
+-------------+-------------+-------------+-------------+-------------+
| Example     | Description | Variables   | Format      | Result      |
|             |             |             | String      |             |
+=============+=============+=============+=============+=============+
| Plain text  | A format    | \           | Hello World | Hello World |
|             | string with |             |             |             |
|             | no          |             |             |             |
|             | conditions  |             |             |             |
|             | or          |             |             |             |
|             | variables.  |             |             |             |
|             | This format |             |             |             |
|             | string will |             |             |             |
|             | allows      |             |             |             |
|             | output the  |             |             |             |
|             | plain text  |             |             |             |
|             | from the    |             |             |             |
|             | format      |             |             |             |
|             | string for  |             |             |             |
|             | every       |             |             |             |
|             | attribute   |             |             |             |
|             | (not very   |             |             |             |
|             | useful).    |             |             |             |
+-------------+-------------+-------------+-------------+-------------+
| Plain text  | To use data | \$1 =\>     | Hello \$1   | Hello World |
| with        | from the    | World       |             |             |
| variables   | attribute   |             |             |             |
|             | within your |             |             |             |
|             | format      |             |             |             |
|             | string you  |             |             |             |
|             | can use     |             |             |             |
|             | variable    |             |             |             |
|             | substitutio |             |             |             |
|             | n.          |             |             |             |
|             | You are     |             |             |             |
|             | given 4     |             |             |             |
|             | variables   |             |             |             |
|             | to use      |             |             |             |
|             | within your |             |             |             |
|             | format      |             |             |             |
|             | string      |             |             |             |
|             | which map   |             |             |             |
|             | to the data |             |             |             |
|             | in your     |             |             |             |
|             | attribute   |             |             |             |
|             |             |             |             |             |
|             | i.e. \$1    |             |             |             |
|             | =\>         |             |             |             |
|             | Vocabname,  |             |             |             |
|             | \$2 =\>     |             |             |             |
|             | Measure,    |             |             |             |
|             | \$3 =\>     |             |             |             |
|             | Freetext    |             |             |             |
|             | and \$4 =\> |             |             |             |
|             | Certainty   |             |             |             |
+-------------+-------------+-------------+-------------+-------------+
| Plain Text  | A format    | \$1 =\> Foo | (\$1) \$2,  | (Foo) Bar,  |
| with        | string can  |             | \$3, \$4    | Something,  |
| multiple    | reference   | \$2 =\> Bar | (\$1)       | Else (Foo)  |
| variables   | multiple    |             |             |             |
|             | variables   | \$3 =\>     |             |             |
|             | and can     | Something   |             |             |
|             | reference   |             |             |             |
|             | the same    | \$4 =\>     |             |             |
|             | variable    | Else        |             |             |
|             | multiple    |             |             |             |
|             | times.      |             |             |             |
+-------------+-------------+-------------+-------------+-------------+
| Plain Text  | To control  | \$1         | This is {{  | This is     |
| with a      | the output  |             | if          | Hello World |
| single      | of text in  |             | equal(\$1,  |             |
| condition   | your format |             | \"Hello\")  |             |
|             | string you  |             | then \"\$1  |             |
|             | can use     |             | World\" }}  |             |
|             | conditional |             |             |             |
|             | expressions |             |             |             |
|             | .           |             |             |             |
|             | Conditional |             |             |             |
|             | expressions |             |             |             |
|             | use a       |             |             |             |
|             | strict      |             |             |             |
|             | syntax      |             |             |             |
|             | describe    |             |             |             |
|             | below.      |             |             |             |
|             |             |             |             |             |
|             | Each        |             |             |             |
|             | condition   |             |             |             |
|             | must begin  |             |             |             |
|             | end with    |             |             |             |
|             | double      |             |             |             |
|             | handle      |             |             |             |
|             | bars.       |             |             |             |
|             |             |             |             |             |
|             | i.e. {{     |             |             |             |
|             | condition   |             |             |             |
|             | }}          |             |             |             |
|             |             |             |             |             |
|             | Each        |             |             |             |
|             | condition   |             |             |             |
|             | must use    |             |             |             |
|             | the if      |             |             |             |
|             | elsif else  |             |             |             |
|             | program     |             |             |             |
|             | flow        |             |             |             |
|             |             |             |             |             |
|             | i.e. {{ if  |             |             |             |
|             | \<expressio |             |             |             |
|             | n\>         |             |             |             |
|             | then        |             |             |             |
|             | \<result\>  |             |             |             |
|             | elsif       |             |             |             |
|             | \<expressio |             |             |             |
|             | n\>         |             |             |             |
|             | then        |             |             |             |
|             | \<result\>  |             |             |             |
|             | \... else   |             |             |             |
|             | \<result\>  |             |             |             |
|             | }}          |             |             |             |
|             |             |             |             |             |
|             | Each        |             |             |             |
|             | expression  |             |             |             |
|             | within a if |             |             |             |
|             | statement   |             |             |             |
|             | is formed   |             |             |             |
|             | from using  |             |             |             |
|             | logical and |             |             |             |
|             | comparison  |             |             |             |
|             | operators   |             |             |             |
|             | which will  |             |             |             |
|             | be          |             |             |             |
|             | described   |             |             |             |
|             | in later    |             |             |             |
|             | examples.   |             |             |             |
|             |             |             |             |             |
|             | Each result |             |             |             |
|             | within a if |             |             |             |
|             | statement   |             |             |             |
|             | is formed   |             |             |             |
|             | either as a |             |             |             |
|             | quoted      |             |             |             |
|             | string or   |             |             |             |
|             | number      |             |             |             |
|             | value or    |             |             |             |
|             | variable    |             |             |             |
|             | reference   |             |             |             |
|             |             |             |             |             |
|             | e.g.        |             |             |             |
|             | \"Hello     |             |             |             |
|             | World\",    |             |             |             |
|             | 1.123, \$1  |             |             |             |
+-------------+-------------+-------------+-------------+-------------+
| Plain text  | A format    | \$1 =\>     | This is {{{ | This is     |
| with        | string can  | \"Something | if \$1 then | Something   |
| multiple    | contain     | \"          | \$1 else    | Else        |
| conditions  | multiple    |             | \"NULL\" }} |             |
|             | conditional | \$2 =\>     | {{ if \$2   |             |
|             | expressions | \"Else\"    | then \$2    |             |
|             | .           |             | else        |             |
|             |             |             | \"NULL\" }} |             |
+-------------+-------------+-------------+-------------+-------------+
:::

### Railroad Diagram {#FAIMSData,UIandLogicCook-Book-RailroadDiagram}

The railroad diagram below shows how to construct a conditional
statement.

[![](attachments/3014726_attachments_faims_format_box_diagram%20(1).jpg){.confluence-embedded-image}]{.confluence-embedded-file-wrapper}

### Format Statement Functions {#FAIMSData,UIandLogicCook-Book-FormatStatementFunctions}

You can use the following functions in your format string described
above.

::: {.table-wrap}
+-----------------------------------+-----------------------------------+
| Function                          | Description                       |
+===================================+===================================+
| equal(x, y)                       | x == y                            |
+-----------------------------------+-----------------------------------+
| greaterThan(x, y)                 | x \> y                            |
+-----------------------------------+-----------------------------------+
| greaterThanEqual(x, y)            | x \>= y                           |
+-----------------------------------+-----------------------------------+
| lessThan(x, y)                    | x \< y                            |
+-----------------------------------+-----------------------------------+
| lessThanEqual(x, y)               | x \<= y                           |
+-----------------------------------+-----------------------------------+
| between(x, y, z)                  | x \< y && y \< z                  |
+-----------------------------------+-----------------------------------+
| in(x, \[a, b, c\])                | x in list \[a, b, c\]             |
+-----------------------------------+-----------------------------------+
| not(x)                            | !x                                |
+-----------------------------------+-----------------------------------+
:::

### Examples {#FAIMSData,UIandLogicCook-Book-Examples}

::: {.table-wrap}
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Example                                           Variables              Format String                                                                                     Result
  ------------------------------------------------- ---------------------- ------------------------------------------------------------------------------------------------- --------------
  Null                                              \$1=Hello, \$2=World   NULL                                                                                              Hello, World

  Empty                                             \$1=Hello, \$2=World   \                                                                                                 \

  Plain text                                        \$1=Hello, \$2=World   Test                                                                                              Test

  Variables                                         \$1=Hello, \$2=World   \$1 \$2                                                                                           Hello World

  Single condition                                  \$1=Hello, \$2=World   \$1 {{ if equal(1,1) then \$2 }}                                                                  Hello World

  Parser Error                                      \$1=Hello, \$2=World   \$1 {{ if 1==1 then \$2 }}                                                                        \

  Null check                                        \$1=Hello, \$2=World   {{ if \$1 then \$2 }}                                                                             World

  Number condition and double quote string result   \$1=Hello, \$2=World   {{ if equal(1.01, 1.01) then \"\$1 \$2\"}}                                                        Hello World

  Number condition and single quote string result   \$1=Hello, \$2=World   {{ if equal(1.01, 1.01) then \'\$1 \$2\'}}                                                        Hello World

  Number condition and number result                \$1=Hello, \$2=World   {{ if equal(1.01, 1.01) then 1.01}}                                                               1.01

  Number condition and variable result              \$1=Hello, \$2=World   {{ if equal(1.01, 1.01) then \$1 }}                                                               Hello

  Int condition                                     \$1=Hello, \$2=World   {{ if equal(1, 1) then \"\$1 \$2\"}}                                                              Hello World

  String condition                                  \$1=Hello, \$2=World   {{ if equal(\"test\", \"test\") then \$1}}                                                        Hello

  Variable condition                                \$1=Hello, \$2=World   {{ if equal(\$1, \$1) then \$1}}                                                                  Hello

  Between condition                                 \$1=Hello, \$2=World   {{ if between(1, 0, 5) then \$1 else \$2}}                                                        Hello

  Not condition                                     \$1=Hello, \$2=World   {{ if not(between(1, 0, 5)) then \$1 else \$2}}                                                   World

  In condition                                      \$1=Hello, \$2=World   {{ if in(\$1, \[\"Hello\", \"World\"\]) then \$1 else \$2}}                                       Hello

  In condition with int                             \$1=Hello, \$2=World   {{ if in(\$1, \[1, \"World\"\]) then \$1 else \$2}}                                               World

  In condition with variable                        \$1=Hello, \$2=World   {{ if in(\$1, \[\$1, \"World\"\]) then \$1 else \$2}}                                             Hello

  And condition                                     \$1=Hello, \$2=World   {{ if and(equal(1,1), in(\$1, \[\$1, \"World\"\])) then \$1 else \$2}}                            Hello

  Or and condition                                  \$1=Hello, \$2=World   {{ if or(equal(1,2),and(equal(1,1), in(\$1, \[\$1, \"World\"\]))) then \$1 else \$2}}             Hello

  Plain text and condition                          \$1=Hello, \$2=World   Blah {{ if or(equal(1,2),and(equal(1,1), in(\$1, \[\$1, \"World\"\]))) then \$1 else \$2}}        Blah Hello

  Plain text and condition with spaces              \$1=Hello, \$2=World   Blah {{ if or(equal(1,2),   and(  equal(1,1), in(\$1, \[\$1, \"World\"\]))) then \$1 else \$2}}   Blah Hello
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
:::

Duplicate TabGroup {#FAIMSData,UIandLogicCook-Book-DuplicateTabGroup}
==================

Use the following to duplicate a TabGroup. When duplicating a TabGroup
all the values in the TabGroup are save to a new entity except for those
attributes that are in the exclusion list.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="a6027cb6-f78b-49b4-93e5-b421d5370672"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
// This geometry will be added to the new entity
geometry = ...
 
// These attributes will be added to the new entity
extraAttributes = new ArrayList();
extraAttributes.add(createEntityAttribute(...));
 
// These attributes will be excluded from the new entity
excludeAttributes = new ArrayList();
excludeAttributes.add("name"); // Note: this list only contains the name of the attribute to exclude
 
saveCallback = new SaveCallback() {
    onSave(newRecord) {
        ...
    }
}
duplicateTabGroup("tabgroup1", geometry, extraAttributes, excludeAttributes, saveCallback);
```
:::
:::

### Disable AutoSave {#FAIMSData,UIandLogicCook-Book-DisableAutoSave}

Use the following to disable autosave. 

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="3927681d-8e64-469e-96d4-b2f74bbb5713"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
disableAutoSave("tabgroup1");
```
:::
:::

Display Custom HTML Descriptions in view Info tab {#FAIMSData,UIandLogicCook-Book-DisplayCustomHTMLDescriptionsinviewInfotab}
=================================================

To display custom info tab then you must first change the data schema
descriptions to use html fragments instead of simple text. Below is a
sample portion of a property with html descriptions.

Note: The default behaviour is to not display custom html descriptions
which will then generate a predefined html template for the info tab.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="71d7fe5f-bad4-45a0-883e-319bdadeb7e0"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<property name="Attribute1" type="vocab">
            <description><![CDATA[
<div>
    <p><b>Description</b></p>
    <p>Attribute description</p>
    <hr/>
</div>]]>
            </description>
            <lookup>
                <term pictureURL="files/data/vocab1.png">
                    Vocab1
                    <description><![CDATA[
<div>
    <div>
        <img style="width:100%;" src="files/data/vocab1.png" alt="vocab1"/>
    </div>
    <div>
        <div>
            <p><b>Vocab1</b></p>
            <p>Vocab1 description</p>
        </div>
    </div>
    <hr/>
</div>]]>
                    </description>
                </term>
...
            </lookup>
</property>
```
:::
:::

After adding in the html descriptions you must then flag the view to use
html descriptions via the ui schema or dynamic ui e.g.

In the ui schema you have to set the faims\_html\_description to be
true.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="69bb95d7-ad62-42eb-879b-6c1ceff56a59"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
<select1 ref="attribute1" type="image" faims_attribute_name="Attribute 1" faims_attribute_type="vocab" faims_html_description="true">
    <label>Attribute 1</label>
        <item>
            <label>placeholder</label>
            <value>placeholder</value>
        </item>
</select1>
```
:::
:::

If using dynamic ui then you must set html descriptions to be true.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="68d0b72f-2fd8-438f-b6d8-d70988ef8c9d"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
viewDef = createViewDef();
viewDef.createTextField()   
viewDef.setLabel(...);
...
viewDef.setHTMLDescription(true);
```
:::
:::

Now the info tab will render you custom html. 

::: {.aui-message .hint .shadowed .information-macro}
::: {.message-content}
Tab showing and closing actions generally should be embedded within an
event handler for that tab, as rendering doesn\'t occur immediately
after the code is read.

e.g.

::: {.code .panel .pdl}
::: {.codeContent .panelContent .pdl}
::: {.syntaxhighlighter .nogutter .java style="width: 570.0px;font-size: 1.0em;"}
\

::: {.table-wrap}
+-----------------------------------------------------------------------+
| ::: {.container style="float: none;width: auto;height: auto;vertical- |
| align: baseline;" title="Hint: double-click to select code"}          |
| ::: {.line .number1 .index0 .alt2 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `onEvent(`{.java .plain                                               |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}`"tabgroup"`{.java            |
| .string                                                               |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,51,102);"}`, `{.java                 |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}`"show"`{.java                |
| .string                                                               |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,51,102);"}`, `{.java                 |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}`"onShow()"`{.java            |
| .string                                                               |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,51,102);"}`);`{.java                 |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}                              |
| :::                                                                   |
|                                                                       |
| ::: {.line .number2 .index1 .alt1 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
|                                                                       |
| :::                                                                   |
|                                                                       |
| ::: {.line .number3 .index2 .alt2 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `onShow() {`{.java .plain                                             |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}                              |
| :::                                                                   |
|                                                                       |
| ::: {.line .number4 .index3 .alt1 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `  `{.java .spaces                                                    |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;"}`// ...`{.java                                  |
| .comments                                                             |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,130,0);"}                            |
| :::                                                                   |
|                                                                       |
| ::: {.line .number5 .index4 .alt2 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `  `{.java .spaces                                                    |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;"}`showTab(`{.java                                |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}`"tabgroup/tab"`{.java        |
| .string                                                               |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,51,102);"}`);`{.java                 |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}                              |
| :::                                                                   |
|                                                                       |
| ::: {.line .number6 .index5 .alt1 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `  `{.java .spaces                                                    |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;"}`// ...`{.java                                  |
| .comments                                                             |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,130,0);"}                            |
| :::                                                                   |
|                                                                       |
| ::: {.line .number7 .index6 .alt2 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `  `{.java .spaces                                                    |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;"}`cancelTab(`{.java                              |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}`"tabgroup/tab"`{.java        |
| .string                                                               |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,51,102);"}`, `{.java                 |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}`true`{.java                  |
| .keyword                                                              |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;font-weight: bold;color: rgb(51,102,153);"}`);`{. |
| java                                                                  |
| .plain                                                                |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}                              |
| :::                                                                   |
|                                                                       |
| ::: {.line .number8 .index7 .alt1 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `  `{.java .spaces                                                    |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;"}`// ...`{.java                                  |
| .comments                                                             |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,130,0);"}                            |
| :::                                                                   |
|                                                                       |
| ::: {.line .number9 .index8 .alt2 style="float: none;width: auto;heig |
| ht: auto;vertical-align: baseline;background-image: none;"}           |
| `}`{.java .plain                                                      |
| style="float: none;width: auto;font-family: Consolas , "Bitstream Ver |
| a Sans Mono" , "Courier New" , Courier , monospace;height: auto;verti |
| cal-align: baseline;color: rgb(0,0,0);"}                              |
| :::                                                                   |
| :::                                                                   |
+-----------------------------------------------------------------------+
:::
:::
:::
:::
:::
:::

\

#### Arch16n {#FAIMSData,UIandLogicCook-Book-Arch16n style="margin-bottom: 10.0px;font-family: " source="" sans="" pro="" source-sans-pro="" helveticaneue="" neue="" helvetica="" arial="" sans-serif=""}

</div>

Attachments
-----------

-   [3014726\_attachments\_faims\_format\_box\_diagram
    (1).jpg](attachments/3014726_attachments_faims_format_box_diagram%20%281%29.jpg)
