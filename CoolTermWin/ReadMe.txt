
                    CoolTerm

       Copyright (c) 2007-2013 Roger Meier,
              All rights reserved

         http://freeware.the-meiers.org



WHAT IS IT?
===========

CoolTerm is an easy-to-use terminal for communication with hardware connected to serial ports.

CoolTerm is a simple serial port terminal application (no terminal emulation) that is geared towards hobbyists and professionals with a need to exchange data with hardware connected to serial ports such as servo controllers, robotic kits, GPS receivers, microcontrollers, etc.
The features of CoolTerm include:
- Capability of multiple concurrent connections if multiple serial ports are available.
- Display of received data in plain text or hexadecimal format.
- Sending data via keypresses as well as a "Send String" dialog that supports data entry in plain text or hexadecimal format.
- Sending data via copy-paste of text into the terminal window.
- Sending of text files.
- Capability of capturing received data to text files.
- Local echo of transmitted data.
- Local echo of received data (loop back to sender).
- Hardware (CTS, DTR) and software flow control (XON).
- Optical line status indicators.
- Capability of manually toggling line states of certain handshaking signals when hardware flow control is disabled.
- Configurable character and line delays.
- Capability of saving and retrieving connection options.
- and more...



INSTALLATION
============
CoolTerm comes without an installer and can be placed anywhere on the harddrive as long as the correct folder structure is maintained. I.e. for the Windows version the "CoolTerm Libs" folder must reside in the same location as the "CoolTerm.exe" executable.



HOW TO USE IT
=============

Please refer to the built-in help.



VERSION HISTORY
===============

1.4.3: 09/02/2013
-----------------
NEW/CHANGED FEATURES:
- Added preference setting to select the date and time format used for timestamps. The user can select between the SQL Date/Time format (YYYY-MM-DD HH:MM:SS) or the format determined by the users local system settings.
- Added options to choose the timestamp type and modified the code to fix an bug where the millisecond count and the Date/Time timestamp could get out of sync. It is now only possible to capture timestamps with millisecond resolution when selecting the relative timestamp format.
BUG FIXES AND STABILITY IMPROVEMENTS:
- Made various stability improvements to the code that updates the GUI while data is being sent and received.

NOTE TO MAC USERS:
Version 1.4.x will be the last release of CoolTerm compiled as Universal Binary. Starting at version 1.5.x, CoolTerm will only be deployed for Intel based Macs.


1.4.2: 02/17/2013
-----------------
NEW/CHANGED FEATURES:
- Added options to set the initial state of RTS and DTR when the serial port opens. These options will only have an effect if the respective hardware flow control is not enabled.
- Changed the behavior of capturing received data to file when timestamps are enabled. Instead of appending a time stamp at every occurrence of CR and/or LF characters by default, it is now possible to specify the termination string at which to split the data. Furthermore, CoolTerm will now wait until the specified termination string is received until the data is captured to file.
- Added option to convert received data to hex before capturing to a capture file.
- Enabled the "Close Window" short cut for the "Send String" window.
- Added Alt+ENTER short cut for toggling between ASCII and Hex mode in "Send String"
- Added Connection/Reset menu item to provide a way to reset the port and unlock it if XOFF is active.
- Changed the behavior of the text file capturing with regards to the state of the port. It is now possible to start capturing before the port is opened. In addition, capturing is no longer stopped automatically when the port is closed. This allows for capturing to remain enabled even when the connection state of the port changes. 
- Added code to allow canceling of a text file transmission in progress if XOFF is active.
- Added option to the connection settings (Misc. Options) to automatically close the serial port when the window is being closed without showing a warning if the port is still open.
- Updated the built-in help with information on all menu items.

BUG FIXES AND STABILITY IMPROVEMENTS:
- fixed bug that would cause a NilObjectException in the Xmit routine in cases where the serial port is still transmitting or is hung while the port goes out of scope. This hopefully fixes the crash bug some users have experienced on occasion.
- Fixed bug that caused the transmit line delay setting to not properly be saved to connection settings files.
- Made improvements to receive buffer code to avoid resource conflicts.
Windows only:
- Changed file association on windows to work even on systems where the current user may not have administrative privileges.

APPLESCRIPT:
- Changed AppleScript commands to use unique terminal window IDs instead of the names when addressing windows.
- Added the following AppleScript commands
	- WindowCount as integer
	- WindowID(Index as integer) as integer
	- WindowName(index as integer) as String
	- IndexOfWindowID(ID as integer) as integer
	- NewWindow as integer
	- Quit
	- ResetPort(ID as integer)
	- FlushPort(ID as integer)
	- BytesLeftToSend(ID as integer) as integer
	- LastErrorCode(ID as integer) as integer
	- GetCTS(ID as integer) as boolean
	- GetDSR(ID as integer) as boolean
	- GetDCD(ID as integer) as boolean
	- GetRI(ID as integer) as boolean
	- CaptureStart(ID as integer, FilePath as string) as boolean
	- CapturePause(ID as integer)
	- CaptureResume(ID as integer)
	- CaptureStop(ID as integer)
	- SendTextFile(ID as integer, FilePath as string) as boolean
	- SendBreak(ID as integer)
	- SetDTR(ID as integer, Value as boolean)
	- GetDTR(ID as integer) as boolean
	- SetRTS(ID as integer, Value as boolean)
	- GetRTS(ID as integer) as boolean
