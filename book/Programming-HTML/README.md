## Knowledge base for HTML
* Source: [https://www.w3schools.com/html/](https://www.w3schools.com/html/html_elements.asp)
* Notes:
  - `<b>` is an empty emelmetns without a closing tag which defined a line break or can be closed like this: `<\b>`
  - tages are not case sensitive, `<P>` means the same as `<p>`
  - All HTML elements can have `attributes` which provide additonal information about an element
  - Attributes are always specified in the `start tag`
  - Attributes usually come in name/value paris like: `name = "value"`
    ```html
    <p title="I'm a tooltip">
    This is a paragraph.
    </p>
    <a href="https://www.w3schools.com"> This is a link </a> 
    <img src="w3schools.jpp" alt ="W3Schools.com" width ="104" heigth="142">
    
    ```
    - THE HTML5 standard does not require lowercase attribute names, but lowercase is _`recommended`_
    - The HTML5 standard does not require quotes around attribute values but quotes is _`recommended`_
    - Double quotes around attribute values are the most common, to contain double quotes, it is necessary to use single quotes 
    - [A complete list of all attributes for each HTML element](https://www.w3schools.com/tags/ref_attributes.asp)
     ![HTML attributes](assets\img\2017-03-04-21-34-12.png)
    - Headings are defined with `<h1>` (most important) to `<h6>` (least important) tags
    - `<p>` element defines a _`paragraph`_. <div style="background-color:yellow">_Broweser automatically add some white space (margin) before and after a paragraph_ </div>
    - <div style="background-color:#ce311c">You cannot be sure how HTML will be displayed. Large or small screens, and resized windows will create different results. With HTML, you cannot change the output by adding extra spaces or extra lines in your HTML code. The browser will remove any extra spaces and extra lines when the page is displayed:</div>
    - `<pre>` element defineds preformatted text
    - `<tagname style="property:value;">`, The `property` is a CSS property. The `value` is a CSS value
      ```html
      <body style="background-color:powderblue;">
      <h1 style="color:blue;">
      <p style="color:red;">
      <h1 style="font-family:verdana;">
      <p style="font-size:300%;">
      <h1 style="text-align:center;">Centered Heading</h1>
      // The text-align property defines the horizontal text alignment for an HTML element:
      <p><b>This text is bold</b></p>
      <p><i>This text is italic</i></p>
      <p>This is<sub> subscript</sub> and <sup>superscript</sup></p>
      <b> - Bold text
      <strong> - Important text
      <i> - Italic text
      <em> - Emphasized text or italic 
      <mark> - Marked text or highlight
      <small> - Small text
      <del> - Deleted text
      <ins> - Inserted text or underscore
      <sub> - Subscript text
      <sup> - Superscript text
      <q> - Short quotation
      <blockquote> - Quotations
      <abbr> - Abbreviations, it will display the title when hover over it
      <p>The <abbr title="World Health Organization">WHO</abbr> was founded in 1948.</p>
      <address> - Contract Information
      <cite> - in italic
      <bdo dir="rtl">This line will be written from right to left</bdo>
      <code>
      var x = 5;
      var y = 6;
      document.getElementById("demo").innerHTML = x + y;
      </code>
      <!-- Write your comments here -->      
      ```
    - HTML Layout Elements
      ![](assets\img\2017-03-04-22-50-10.png)

