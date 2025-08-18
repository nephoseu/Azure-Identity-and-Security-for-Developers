---
lab:
    title: 'Lab 02: Secure Java Spring Boot apps using Microsoft Entra ID'
    module: 'Implement user authentication and authorization'
---

# Lab 02 - Secure Java Spring Boot apps using Microsoft Entra ID

## Lab Overview
In this lab, you will configure a Java Spring Boot web application to authenticate users using Microsoft Entra ID and MSAL4J. You will register the app in Entra ID, configure the application, and run it locally to verify authentication.

## Estimated timing: 120 minutes

## Prerequisites
- Azure subscription
- JDK version 17
- Maven 3
- Java Extension Pack for Visual Studio Code 
- Visual Studio Code
- Azure Tools for Visual Studio Code

## Tasks

+ Task 1: Check prerequisites
+ Task 2: Clone the Application
+ Task 3: Register the Application in Microsoft Entra ID
+ Task 4: Configure the Application
+ Task 5: Build and Run the Application

## Task 1: Check prerequisites
1. Open terminal
1. Check Java version by entering following command in terminal:
```
java -version
```
1. Check Maven version by entering following command in terminal:
```
mvn -v
```

## Task 2: Clone the Application
1. Open a terminal or Git Bash.
2. Run the following command:
```
git clone https://github.com/nephoseu/AISD_Spring_Boot_App.git
```
## Task 3: Register the Application in Microsoft Entra ID
1. Sign in to the Azure Portal (https://portal.azure.com).
1. Navigate to Microsoft Entra ID > App registrations > New registration.
1. Fill in the form:
- Name: 
```
java-spring-webapp-auth
```
- Supported account types: Accounts in this organizational directory only

- In the Redirect URI (optional) section, select Web in the combo-box and enter the following redirect URI:
```
 http://localhost:8080/login/oauth2/code/
 ```
1. Click Register.

1. On the app's registration page, find and copy the Application (client) ID value to use later. You use this value in your app's configuration file or files.

1. On the app's registration page, select Certificates & secrets on the navigation pane to open the page where you can generate secrets and upload certificates.

1. In the Client secrets section, select New client secret.

- Type a description - for example, app secret.

- Select one of the available durations: In 1 year, In 2 years, or Never Expires.

- Select Add. The generated value is displayed.

1. Copy and save the generated value for use in later steps. You need this value for your code's configuration files. This value isn't displayed again, and you can't retrieve it by any other means. So, be sure to save it from the Azure portal before you navigate to any other screen or pane.
## Task 4: Configure the Application
1. Open the project in your IDE (e.g., Visual Studio Code).
1. Navigate to src/main/resources/application.yml.
1. Replace placeholders with your values:
```
tenant-id: <Your_Tenant_ID>
client-id: <Your_Client_ID>
client-secret: <Your_Client_Secret>
```

1. Open pom.xlm file
1. Check java version, and replace it with version you have instaled. 
Replace this:
```
<java.version>VERSION</java.version>
```
to: 
```
<java.version>17</java.version>
```

>**Note**: If you have installed some other version, for example 21, replace it with 21 instead of 17.

## Task 5: Build and Run the Application
1. In the terminal, run:
```
mvn clean verify
mvn spring-boot:run
```
1. Open a browser and go to http://localhost:8080.
1. You should be redirected to the Microsoft Entra ID login page.
1. Sign in with a user from your tenant.
1. Check Token ID. 

