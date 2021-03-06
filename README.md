﻿### What is WebFormsDocumentViewer?
WebFormsDocumentViewer is a simple custom control that lets you embed documents (PDF, Word, PowerPoint, Excel, RichTextFormat, Text and Mail) in your ASP.NET WebForms pages.

### How do I get started?
First, add a reference in your web.config to the WebFormsDocumentViewer assembly:

```xml
 <system.web>
    <pages>
      <controls>
        <add assembly="WebFormsDocumentViewer" namespace="WebFormsDocumentViewer" tagPrefix="cc" />
      </controls>
    </pages>
  </system.web>
  <system.webServer>
```

Or on your web page:

```csharp
<%@ Register Assembly="WebFormsDocumentViewer" Namespace="WebFormsDocumentViewer" TagPrefix="cc" %>
```

### Where can I get it?
First, [install NuGet](http://docs.nuget.org/docs/start-here/installing-nuget). Then, install [WebForms.DocumentViewer](https://www.nuget.org/packages/WebForms.DocumentViewer/) from the package manager console:

```
PM> Install-Package WebForms.DocumentViewer
```

### How to use it?
You can configure the following parameters of the viewer:
* Width: sets the width of the iframe
* Height: sets the height of the iframe
* FilePath: path to the file to be render on the HTML page
* TempDirectoryPath: path for the temporary converted to PDF files (see Word, PowerPoint, Excel and RichTextFormat sections below).
* PdfRenderer: is used by documents converted to PDFs (see below) and you can choose between [PDF.js](https://mozilla.github.io/pdf.js/) and [Adobe Reader](https://acrobat.adobe.com/uk/en/). Adobe Reader is used by default now, but this requires Adobe to be installed client-side. PDF.js is relying only on JavaScript, but the library is still developing. For further information check their websites.

### How to embed PDF documents?
For PDF documents (.pdf extension), a simple iframe is generated, so the following line is enough to embed a document:

```html
<cc:DocumentViewer runat="server" Width="500" Height="500" FilePath="~/sample.pdf" />
```

You can additionally set the PdfRenderer parameter if you want to use PDF.js.

### How to embed Word documents?
Word documents (.doc and .docx extensions) are converted to PDF documents, then rendered in iframe. You should have Microsoft Office installed on the server for this to work.
You can embed a Word document as shown below:

```html
<cc:DocumentViewer runat="server" Width="500" Height="500" FilePath="sample.docx" TempDirectoryPath="~/TempFiles" PdfRenderer="PdfJs" />
```

If TempDirectoryPath is not supplied, the converted documents can be found in the Temp directory of the project root.
If PdfRenderer is not supplied, Adobe Reader is used by default.


### How to embed PowerPoint documents?
PowerPoint documents (.ppt and pptx extensions) are converted to PDF documents, then rendered in iframe. You should have Microsoft Office installed on the server for this to work.
You can embed a PowerPoint document as shown below:

```html
<cc:DocumentViewer runat="server" Width="500" Height="500" FilePath="sample.pptx" TempDirectoryPath="~/TempFiles" />
```

If TempDirectoryPath is not supplied, the converted documents can be found in the Temp directory of the project root.
You can additionally set the PdfRenderer parameter if you want to use PDF.js.

### How to embed Excel documents?
Excel documents (.xls and .xlsx extensions) are converted to HTML files, then rendered in iframe. You should have Microsoft Office installed on the server for this to work.
You can embed an Excel document as shown below:

```html
<cc:DocumentViewer runat="server" Width="500" Height="500" FilePath="sample.xlsx" TempDirectoryPath="~/TempFiles" />
```

If TempDirectoryPath is not supplied, the converted documents can be found in the Temp directory of the project root.
PdfRenderer parameter is not taken into consideration as Excels are rendered as HTMLs.

### How to embed RichTextFormat documents?
RichTextFormat documents (.rtf extension) are converted to PDF documents, then rendered in iframe. You should have Microsoft Office installed on the server for this to work.
You can embed a RichTextFormat document as shown below:

```html
<cc:DocumentViewer runat="server" Width="500" Height="500" FilePath="sample.rtf" TempDirectoryPath="~/TempFiles" PdfRenderer="PdfJs" />
```

If TempDirectoryPath is not supplied, the converted documents can be found in the Temp directory of the project root.
If PdfRenderer is not supplied, Adobe Reader is used by default.

### How to embed Text documents?
For Text documents (.txt extension), a simple iframe is generated, so the following line is enough to embed a document:

```html
<cc:DocumentViewer runat="server" Width="500" Height="500" FilePath="~/sample.txt" />
```

Other parameters are not required, as browsers support text documents by default.

### How to embed Mail files?
Mail files (.msg and .eml extensions) are converted to HTML, then rendered in iframe. You should have Microsoft Office installed on the server for this to work.
You can embed a Mail file as shown below:

```html
<cc:DocumentViewer runat="server" Width="500" Height="500" FilePath="sample.msg" TempDirectoryPath="~/TempFiles" />
```

If TempDirectoryPath is not supplied, the converted documents can be found in the Temp directory of the project root.
PdfRenderer parameter is not taken into consideration as Mails are rendered as HTMLs.

### Do you have an issue?
Have a bug or a feature request? Please search for existing and closed issues before submitting a new one. If your problem or idea is not addressed yet, please open a new issue.

### License, etc.
WebFormsDocumentViewer is Copyright © 2017 Hajbok Robert under the [MIT](http://opensource.org/licenses/MIT) license.
