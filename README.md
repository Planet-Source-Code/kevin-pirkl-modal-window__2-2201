<div align="center">

## Modal Window


</div>

### Description

To create a modal window using JavaScript that supports full data entry capabilities. The window open function also has the ability to open the new window centered on the screen.
 
### More Info
 
A global variable in the parent .htm file below is used to store a handle to the child window. The parent windows BODY tag has a onFocus trap that executes a check to see if the child window is open. If the child is open then the parent window will set the focus to that window bringing it to the front. It works great unlike the onBlur samples available out there. 

----

EXTRACT THE CODE BELOW INTO A FILE CALLED test2.htm AND THE SECOND PART OF THE CODE BELOW INTO A FILE CALLED test3.htm THEN RUN TEST2.HTM. 

----




<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Kevin Pirkl](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/kevin-pirkl.md)
**Level**          |Beginner
**User Rating**    |4.3 (13 globes from 3 users)
**Compatibility**  |
**Category**       |[Windows](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/windows__2-80.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/kevin-pirkl-modal-window__2-2201/archive/master.zip)





### Source Code

```
<%
'------------------
'
'------------------
%>
<html>
<HEAD>
	<TITLE>Modal Window Test</TITLE>
<script LANGUAGE="JavaScript"><!--
sticky_URL = "BuildQuery.asp"
ModalWin = null;
function openWin() {
	if (!ModalWin || ModalWin.closed) {
		ModalWin = window.open(sticky_URL,"ModalWin","resizeable=yes,scrollbars=yes,width=400,height=300");
	}
	else
	{
		ModalWin.focus();
	}
}
function FocusModalWin(){
	setTimeout(CheckModalWin, 50);
}
function CheckModalWin(){
	if (ModalWin && !ModalWin.closed) {
		ModalWin.focus();
	}
}
function go(url,iHeight,iWidth,sNewWindow,sModalWinName) {
	if (url=="Refresh")
	{
	top.location.href="default.htm";
	}
	else
	{
		if (document.all)
		  var xMax = screen.width, yMax = screen.height;
		else
		  if (document.layers)
		    var xMax = window.outerWidth, yMax = window.outerHeight;
		  else
		    var xMax = 640, yMax=480;
		// var xOffset = (xMax - 200)/2, yOffset = (yMax - 200)/2;
		var xOffset = (xMax - iWidth)/2, yOffset = (yMax - iHeight)/2;
		if (sNewWindow=="new")
		{
			// window.open (url, null,"height=" +iHeight + ",width=" + iWidth + ",status=yes,toolbar=no,menubar=no,location=no");
			// ModalWin = window.open(sticky_URL,"ModalWin","resizeable=yes,scrollbars=yes,width=400,height=300");
			if (go.arguments.length==5) {
				if (!ModalWin || ModalWin.closed) {
					ModalWin = window.open (url, sModalWinName,"screenX="+xOffset+",screenY="+yOffset+",top="+yOffset+",left="+xOffset+",height=" +iHeight + ",width=" + iWidth + ",status=yes,toolbar=no,menubar=no,location=no");
				}
				else
				{
					ModalWin.focus();
				}
			}
			else
			{
				window.open (url, null,"screenX="+xOffset+",screenY="+yOffset+",top="+yOffset+",left="+xOffset+",height=" +iHeight + ",width=" + iWidth + ",status=yes,toolbar=no,menubar=no,location=no");
			}
		}
		else
		{
			location.href = url;
			// window.open (url , null,"height=450,width=600,status=yes,toolbar=no,menubar=no,location=no");
		}
	}
}
--></script>
</HEAD>
<BODY onFocus="FocusModalWin()" bgcolor="#FFFFFF" >
<input type=button value="Open Test 3" onclick="javascript:go('test3.htm', 300, 500,'new','winTest3');" title="Open Test 3">
<BR>
Click the button to open the modal window then attempt to click on this window again.
</BODY>
</HTML>
-- -CUT HERE FOR Make next few lines into test3.htm -------------------------
<html>
<HEAD>
	<TITLE>Modal Window now open</TITLE>
</HEAD>
<BODY bgcolor="#FFFFFF">
Success!!!! Try clicking on the parent window before you close this window.
<FORM NAME=cmdTest METHOD=POST ACTION=test.asp>
<INPUT TYPE=TEXT VALUE="TYPE HERE TEST" NAME=VAR1>
<INPUT TYPE=SUBMIT VALUE="SUBMIT" NAME=cmdSubmit>
</FORM>
</BODY>
</HTML>
```

