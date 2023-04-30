# Creating your first script
**```using Rocket Launch example```**


### To create a shell script
- Create a bash file with .sh extension
- and write all the commands in it that you want to execute

![image](https://user-images.githubusercontent.com/87442305/235345809-5bf460a8-158d-462a-8f56-57968d288eca.png)

### Run Script
- We can run script using ```bash``` command 
- ```bash create-and-launch-rocket.sh```
- when the shell script is executed, it runs each line in that file


### Run commands as an executable 
- eg: you might want to run a command directly -> ```create-and-launch-rocket```
- if you want this then dont name your script with ```.sh``` extension
- Now when we creat the script but we need to tell OS to run as command otherwise it will show command not found error 

![image](https://user-images.githubusercontent.com/87442305/235346037-456b6849-37b0-4f3b-8426-52c816f7bc36.png)

- to add our script as a command, append the **path to the directory containing the script** to the **end of the path variable**

![image](https://user-images.githubusercontent.com/87442305/235346107-6242f96a-c276-48ec-b77e-0b1d0085bf20.png)

- now you can use our own created command just like a normal command
- To see location of a command use ```which``` command -> ```which create-and-launch-rocket```

![image](https://user-images.githubusercontent.com/87442305/235346169-c41b968a-81cf-4aed-8925-eb0794fbceef.png)

### Permissions
For a shell script to work, we need to specify correct permissions to it. We need to set 'x' bit for the file to run as executable

You can check that using ls-l -> ```ls –l /home/michael/create-and-launch-rocket```

![image](https://user-images.githubusercontent.com/87442305/235346356-4702615e-f18a-45bb-a377-1d26e1b6ab43.png)

You can see the 'x' bit is not set for this file

- use ```chmod +x``` command to make it executable Eg: ``` $ chmod +x /home/michael/create-and-launch-rocket ```

![image](https://user-images.githubusercontent.com/87442305/235346864-71d899f9-f9d5-4768-8cde-2629c7e9b087.png)

