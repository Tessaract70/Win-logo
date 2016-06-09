These are batch files that display ASCII text art of the Windows logo and version number. I created
them as a banner for remote SSH into my Windows server. It is a bit more involved than doing it on
a Linux or Mac in that Windows command line sessions don't recognize the ANSI escape sequences for
color and MOTD isn't supported. In order for these batch files to work modifications need to be made
on both the client and server. For the server side, a registry entry must be made at HKEY_CURRENT_USER\
Software\Microsoft\Command Processor\. A new string value must be added named "AutoRun" (without
quotes). The value data must be set as C:\path_to_file\logo.bat. You can place the file anywhere as
long as it's reflected in the string. For the client side you must install Ansicon in order for your
terminal session to be able to process the escape sequences sent from the server. Ansicon can be
found on github and the setup instructions are quite simple. Get the .zip file from this URL
https://github.com/adoxa/ansicon/dowloads and unzip it into a directory named Ansicon under Program
Files. Open a command prompt under elevated privilages and navigate to C:\Program Files\Ansicon and
to either the x86 or x64 folder depending on your system. Type ansicon -i and hit enter. This should
add a string value named AutoRun to the HKEY_CURRENT_USER\Software\Microsoft\Command Processor\ as
was added on the server side. This one should have value data that will look like "(if %ANSICON_
VER%==^%ANSICON_VER^% "c:\Program Files\Ansicon\x64\ansicon" -p)" without the quotes. You can verify
this by checking the registry. Lastly the directory from which you executed the ansicon -i command
must be added to the system path in the Environment Variables. Happy SSHing!
