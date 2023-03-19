# Infrastructure

## Master Server
- Controls Pipelines
- Schedules Builds

## Agents/Minions
- Perform the build


EG: 
![image](https://user-images.githubusercontent.com/87442305/226196981-738b666d-3a63-4164-8f5f-a181ab97eddc.png)


# Agents Types

## **_Pernament_ Agents** 
- Dedicated Servers for running jobs
- Prerequisits: Java installed, build tools

## **Cloud Agents**
- Ephemeral/Dynamic Agents spun on Demand
Eg: Docker, Kubernetes, AWS Fleet Manager

# Build Types

### 1. Freestyle Build 
- Simplest method to create a build
- 'Feels' like Shell scripting

### 2. Pipelines
- Use the Groovy Syntax
- Use stages to break down components build
- Stagess: Clone --> Build --> Test --> Package --> Deploy

![image](https://user-images.githubusercontent.com/87442305/226197797-89a3c939-b113-4ef3-bd40-29c08f2126f3.png)
