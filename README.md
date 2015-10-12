AXDump
======

AXDump is a tool for debugging accessibility of rich text components on OS X.
Specifically, it dumps the `AXAttributedStringForRange` for a whole `AXTextArea`.
This attributed string can then be inspected to discover bugs/features.

Supported Text Editors
======================
* TextMate 2
* TextEdit
* Pages
* LibreOffice Writer

Usage
=====
Currently the tool is very arcane. There is no binary, it is expected to be
run from Xcode. To change the editor to dump, source code edit needs to be done.

To use AXDump, follow these steps:

1. Open the text you want to debug in the text editor app you want to debug. Note that the app should not be in full screen. Click in the text area so that text cursor appears, and turn VoiceOver on (⌘F5) and off (⌘F5). This ensures for some applications that lazy-loaded accessibility implementations get actually loaded.
2. Add Xcode.app to System Preferences > Security & Privacy > Privacy > Accessibility (requires unlocking the lock in the bottom of the window).
3. Open the AXDump.xcodeproj. Do not put Xcode to full screen.
4. in the `main` function at the end of the main.m file, on the first line containing `AX_CALL_`, change the editor to be debugged by using `find<editor>TextComponent`, substituting `<editor>` with one of `TextMate`, `TextEdit`, `Pages`, `LibreOffice`
5. Run the project (⌘R)
6. See the attributed string in the Console of Xcode's Debug Area

Then you can iterate by repeating only steps 5. and 6.
