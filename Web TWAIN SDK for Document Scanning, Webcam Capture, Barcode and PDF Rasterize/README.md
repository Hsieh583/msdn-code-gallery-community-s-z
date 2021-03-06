# Web TWAIN SDK for Document Scanning, Webcam Capture, Barcode and PDF Rasterize
## Requires
- Visual Studio 2008
## License
- Apache License, Version 2.0
## Technologies
- C#
- SQL Server
- ASP.NET
- Javascript
- Web
- HTML5
- Webcam
- WIA
- PDF
- Image Processing
- scanner
- Twain
- document scanning
- Barcode
## Topics
- ImageViewer
- using webcam
- Image manipulation
- Image
- HTTP
- Databases
- HTML5/JavaScript
- media capture
- Image editing
- document scanning
- PDF rasterizer
## Updated
- 08/26/2016
## Description

<h2>Introduction</h2>
<p><em>The sample illustrates how to use <a href="http://www.dynamsoft.com/Products/WebTWAIN_Overview.aspx" target="_blank">
Dynamic Web TWAIN</a> JavaScript library to scan documents, control webcam, read barcode and rasterize PDF in web browsers. All of these functionalities can work on
<strong>Windows </strong>and <strong>macOS</strong>.</em></p>
<h2><em>Features of Dynamic Web TWAIN</em></h2>
<ul class="right-content">
<li>TWAIN specification 2.1 and below compatible (ActiveX, HTML5 for Windows, Plugin APIs).
</li><li>TWAIN specification 1.9 and below compatible (HTML5 for Mac API). </li><li>Optional disk caching mechanism enables high volume document scanning (up to thousands of pages).
</li><li>Supports Auto Document Feeder (ADF) and multiple image acquisition. </li><li>Supports duplex scanning mode. </li><li>Supports image preview mode. </li><li>Supports blank page detection. </li><li>Built-in wizard mode intelligently manages TWAIN states. </li><li>
<p>Supports setting up image acquisition parameters (resolution, pixel type, bit depth, brightness, contrast, page size, unit, etc).</p>
</li><li>
<p>Supports both Native and Disk File Image transfer modes. ActiveX, Plugin and HTML5 for Windows APIs also support Buffered Memory transfer mode.</p>
</li></ul>
<h2><span>Building the Sample</span></h2>
<p><em>Download and extract the package. Open the project with Visual Studio 2005, 2008, 2010, 2013 and 2015.</em></p>
<p><em><img id="158601" src="158601-online-demo.png" alt="" width="348" height="491"></em></p>
<p><em>Press F5 to launch the project:</em></p>
<p><em><img id="158602" src="158602-online-demo-view.png" alt="" width="930" height="752"><br>
</em></p>
<h2><span style="font-size:20px; font-weight:bold">Document Scanning, Webcam, Barcode &amp; PDF in JavaScript</span></h2>
<h3><em>Scan Document</em></h3>
<p>Here is the complete code for scanning document from TWAIN, WIA scanners.</p>
<div class="scriptcode">
<div class="pluginEditHolder" pluginCommand="mceScriptCode">
<div class="title"><span>JavaScript</span></div>
<div class="pluginLinkHolder"><span class="pluginEditHolderLink">Edit</span>|<span class="pluginRemoveHolderLink">Remove</span></div>
<span class="hidden">js</span>

