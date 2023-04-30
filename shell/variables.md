# Variables
###  variable is a named value that can be assigned and accessed throughout the script

## To define a variable
- To define a variable, you can use the following syntax: ```variable_name=value```

- eg: mission_name = mars-mission

## To use a variable
- You can then access the value of the variable by prefixing the variable name with a dollar sign '$'
- Eg: 
``` 
mission_name = mars

mkdir = $mission_name
```

## Store values into variable of another command
You can also use variables to store the result of other commands

- For example: ```rocket-status lunar-mission``` command outputs the status of launch as either "launching", "success" or "failed". we can store the output of the "rocket-status" command in a variable and print msg on the screen using ```echo``` command
```
rocket_status = $(rocket-status $mission_name)
echo "Status of launch: $rocket_status"
```

![image](https://user-images.githubusercontent.com/87442305/235347601-e4bf90cc-8c77-4e04-bf9b-5cd5382f75cb.png)

