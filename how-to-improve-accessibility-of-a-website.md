## How to improve accessibility of a website？


###### 1. Supply "alt" tags for images

```html
<img src="graphics/logo.gif" alt="University of Texas" / >
```
###### 2. Supply empty "alt" tags for unessential images

<image src="graphics/spacer.gif" alt="" / >

###### 3. Create Meaningful Links

Bad Example: <a href="http://www.utexas.edu/">click here"</a>
Good Example: <a href="http://www.utexas.edu/">University of Texas at Austin</a>

###### 4.  Allow users to skip over navigational links

<a href="#main_content">Skip navigational links</a>...
...<a name="main_content"></a>

###### 5. Data Tables - Use Headers
```html
<TABLE border="1">
<caption> Amount and type of Jello consumed </caption>
<TR>
   <TH id=”t1” >Name</TH>
<TH id=”t2” >Serving Size (oz)</TH>
<TH id=”t3” abbr="Type">Type of Jello</TH>
<TH id=”t4” >Seconds</TH>
</TR>
<TR>
<TD headers=”t1” >George</TD>
<TD headers=”t2” >10</TD>
<TD headers=”t3” >Red</TD>
<TD headers=”t4” >No</TD>
</TR>
<TR>
<TD headers=”t1” >Bob</TD>
<TD headers=”t2” >5</TD>
<TD headers=”t3” >Green</TD>
<TD headers=”t4” >Yes</TD>
</TR>
</TABLE>
```
###### 6.  Use Frames Sparingly if at all, and give them titles
```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Frameset//EN">
<HTML>
<HEAD>
<TITLE>A frameset document</TITLE>
</HEAD>
<FRAMESET cols="10%, 90%" title=”University Book Store”>
<FRAME src="nav.html" title=”navigational links”>
<FRAME src="doc.html" title=”main content of page”>
<NOFRAMES>
```
###### 7.  Associate Labels with Form Elements
```html
<FORM action="FMPro" method="post">
<fieldset>
<legend>Personal information </legend>
<label for=”firstname”>First name: </label>
<INPUT id=”firstname” type="text" tabindex="1">
<label for=”lastname”>Last name: </label>
<INPUT id=”lastname” type="text" tabindex="2"> ...etc...
</fieldset>
<fieldset>
<legend>Medical History</legend>
<p>
<label for=”grantees”>Grantees:</label>
</p>
<p>
<input id=”grantees” type=”text” tabindex=”3”>
</p> 
</fieldset>
</FORM>
```
###### 8.  Make sure you can navigate through your site using the keyboard only

Take your mouse and put it in your drawer. Now, navigate your website with your keyboard alone!

###### 9.  Supply "alt" tags for Java applets and plugins
```html
<applet name="DigiChat"
“codebase="http://rm150nt.cpd.usu.edu/DigiChat/DigiClasses/"
code="digi/digichat/DigiChatApplet.class"
width="200" height="100" align="right"
archive="Client.jar"
alt=”This is a chat program which requires a Java-compatible Web browser to run”>
<param name="port" value="8303">
<param name="background" value="FFFFFF">
<param name="textcolor" value="000000">
<param name="cabbase" value="Client.cab">
</applet>
```
[1] [Accessibility in HTML5](http://www.clarissapeterson.com/2012/11/html5-accessibility/)
[2] [Web Content Accessibility Guidelines](https://www.w3.org/TR/WCAG20/)
[3] [Web Accessibility Checklist](https://www.utexas.edu/learn/accessibility/testing.html#design)
[4] [Accessible HTML Samples](https://www.utexas.edu/learn/accessibility/samplehtml.html)