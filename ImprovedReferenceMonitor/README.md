
# Fixing your security layer

In this assignment you will analyze the bugs in your security layer from [[Part One](ABStoragePartOne.md)] and fix them.  You may want to use test cases from [Part Two](ABStoragePartTwo.md) to help identify these bugs.  Finally, you will write a report discussing the different classes of bugs that your code had, and why.




## Overview
----
In this assignment you are fixing your reference monitor.  You have been sent a bunch of test programs that try to compromise your reference monitor.  Your job will be to determine where your reference monitor failed, and fix it to ensure an attacker cannot circumvent the security layer.



## Common Bugs
 * The reference monitor needs to track the state of the information on disk, but cannot re-read it for every access (due to efficiency concerns). A common mistake is when the attacker can cause the reference monitor’s state to diverge from the underlying system’s state, especially in error conditions. For example, if the program attempts to write past the end of a file (or before the beginning of a file), the reference monitor may incorrectly update its state. As a result, the reference monitor will improperly block or allow writes since the disk contents differ. This can cause both security and accuracy issues.

 * Time-of-check-to-time-of-use (TOCTTOU) bugs and other types of race conditions are a fairly common oversight for students. Some students write test cases that attempt to trigger a race condition to exploit these problems. This can result in essentially any sort of attack, even infinite loops in the reference monitor in some cases.

 * Some reference monitors inappropriately share state for different files. For example, there may be a global set of state that is used to store the first two bytes. By opening multiple files, an attacker may be able to overwrite this state and cause security and accuracy issues.

 * In rare cases, a student’s reference monitor may inappropriately retain state for a file. For example, an attacker may create a file, write some data, then close and delete the file. If the attacker recreates a file with the same name, the state should be cleared.

 * Many reference monitors had accuracy or security bugs as a result of not properly following the instructions.  