<div class="preview">
<pre class="js">&lt;input&nbsp;type=<span class="js__string">&quot;button&quot;</span>&nbsp;value=<span class="js__string">&quot;Scan&quot;</span>&nbsp;onclick=<span class="js__string">&quot;AcquireImage();&quot;</span>&nbsp;/&gt;&nbsp;
&nbsp;
&lt;!--&nbsp;dwtcontrolContainer&nbsp;is&nbsp;the&nbsp;<span class="js__statement">default</span>&nbsp;div&nbsp;id&nbsp;<span class="js__statement">for</span>&nbsp;Dynamic&nbsp;Web&nbsp;TWAIN&nbsp;control.&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;If&nbsp;you&nbsp;need&nbsp;to&nbsp;rename&nbsp;the&nbsp;id,&nbsp;you&nbsp;should&nbsp;also&nbsp;change&nbsp;the&nbsp;id&nbsp;<span class="js__operator">in</span>&nbsp;the&nbsp;dynamsoft.webtwain.config.js&nbsp;accordingly.&nbsp;--&gt;&nbsp;
&lt;div&nbsp;id=<span class="js__string">&quot;dwtcontrolContainer&quot;</span>&gt;&lt;/div&gt;&nbsp;
&nbsp;
&lt;script&nbsp;type=<span class="js__string">&quot;text/javascript&quot;</span>&gt;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;Dynamsoft.WebTwainEnv.RegisterEvent(<span class="js__string">'OnWebTwainReady'</span>,&nbsp;Dynamsoft_OnReady);&nbsp;<span class="js__sl_comment">//&nbsp;Register&nbsp;OnWebTwainReady&nbsp;event.&nbsp;This&nbsp;event&nbsp;fires&nbsp;as&nbsp;soon&nbsp;as&nbsp;Dynamic&nbsp;Web&nbsp;TWAIN&nbsp;is&nbsp;initialized&nbsp;and&nbsp;ready&nbsp;to&nbsp;be&nbsp;used</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;DWObject;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__operator">function</span>&nbsp;Dynamsoft_OnReady()&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject&nbsp;=&nbsp;Dynamsoft.WebTwainEnv.GetWebTwain(<span class="js__string">'dwtcontrolContainer'</span>);&nbsp;<span class="js__sl_comment">//&nbsp;Get&nbsp;the&nbsp;Dynamic&nbsp;Web&nbsp;TWAIN&nbsp;object&nbsp;that&nbsp;is&nbsp;embeded&nbsp;in&nbsp;the&nbsp;div&nbsp;with&nbsp;id&nbsp;'dwtcontrolContainer'</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>&nbsp;(DWObject)&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.ImageCaptureDriverType&nbsp;=&nbsp;<span class="js__num">3</span>;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;count&nbsp;=&nbsp;DWObject.SourceCount;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">for</span>&nbsp;(<span class="js__statement">var</span>&nbsp;i&nbsp;=&nbsp;<span class="js__num">0</span>;&nbsp;i&nbsp;&lt;&nbsp;count;&nbsp;i&#43;&#43;)&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;document.getElementById(<span class="js__string">&quot;source&quot;</span>).options.add(<span class="js__operator">new</span>&nbsp;Option(DWObject.GetSourceNameItems(i),&nbsp;i));&nbsp;<span class="js__sl_comment">//&nbsp;Get&nbsp;Data&nbsp;Source&nbsp;names&nbsp;from&nbsp;Data&nbsp;Source&nbsp;Manager&nbsp;and&nbsp;put&nbsp;them&nbsp;in&nbsp;a&nbsp;drop-down&nbsp;box</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__operator">function</span>&nbsp;AcquireImage()&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>&nbsp;(DWObject)&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;OnAcquireImageSuccess,&nbsp;OnAcquireImageFailure;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;OnAcquireImageSuccess&nbsp;=&nbsp;OnAcquireImageFailure&nbsp;=&nbsp;<span class="js__operator">function</span>()&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.CloseSource();&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.SelectSourceByIndex(document.getElementById(<span class="js__string">&quot;source&quot;</span>).selectedIndex);&nbsp;<span class="js__sl_comment">//Use&nbsp;method&nbsp;SelectSourceByIndex&nbsp;to&nbsp;avoid&nbsp;the&nbsp;'Select&nbsp;Source'&nbsp;dialog</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.OpenSource();&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.IfDisableSourceAfterAcquire&nbsp;=&nbsp;true;&nbsp;<span class="js__sl_comment">//&nbsp;Scanner&nbsp;source&nbsp;will&nbsp;be&nbsp;disabled/closed&nbsp;automatically&nbsp;after&nbsp;the&nbsp;scan.</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.AcquireImage(OnAcquireImageSuccess,&nbsp;OnAcquireImageFailure);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&lt;/script&gt;</pre>
</div>
</div>
</div>
<p>To upload an image, use the JavaScript code on the client-side:</p>
<p>&nbsp;</p>
<div class="scriptcode">
<div class="pluginEditHolder" pluginCommand="mceScriptCode">
<div class="title"><span>JavaScript</span></div>
<div class="pluginLinkHolder"><span class="pluginEditHolderLink">Edit</span>|<span class="pluginRemoveHolderLink">Remove</span></div>
<span class="hidden">js</span>