- Added code to suppress error messages when CoolTerm is controlled by an AppleScript.
- Updated AppleScriptReadme.txt to reflect latest changes.


1.4.1: 11/21/2011
-----------------
- Improved handling of exceptions if preferences or connection settings can not be read or written.
- Checking serial port for nil in the transmit thread to avoid NilObjectException exceptions. Not clear if this fixes the issue a few users have seen.
- Improved exception handling when serial port adapters are added or removed from the system while CoolTerm is running.
- Fixed a bug in the circular receive buffer that could cause an OutOfBoundsException when reading data.
- Improved handing of OutOfMemoryExceptions when attempting to set the receive buffer size to a value larger than the amount of memory available on the user's system.


1.4.0: 9/12/2011
----------------
NEW FEATURES:
- New Connection options window with multiple pages.
- The connection options now display port information for the selected port.
- It is now possible to change baudrate, byte format settings, and flow control settings while the port is open.
- Added the option to specify additional baud rates via a "baudrates.ini" file. E.g. any baud rates that are known to be supported by the hardware that are not listed in the popup menu in the connection settings dialog can be added to a "baudrate.ini" file that resides in the same directory as CoolTerm.
- Added the option to specify additional serial ports via a "ports.ini" file. E.g. any devices such as /dev/tty.xxx devices on OSX and Linux that CoolTerm can not enumerate can be added to a "ports.ini" file that resides in the same directory as CoolTerm.
- Added the option to add timestamps to data captured to text files.
- Added a keyboard shortcut to connect/disconnect.
- Added option to replace TAB key presses with a configurable number of spaces (default = 4).
- Added option to enable/disable capturing of local echo of transmitted data in capture files.
- Added an option to keep the capture file open while capturing is in progress (default) or close it after writing and re-opening when new data arrives. This allows other applications to read the capture file while capturing is in progress.
- Added status LEDs for TX and RX to indicate activity related to sending and receiving data.
- Added preferences option to disable all menu shortcuts (on Windows and Linux only) in order to allow sending CTRL characters via the terminal. On Mac, the keyboard shortcuts use the Command key and thus don't interfere with CTRL characters.
- [MAC] AppleScript BETA: Added basic AppleScript handling for the most important terminal operations such as loading a settings file, opening/closing ports, and reading/writing data. The AppleScript functionality, while included in CoolTerm 1.4.0, is currently in public BETA , to allow a broader audience to beta test this feature and provide feedback. Refer to the attached "AppleScript ReadMe.txt" file for more details.
- [LINUX] Making LINUX version (unsupported) available.

IMPROVEMENTS:
- Made significant improvements to the code that processes received data, including changing architecture of the receive buffer to a circular buffer to improve efficiency and stability.
- Made significant improvements to the code that transmits data, including changing the architecture of the data transmission to be more asynchronous in nature to improve the responsiveness of CoolTerm during transmission of large text files, particularly with XON/XOFF flow control enabled
- CoolTerm now opens a progress window whenever the length of the text to be transmitted exceeds a certain threshold, and not only when text files are sent. 
- Flow control settings are now displayed in the terminal window as part of the port configuration string. For XON/XOFF the state is displayed, i.e. XON or XOFF.
- Added error messages to alert the user of errors that occur while attempting to open the serial port.
- Added check to warn the user if multiple files are dropped onto the CoolTerm window.
- "Send String" windows can now be resized.
- It is now possible to send CTRL characters when the terminal is set to Line Mode.
- Improved code for Line Mode to ensure that a pressed key is captured even if the command line didn't have the focus.
- Changed behavior of the status LEDs to better reflect the state of the signals. A green LED turned on now means that a signal is "active", the LED turned off means that it is "inactive".
- Changed the default state of DTR when a port is opened to "active" to conform with common practice, with the exception of Windows platforms when DTR flow control is enabled, in which case the default is "inactive" in order to avoid serial port errors.
- Improved handling of file IO errors when sending textile or capturing received data to textiles.
- Improved handling of file IO errors when reading and writing settings files.
- Improved error reporting. Crash reports will now include information about all open terminals.
- Slight change to the behavior during setting the break signal in that no characters are being read from the receive buffer. Received characters will be read after the break signal has been cleared.

BUG FIXES:
- Fixed a bug that would show an error message when the user chooses cancel in the capture file save dialog.
- Fixed a bug that threw an exception when opening the connection settings on a system without serial ports installed.
- Fixed a bug the displayed an error message when the user cancelled out of the "Send Textfile" dialog.
- [WIN] Fixed a bug where the removal of a serial port adapter could cause an exception when starting a connection.
- [MAC] Implemented a workaround for a known RB bug where the baudrates 3600, 7200, 14400, and 28800 baud would not be set correctly and default to 57600 baud instead.


