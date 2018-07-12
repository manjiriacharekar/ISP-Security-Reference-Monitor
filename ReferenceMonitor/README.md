# Implement a Defensive Security System

This program will help you understand security mechanisms. You will be
guided through the steps of creating a reference monitor using the security
layer functionality in Repy V2. A reference monitor is an access control
concept that refers to an abstract machine that mediates all access to
objects by subjects. This can be used to allow, deny, or change the
behavior of any set of calls. While not a perfect way of validating your
reference monitor, it is useful to create test cases to see whether your
security layer will work as expected. (The test cases may be turned in as
part of the next assignment.)

This program is intended to reinforce concepts about access control and
reference monitors in a hands-on manner. 






## Overview
----
In this program you will create a security layer which keeps a backup
copy of a file in case it is written incorrectly.  This is a common
technique for things like firmware images where a system may not be able to
recover if the file is written incorrectly.  For this program, every
`correct' file must start with the character 'S' and end with the character
'E'.  If any other characters (including lowercase 's', 'e', etc.) are
the first or last characters, then the file is considered invalid. 

However, you must permit the application to write information into the file.  
The application should not be blocked from performing any writeat() operation, 
because when it chooses it may later write 'S' at the start and 'E' at the 
end.  Note that checking if the file starts with 'S' and ends with 'E' is
only performed when close is called.

You may store two copies of A/B files on disk, one that is the valid backup
(which is used for reading) and the other that is written to.  When an
app calls ABopenfile(), this indicates that the A/B files, which you should
name filename.a and filename.b, should be opened.  
