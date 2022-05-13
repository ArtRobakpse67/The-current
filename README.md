# The-current
;https://dev.to/valeria/how-to-automate-file-upload-testing-with-autoit-and-protractor-d94 Sleep(2000) ;then I click on an element to open browser file open dialog  ;Wait 15sec for file dialog (Class #32770) with title 'Open' $hWnd = WinWait("[CLASS:#32770]","",15) ControlFocus($hWnd, "", "[CLASS:Edit; INSTANCE:1]") ControlSetText($hWnd, "", "[CLASS:Edit; INSTANCE:1]", "testtext") ConsoleWrite("$hWnd = " &amp; $hWnd &amp; @CRLF)  ;My experience has shown that ControlClick() works unstable. From time to time a button is ;not clicked by unknown reason. ;ControlClick($hWnd, "", "[CLASS:Button; INSTANCE:1]") ;I have solved this problem by using mouse actions such as mouse move and mouse click.  ;Get Open button position. ;ControlGetPosition returs x and y coordinates of high left corner of the button. Local $pos[2] $pos = ControlGetPos($hWnd, "", "[CLASS:Button; INSTANCE:1]")  ;Set the way coords will be used in the mouse functions, either absolute coords or coords relative ;to the current active window  ;2 = relative coords to the client area of the active window AutoItSetOption("MouseCoordMode", 2)  ;Define $x and $y variables. To prevent some random failures move the mouse from high left corner ;to another button space by adding 10px to $x and $y. Feel free in playing with coordinate values! $x=$pos[0] + 10 $y=$pos[1] + 10  MouseClick($MOUSE_CLICK_LEFT, $x, $y, 1); ConsoleWrite("$hWnd = " &amp; $hWnd &amp; @CRLF)