1.3.1: 1/11/2011
----------------
Improvements:
- Added a preferences option to automatically check for updates at startup.

Fixes:
- Fixed a bug that caused a StackOverFlowException when serial port devices were unexpectedly removed from the system, e.g. when a USB serial adapter was unplugged while the terminal was connected to that device. The error handling for this situation has been improved.
- Fixed a bug that caused an OutOfBoundsException when a serial port device failure occurred during enumeration.
- Fixed a bug that resulted in incorrect formatting of long crash reports.


1.3.0: 10/28/2010
-----------------
New features:
- Added a transmit line delay option which adds a specified delay after certain characters such as new line characters (configurable).
- Added a transmit character delay option (configurable).
- Added a "Connection/Send Break" menu item for sending serial breaks.
- Added the option to play a notification sound after a text file has been sent.
- Added auto-connect feature.
- Added the .hex file extension to the "Text Files" file type set (for the "Send Text File" dialog).
- It is now possible to have default settings loaded at startup and when a new terminal window is opened. If a default.stc settings file exists in the application folder of CoolTerm, it will be applied to new terminal windows.
- Added a menu item to save current settings as default settings.

Improvements:
- Pressing ENTER or RETURN in the connection settings dialog now envokes the "Ok" button, even if a textfield is currently selected.
- Pressing ESC in the connection settings dialog now invokes the "Cancel" button, even if a textfield is currently selected.
- Pressing Shift+ENTER or Shift+RETURN now invokes the "Send" button in "Send String" windows.
- Improved handling of command line arguments.
- The values for "Receive Buffer Size" and the character and line delays are now limited to a range from 0 to a maximum value (2,147,483,647 and 10,000, respectively).
- When a "Send String" window is opened, the text field now receives focus automatically.
- Improved exception handling and error reporting.
- Improved behavior of the command history buffer and menu.
- GUI improvements.

Fixes:
- Fixed a bug that allowed opening multiple "Save As..." for the same Terminal window dialogs on Windows.
- Fixed a bug that could cause a StackOverflow on serial port errors due to calling port.flush
- Fixed bug that could cause a crash when sending empty strings via a "Send  String" window.
- (Win) Fixed issue that would allow the terminal window to be activated via the taskbar when the connection options window is open.
- Several minor bug fixes.


1.2.0: 2/19/2010
----------------
- Added "Line Mode" to the communication settings. In "Line Mode" a line of typed text will not be sent to the serial port until the Enter key is pressed.
- Added "History" which is available in "Line Mode" the up and down arrow keys can be used to select previously typed lines.
- Added a receive buffer size limit option.
- Added handling of the bell character (ASCII code 7), which can be enabled through the communication settings.
- It is now possible to open the communication settings and edit certain options while the serial port is open.
- The viewer mode (plain or hex) is now saved as parameter in connection settings files.
- The size and position of terminal windows is now saved with connection settings.
- Fixed bug that converted occurrences CR+CR+LF strings to single spaces on Windows.


1.1.2: 7/17/2009
----------------
- Separated option to handle backspace characters in ASCII view from option to convert non-printable characters.
- Changed character used to display non-printable characters to a period (ASCII code 46) for better compatibility and consistency across platforms.
- Changed short cuts for "View/Autoscroll" and View Mode menu items to avoid conflict with other menu items such as "Edit/Select All".
- Windows build now associates .stc files with CoolTerm.
- Minor bug fixes.


1.1.1: 6/29/2009
----------------
- Added option to handle backspace characters in ASCII view to Connection Settings.
- Fixed bug in SendString that prevented typing 8 in hex mode.
- Fixed bug that printed the wrong character for cursor down key when ConvertNonPrint was enabled.
- Added a "Check for Updates" Menu item.


1.1.0: 6/18/2009
----------------
- Added an option to the connection settings to automatically terminate string sent from "Send String" windows with a configurable "Termination String", such as e.g. a linefeed etc.
- In ASCII view mode, all incoming "New Line" such as CR, LF, CR+LF, are now properly displayed as line breaks.
- Added an option to the connection settings to convert non-printable characters to generic dot characters in ASCII view.
- Added 'View' menu with menu item to switch between Hex and ASCII viewing.
- Moved 'Clear Data' menu item to 'View' menu.
- Added an 'Autoscroll' feature, accessible via the 'View' menu to enable/disable automatic scrolling of received data.
- Changed menu shortcut key for "Cycle through windows" from "0" to "`".
- Added code to produce an audible alert (system beep) when characters are typed while the serial port is not connected.
- Added a 'Help' button to the toolbar


1.0.0: 5/19/2009
----------------
- Initial Release




LICENSE
=======

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT OF THIRD PARTY RIGHTS. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR HOLDERS INCLUDED IN THIS NOTICE BE LIABLE FOR ANY CLAIM, OR ANY SPECIAL INDIRECT OR CONSEQUENTIAL DAMAGES, OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
