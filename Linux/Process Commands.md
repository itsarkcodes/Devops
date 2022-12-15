## Top Command (Table of Process) 


![image](https://user-images.githubusercontent.com/87442305/207924176-0148ecf8-ed0a-4b1f-b305-ac1b0afdcd46.png)

![image](https://user-images.githubusercontent.com/87442305/207924299-049c6b7c-0409-4d2b-8bb6-268d5b4b9919.png)

- top command is used to show the Linux processes.
- It provides a dynamic real-time view of the running system.

![image](https://user-images.githubusercontent.com/87442305/207924794-616f0dd9-4e08-4c70-bf4f-e18bf97e0889.png)

- Exit Top Command After Specific repetition: Top output keep refreshing until you **press ‘q‘.**
- With above command it will automatically exit after 10 repeatation 

![image](https://user-images.githubusercontent.com/87442305/207925397-1ebe898e-bb6e-4bf7-89f1-7ee680c35802.png)

- Shows user specific process
- here it will show what processes are running by user 'aliraza'

> 1) Highlight Running Process in Top: Press ‘z‘   
> 2) Shows Absolute Path of Processes: Press ‘c‘   
> 3) Kill running process: You can kill a process after finding PID of process by pressing ‘k‘ option 

## View Entire Process 
- ps (Process Status) : gives a snapshot of running process

## Difference between top and ps
- top allows you display of process statistics continuously until stopped vs. ps which gives you a single snapshot.

## pgrep command
- pgrep is a command-line utility that allows you to find the process IDs of a running program based on given criteria
- pgrep allows you to use regular expression

![image](https://user-images.githubusercontent.com/87442305/207932031-0e2c7d0f-31cb-46ea-9966-f242e9572585.png)

## Kill a process
- killall : kill all the running process
- kill process-name : kill specified process


### Reference 
https://geeksforgeeks.org/top-command-in-linux-with-examples/
https://linuxize.com/post/pgrep-command-in-linux/