<div class="preview">
<pre class="js"><span class="js__operator">function</span>&nbsp;btnUpload_onclick()&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>&nbsp;(!checkIfImagesInBuffer())&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">return</span>;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;i,&nbsp;strHTTPServer,&nbsp;strActionPage,&nbsp;strImageType;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;_txtFileName&nbsp;=&nbsp;document.getElementById(<span class="js__string">&quot;txt_fileName&quot;</span>);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>(_txtFileName)&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;_txtFileName.className&nbsp;=&nbsp;<span class="js__string">&quot;&quot;</span>;&nbsp;
&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__sl_comment">//DWObject.MaxInternetTransferThreads&nbsp;=&nbsp;5;</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;strHTTPServer&nbsp;=&nbsp;location.hostname;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;DWObject.IfSSL&nbsp;=&nbsp;DynamLib.detect.ssl;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;_strPort&nbsp;=&nbsp;location.port&nbsp;==&nbsp;<span class="js__string">&quot;&quot;</span>&nbsp;?&nbsp;<span class="js__num">80</span>&nbsp;:&nbsp;location.port;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>&nbsp;(DynamLib.detect.ssl&nbsp;==&nbsp;true)&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;_strPort&nbsp;=&nbsp;location.port&nbsp;==&nbsp;<span class="js__string">&quot;&quot;</span>&nbsp;?&nbsp;<span class="js__num">443</span>&nbsp;:&nbsp;location.port;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;DWObject.HTTPPort&nbsp;=&nbsp;_strPort;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;CurrentPathName&nbsp;=&nbsp;unescape(location.pathname);&nbsp;<span class="js__sl_comment">//&nbsp;get&nbsp;current&nbsp;PathName&nbsp;in&nbsp;plain&nbsp;ASCII&nbsp;&nbsp;&nbsp;&nbsp;</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;CurrentPath&nbsp;=&nbsp;CurrentPathName.substring(<span class="js__num">0</span>,&nbsp;CurrentPathName.lastIndexOf(<span class="js__string">&quot;/&quot;</span>)&nbsp;&#43;&nbsp;<span class="js__num">1</span>);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;strActionPage&nbsp;=&nbsp;CurrentPath&nbsp;&#43;&nbsp;<span class="js__string">&quot;SaveToFile.aspx&quot;</span>;&nbsp;<span class="js__sl_comment">//the&nbsp;ActionPage's&nbsp;file&nbsp;path&nbsp;,&nbsp;Online&nbsp;Demo:&quot;SaveToDB.aspx&quot;&nbsp;;Sample:&nbsp;&quot;SaveToFile.aspx&quot;;</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;redirectURLifOK&nbsp;=&nbsp;CurrentPath&nbsp;&#43;&nbsp;<span class="js__string">&quot;online_demo_list.aspx&quot;</span>;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">for</span>&nbsp;(i&nbsp;=&nbsp;<span class="js__num">0</span>;&nbsp;i&nbsp;&lt;&nbsp;<span class="js__num">4</span>;&nbsp;i&#43;&#43;)&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>&nbsp;(document.getElementsByName(<span class="js__string">&quot;ImageType&quot;</span>).item(i).checked&nbsp;==&nbsp;true)&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strImageType&nbsp;=&nbsp;i&nbsp;&#43;&nbsp;<span class="js__num">1</span>;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">break</span>;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;fileName&nbsp;=&nbsp;_txtFileName.value;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;replaceStr&nbsp;=&nbsp;<span class="js__string">&quot;&lt;&quot;</span>;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;fileName&nbsp;=&nbsp;fileName.replace(<span class="js__operator">new</span>&nbsp;<span class="js__object">RegExp</span>(replaceStr,<span class="js__string">'gm'</span>),<span class="js__string">'&amp;lt;'</span>);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;uploadfilename&nbsp;=&nbsp;fileName&nbsp;&#43;&nbsp;<span class="js__string">&quot;.&quot;</span>&nbsp;&#43;&nbsp;document.getElementsByName(<span class="js__string">&quot;ImageType&quot;</span>).item(i).value;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;OnSuccess&nbsp;=&nbsp;<span class="js__operator">function</span>(httpResponse)&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;appendMessage(<span class="js__string">'&lt;b&gt;Upload:&nbsp;&lt;/b&gt;'</span>);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;checkErrorStringWithErrorCode(<span class="js__num">0</span>,&nbsp;<span class="js__string">&quot;Successful.&quot;</span>);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>&nbsp;(strActionPage.indexOf(<span class="js__string">&quot;SaveToFile&quot;</span>)&nbsp;!=&nbsp;-<span class="js__num">1</span>)&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;alert(<span class="js__string">&quot;Successful&quot;</span>)<span class="js__sl_comment">//if&nbsp;save&nbsp;to&nbsp;file.</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;<span class="js__statement">else</span>&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;window.location.href&nbsp;=&nbsp;redirectURLifOK;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;OnFailure&nbsp;=&nbsp;<span class="js__operator">function</span>(errorCode,&nbsp;errorString,&nbsp;httpResponse)&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;checkErrorStringWithErrorCode(errorCode,&nbsp;errorString,&nbsp;httpResponse);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>&nbsp;(strImageType&nbsp;==&nbsp;<span class="js__num">2</span>&nbsp;&amp;&amp;&nbsp;document.getElementById(<span class="js__string">&quot;MultiPageTIFF&quot;</span>).checked)&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>&nbsp;((DWObject.SelectedImagesCount&nbsp;==&nbsp;<span class="js__num">1</span>)&nbsp;||&nbsp;(DWObject.SelectedImagesCount&nbsp;==&nbsp;DWObject.HowManyImagesInBuffer))&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.HTTPUploadAllThroughPostAsMultiPageTIFF(&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strHTTPServer,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strActionPage,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;uploadfilename,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;OnSuccess,&nbsp;OnFailure&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">else</span>&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.HTTPUploadThroughPostAsMultiPageTIFF(&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strHTTPServer,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strActionPage,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;uploadfilename,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;OnSuccess,&nbsp;OnFailure&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">else</span>&nbsp;<span class="js__statement">if</span>&nbsp;(strImageType&nbsp;==&nbsp;<span class="js__num">4</span>&nbsp;&amp;&amp;&nbsp;document.getElementById(<span class="js__string">&quot;MultiPagePDF&quot;</span>).checked)&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>&nbsp;((DWObject.SelectedImagesCount&nbsp;==&nbsp;<span class="js__num">1</span>)&nbsp;||&nbsp;(DWObject.SelectedImagesCount&nbsp;==&nbsp;DWObject.HowManyImagesInBuffer))&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.HTTPUploadAllThroughPostAsPDF(&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strHTTPServer,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strActionPage,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;uploadfilename,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;OnSuccess,&nbsp;OnFailure&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">else</span>&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.HTTPUploadThroughPostAsMultiPagePDF(&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strHTTPServer,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strActionPage,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;uploadfilename,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;OnSuccess,&nbsp;OnFailure&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">else</span>&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.HTTPUploadThroughPostEx(&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strHTTPServer,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.CurrentImageIndexInBuffer,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strActionPage,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;uploadfilename,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strImageType,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;OnSuccess,&nbsp;OnFailure&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
<span class="js__brace">}</span></pre>
</div>
</div>
</div>
<p>&nbsp;</p>
<p>And the C# code on the server-side:</p>
<p>&nbsp;</p>
<div class="scriptcode">
<div class="pluginEditHolder" pluginCommand="mceScriptCode">
<div class="title"><span>C#</span></div>
<div class="pluginLinkHolder"><span class="pluginEditHolderLink">Edit</span>|<span class="pluginRemoveHolderLink">Remove</span></div>
<span class="hidden">csharp</span>

