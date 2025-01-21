# Checkmarx Custom Query Rules Repo

This repo is forked from a Russian repo as-is, just translated into English. The two blog posts associated with this repo have also been translated into English.

https://habr.com/ru/companies/dins/articles/477742/ -> https://emeth-.github.io/CxQL-Public-Examples/cheatsheet_1.html


https://habr.com/ru/companies/swordfish_security/articles/521396/ -> https://emeth-.github.io/CxQL-Public-Examples/cheatsheet_2.html

--------------

For a long time, there was no resource where you could post general rules or helper functions and get some new ideas. This repository is intended to share experiences in writing rules in the CxQL language.

All the rules in it are general in nature, extend the capabilities of the system, and can be applied to any projects, without being tied to specifics. Also, you can modify the rules to suit the specifics of your applications by adding and expanding the list of variable names, libraries, and other features used.

## Repository Structure
The structure is divided by languages, as in the tool itself. Almost every line in the rules will be commented on for a better understanding of what is happening and how the CxQL language works.

## Rules
At the moment the repository contains:
* `сommon`
  * `General_privacy_violation_list` - override of the default rule and adding several additional variables for search
  
* `CSharp`
  *  `Find_Hardcoded_Passwords` - Search for passwords in the code that are set as default function parameters.
  *  `Use_Hardcoded_Encryption_Key` - search for encryption keys in the code that are set as a byte array.
  
* `Java`
  * `android`
    * `Activity_Task_Hijacking` - search for components of the application vulnerable to [Task Hijacking](https://xakep.ru/2017/08/14/android-task-hijacking/)
    * `CleartexTraffic_Enabled_True` - check network settings that allow interaction over HTTP
    * `Insecure_Network_Configuration_CleartexTraffic_Permitted_True` - Second rule to check network settings that allow interaction over HTTP
    * `Non_System_Trust_Anchors` - check the correctness of certificate trust settings
    * `ProGuard_Obfuscation_Not_In_Use` - clearing false positives of the base rule if build files for libraries are present in the project
    * `Using_Cert_From_Assets` - use of certificates from application resources
  * `general`
    * `Find_Android_Log_Outputs.txt` - added support for Timber and Loggi libraries for logging
    * `Find_Android_Outputs.txt` - added support for Timber and Loggi libraries for logging
    * `Find_Android_Read.txt` - added support for the `getInputData` method for WorkManager
    
* `JavaScript`
  * `Lodash-CVE` - search for the use of vulnerable methods in the Lodash library
  
* `kotlin`
  * `Sensitive_Data_Exposure` - refinement of the rule for searching for sensitive data
  * `Using_Cert_From_Assets` - use of certificates from application resources
  
* `Objective-C`
  * `Sensitive_Info_In_Plist.txt` - search for sensitive data in .plist format files
  
* `Scala`
  * `Possible_SQL_Injection` - Search for the use of Splicing Literal Values in the slick library