<div class="preview">
<pre class="csharp"><span class="cs__com">//&nbsp;save&nbsp;to&nbsp;file</span>&nbsp;
String&nbsp;strImageName;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;HttpFileCollection&nbsp;files&nbsp;=&nbsp;HttpContext.Current.Request.Files;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;HttpPostedFile&nbsp;uploadfile&nbsp;=&nbsp;files[<span class="cs__string">&quot;RemoteFile&quot;</span>];&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strImageName&nbsp;=&nbsp;uploadfile.FileName;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;uploadfile.SaveAs(Server.MapPath(<span class="cs__string">&quot;.&quot;</span>)&nbsp;&#43;&nbsp;<span class="cs__string">&quot;\\UploadedImages\\&quot;</span>&nbsp;&#43;&nbsp;strImageName);</pre>
</div>
</div>
</div>
<div class="endscriptcode">&nbsp;</div>
<div class="scriptcode">
<div class="pluginEditHolder" pluginCommand="mceScriptCode">
<div class="title"><span>C#</span></div>
<div class="pluginLinkHolder"><span class="pluginEditHolderLink">Edit</span>|<span class="pluginRemoveHolderLink">Remove</span></div>
<span class="hidden">csharp</span>

<div class="preview">
<pre class="csharp"><span class="cs__com">//&nbsp;save&nbsp;to&nbsp;database</span>&nbsp;
<span class="cs__keyword">string</span>&nbsp;strImageName&nbsp;=&nbsp;<span class="cs__string">&quot;&quot;</span>;&nbsp;
<span class="cs__keyword">try</span>&nbsp;
{&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__keyword">int</span>&nbsp;iFileLength;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;HttpFileCollection&nbsp;files&nbsp;=&nbsp;HttpContext.Current.Request.Files;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;HttpPostedFile&nbsp;uploadfile&nbsp;=&nbsp;files[<span class="cs__string">&quot;RemoteFile&quot;</span>];&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__keyword">if</span>&nbsp;(uploadfile&nbsp;!=&nbsp;<span class="cs__keyword">null</span>)&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;{&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strImageName&nbsp;=&nbsp;uploadfile.FileName;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;iFileLength&nbsp;=&nbsp;uploadfile.ContentLength;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Byte[]&nbsp;inputBuffer&nbsp;=&nbsp;<span class="cs__keyword">new</span>&nbsp;Byte[iFileLength];&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;System.IO.Stream&nbsp;inputStream;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;inputStream&nbsp;=&nbsp;uploadfile.InputStream;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;inputStream.Read(inputBuffer,&nbsp;<span class="cs__number">0</span>,&nbsp;iFileLength);&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;String&nbsp;strConnString;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strConnString&nbsp;=&nbsp;Common.DW_ConnString;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;System.Data.SqlClient.SqlConnection&nbsp;sqlConnection&nbsp;=&nbsp;<span class="cs__keyword">new</span>&nbsp;<a class="libraryLink" href="https://msdn.microsoft.com/en-US/library/System.Data.SqlClient.SqlConnection.aspx" target="_blank" title="Auto generated link to System.Data.SqlClient.SqlConnection">System.Data.SqlClient.SqlConnection</a>(strConnString);&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;String&nbsp;SqlCmdText&nbsp;=&nbsp;<span class="cs__string">&quot;INSERT&nbsp;INTO&nbsp;&quot;</span>&nbsp;&#43;&nbsp;Common.DW_SaveTable&nbsp;&#43;&nbsp;<span class="cs__string">&quot;&nbsp;(strImageName,imgImageData)&nbsp;VALUES&nbsp;(@ImageName,@Image)&quot;</span>;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;System.Data.SqlClient.SqlCommand&nbsp;sqlCmdObj&nbsp;=&nbsp;<span class="cs__keyword">new</span>&nbsp;<a class="libraryLink" href="https://msdn.microsoft.com/en-US/library/System.Data.SqlClient.SqlCommand.aspx" target="_blank" title="Auto generated link to System.Data.SqlClient.SqlCommand">System.Data.SqlClient.SqlCommand</a>(SqlCmdText,&nbsp;sqlConnection);&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sqlCmdObj.Parameters.Add(<span class="cs__string">&quot;@Image&quot;</span>,&nbsp;System.Data.SqlDbType.Binary,&nbsp;iFileLength).Value&nbsp;=&nbsp;inputBuffer;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sqlCmdObj.Parameters.Add(<span class="cs__string">&quot;@ImageName&quot;</span>,&nbsp;System.Data.SqlDbType.VarChar,&nbsp;<span class="cs__number">255</span>).Value&nbsp;=&nbsp;strImageName;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sqlConnection.Open();&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sqlCmdObj.ExecuteNonQuery();&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sqlConnection.Close();&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;}&nbsp;
}&nbsp;
<span class="cs__keyword">catch</span>&nbsp;&nbsp;
{&nbsp;
}&nbsp;</pre>
</div>
</div>
</div>
<p>&nbsp;</p>
<h3>Webcam Capture</h3>
<p>&nbsp;</p>
<div class="scriptcode">
<div class="pluginEditHolder" pluginCommand="mceScriptCode">
<div class="title"><span>JavaScript</span></div>
<div class="pluginLinkHolder"><span class="pluginEditHolderLink">Edit</span>|<span class="pluginRemoveHolderLink">Remove</span></div>
<span class="hidden">js</span>

<div class="preview">
<pre class="js"><span class="js__operator">function</span>&nbsp;acquireImageByWebcam()&nbsp;
<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;DWObject.Addon.Webcam.SelectSource(document.getElementById(<span class="js__string">&quot;webcamsource&quot;</span>).options[document.getElementById(<span class="js__string">&quot;webcamsource&quot;</span>).selectedIndex].text);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;valueMediaType&nbsp;=&nbsp;<span class="js__string">&quot;&quot;</span>;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;MediaType&nbsp;=&nbsp;document.getElementById(<span class="js__string">&quot;MediaType&quot;</span>);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>(MediaType&nbsp;&amp;&amp;&nbsp;MediaType.options.length&nbsp;&gt;&nbsp;<span class="js__num">0</span>)&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;valueMediaType&nbsp;=&nbsp;MediaType.options[MediaType.selectedIndex].text;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>(valueMediaType&nbsp;!=&nbsp;<span class="js__string">&quot;&quot;</span>)&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>(!DWObject.Addon.Webcam.SetMediaType(valueMediaType))&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;appendMessage(<span class="js__string">'&lt;b&gt;Error&nbsp;setting&nbsp;MediaType&nbsp;value:&nbsp;&lt;/b&gt;'</span>);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;appendMessage(<span class="js__string">&quot;&lt;span&nbsp;style='color:#cE5E04'&gt;&lt;b&gt;&quot;</span>&nbsp;&#43;&nbsp;DWObject.ErrorString&nbsp;&#43;&nbsp;<span class="js__string">&quot;&lt;/b&gt;&lt;/span&gt;&lt;br&nbsp;/&gt;&quot;</span>);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;valueResolution&nbsp;=&nbsp;<span class="js__string">&quot;&quot;</span>;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;ResolutionWebcam&nbsp;=&nbsp;document.getElementById(<span class="js__string">&quot;ResolutionWebcam&quot;</span>);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>(ResolutionWebcam&nbsp;&amp;&amp;&nbsp;ResolutionWebcam.options.length&nbsp;&gt;&nbsp;<span class="js__num">0</span>)&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;valueResolution&nbsp;=&nbsp;ResolutionWebcam.options[ResolutionWebcam.selectedIndex].text;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>(valueResolution&nbsp;!=&nbsp;<span class="js__string">&quot;&quot;</span>)&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.Addon.Webcam.SetResolution(valueResolution);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;aryResolution&nbsp;=&nbsp;DWObject.Addon.Webcam.GetResolution();&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>(valueResolution&nbsp;!=&nbsp;aryResolution.GetCurrent())&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;appendMessage(<span class="js__string">'&lt;b&gt;Error&nbsp;setting&nbsp;Resolution&nbsp;value:&nbsp;&lt;/b&gt;'</span>);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;appendMessage(<span class="js__string">&quot;&lt;span&nbsp;style='color:#cE5E04'&gt;&lt;b&gt;&quot;</span>&nbsp;&#43;&nbsp;DWObject.ErrorString&nbsp;&#43;&nbsp;<span class="js__string">&quot;&lt;/b&gt;&lt;/span&gt;&lt;br&nbsp;/&gt;&quot;</span>);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;showUI&nbsp;=&nbsp;document.getElementById(<span class="js__string">&quot;ShowUIForWebcam&quot;</span>).checked;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__sl_comment">//&nbsp;optional</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;OnCaptureStart&nbsp;=&nbsp;<span class="js__operator">function</span>&nbsp;()&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__sl_comment">//&nbsp;optional</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;OnCaptureSuccess&nbsp;=&nbsp;<span class="js__operator">function</span>&nbsp;()&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__sl_comment">//&nbsp;optional</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;OnCaptureError&nbsp;=&nbsp;<span class="js__operator">function</span>&nbsp;(error,&nbsp;errorstr)&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;alert(errorstr);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__sl_comment">//&nbsp;optional</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;OnCaptureEnd&nbsp;=&nbsp;<span class="js__operator">function</span>&nbsp;()&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__sl_comment">//Call&nbsp;DWObject.Addon.Webcam.CloseSource()&nbsp;to&nbsp;release&nbsp;webcam.</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.Addon.Webcam.CloseSource();&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;updatePageInfo();&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;DWObject.Addon.Webcam.CaptureImage(showUI,&nbsp;OnCaptureStart,&nbsp;OnCaptureSuccess,&nbsp;OnCaptureError,&nbsp;OnCaptureEnd);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<span class="js__brace">}</span></pre>
</div>
</div>
</div>
<p>&nbsp;</p>
<h3>Barcode Reader</h3>
<p>&nbsp;</p>
<div class="scriptcode">
<div class="pluginEditHolder" pluginCommand="mceScriptCode">
<div class="title"><span>JavaScript</span></div>
<div class="pluginLinkHolder"><span class="pluginEditHolderLink">Edit</span>|<span class="pluginRemoveHolderLink">Remove</span></div>
<span class="hidden">js</span>

<div class="preview">
<pre class="js"><span class="js__operator">function</span>&nbsp;btnScanReadBarcode_onclick()&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>&nbsp;(!checkIfImagesInBuffer())&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">return</span>;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;OnSuccess&nbsp;=&nbsp;<span class="js__operator">function</span>&nbsp;()&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__sl_comment">//Get&nbsp;barcode&nbsp;result.</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.Addon.Barcode.Read(DWObject.CurrentImageIndexInBuffer,&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BarcodeInfo[document.getElementById(<span class="js__string">&quot;ddl_barcodeFormat&quot;</span>).selectedIndex].val,&nbsp;GetBarcodeInfo,&nbsp;GetErrorInfo);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;OnFailure&nbsp;=&nbsp;<span class="js__operator">function</span>(errorCode,&nbsp;errorString)&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;appendMessage(errorString);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;strhttp&nbsp;=&nbsp;<span class="js__string">&quot;http:&quot;</span>;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>(<span class="js__string">&quot;https:&quot;</span>&nbsp;==&nbsp;document.location.protocol)&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strhttp&nbsp;=&nbsp;<span class="js__string">&quot;https:&quot;</span>;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>(Dynamsoft.Lib.env.bMac)&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.Addon.Barcode.Download(strhttp&nbsp;&#43;&nbsp;<span class="js__string">&quot;//www.dynamsoft.com/Demo/DWT/Resources/addon/MacBarcode.zip&quot;</span>,&nbsp;OnSuccess,&nbsp;OnFailure);&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">else</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.Addon.Barcode.Download(strhttp&nbsp;&#43;&nbsp;<span class="js__string">&quot;//www.dynamsoft.com/Demo/DWT/Resources/addon/Barcode.zip&quot;</span>,&nbsp;OnSuccess,&nbsp;OnFailure);&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;&nbsp;&nbsp;
<span class="js__brace">}</span></pre>
</div>
</div>
</div>
<p>&nbsp;</p>
<h3>PDF Rasterizer</h3>
<p>&nbsp;</p>
<div class="scriptcode">
<div class="pluginEditHolder" pluginCommand="mceScriptCode">
<div class="title"><span>JavaScript</span></div>
<div class="pluginLinkHolder"><span class="pluginEditHolderLink">Edit</span>|<span class="pluginRemoveHolderLink">Remove</span></div>
<span class="hidden">js</span>

<div class="preview">
<pre class="js"><span class="js__operator">function</span>&nbsp;btnLoadPDF_onclick()&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;OnPDFSuccess&nbsp;=&nbsp;<span class="js__operator">function</span>&nbsp;()&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;appendMessage(<span class="js__string">&quot;Loaded&nbsp;an&nbsp;image&nbsp;successfully.&lt;br/&gt;&quot;</span>);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;updatePageInfo();&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;OnPDFFailure&nbsp;=&nbsp;<span class="js__operator">function</span>&nbsp;(errorCode,&nbsp;errorString)&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;checkErrorStringWithErrorCode(errorCode,&nbsp;errorString);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>;&nbsp;
&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;OnSuccess&nbsp;=&nbsp;<span class="js__operator">function</span>&nbsp;()&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.IfShowFileDialog&nbsp;=&nbsp;true;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.Addon.PDF.SetResolution(<span class="js__num">300</span>);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.Addon.PDF.SetConvertMode(EnumDWT_ConverMode.CM_RENDERALL);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.LoadImageEx(<span class="js__string">&quot;&quot;</span>,&nbsp;EnumDWT_ImageType.IT_PDF,&nbsp;OnPDFSuccess,&nbsp;OnPDFFailure);&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;OnFailure&nbsp;=&nbsp;<span class="js__operator">function</span>&nbsp;(errorCode,&nbsp;errorString)&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;appendMessage(errorString);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">var</span>&nbsp;strhttp&nbsp;=&nbsp;<span class="js__string">&quot;http:&quot;</span>;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>&nbsp;(<span class="js__string">&quot;https:&quot;</span>&nbsp;==&nbsp;document.location.protocol)&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strhttp&nbsp;=&nbsp;<span class="js__string">&quot;https:&quot;</span>;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">if</span>&nbsp;(Dynamsoft.Lib.env.bMac)&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.IfShowFileDialog&nbsp;=&nbsp;true;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.Addon.PDF.SetResolution(<span class="js__num">300</span>);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.Addon.PDF.SetConvertMode(EnumDWT_ConverMode.CM_RENDERALL);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.LoadImageEx(<span class="js__string">&quot;&quot;</span>,&nbsp;EnumDWT_ImageType.IT_PDF,&nbsp;OnPDFSuccess,&nbsp;OnPDFFailure);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__statement">else</span>&nbsp;<span class="js__brace">{</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DWObject.Addon.PDF.Download(strhttp&nbsp;&#43;&nbsp;<span class="js__string">&quot;//www.dynamsoft.com/Demo/DWT/Resources/addon/Pdf.zip&quot;</span>,&nbsp;OnSuccess,&nbsp;OnFailure);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="js__brace">}</span>&nbsp;
<span class="js__brace">}</span></pre>
</div>
</div>
</div>
<div class="endscriptcode">&nbsp;</div>
<p>&nbsp;</p>
<ul>
</ul>
<h2>More Information</h2>
<ul>
<li><em><a href="http://www.dynamsoft.com/Products/WebTWAIN_Overview.aspx" target="_blank">Dynamic Web TWAIN Homepage</a></em>
</li><li><em><a href="http://developer.dynamsoft.com/dwt" target="_blank">Developer Center</a></em>
</li><li><em><a href="http://www.dynamsoft.com/Downloads/WebTWAIN-Sample-Download.aspx" target="_blank">All Sample Code</a></em>
</li></ul>
<h2>Video</h2>
<p><a href="https://youtu.be/mQEX0l3yz5U" target="_blank">https://youtu.be/mQEX0l3yz5U</a></p>
<h2>Online Demo</h2>
<p><a href="https://www.dynamsoft.com/Demo/DWT/online_demo_scan.aspx" target="_blank">https://www.dynamsoft.com/Demo/DWT/online_demo_scan.aspx</a></p>
