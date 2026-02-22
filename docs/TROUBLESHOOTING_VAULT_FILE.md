The error message we are faced with:
```
msg: >
  We were unable to read either as JSON nor YAML, these are the errors we got
  from each:

  JSON: Expecting value: line 1 column 1 (char 0)


  Syntax Error while loading YAML.
    found character that cannot start any token

  The error appears to be in
  '/runner/project/playbooks/files/config_as_code/remotevault.yml': line 70,
  column 19, but may

  be elsewhere in the file depending on the exact syntax problem.
_ansible_no_log: false
```
The interesting part of the message:
```
Syntax Error while loading YAML.
    found character that cannot start any token
```
Google search for the following:
```
found character that cannot start any token ansible yaml file
```
AI Overview

![alt text](https://github.com/jhoutt/sourcefiles/blob/main/docs/images/vaultts.png "Screenshot")

Troubleshooting
============
1. Use :set list and :set nolist to look for speacial characters.  Make sure we don't have any tabs.<br>
2. Make sure any passwords that have special characters ( @ is a special character ) are surrounded by double quotes ""<br>
3. Reflecting on your vault password it should be a much stronger password.  Make sure to update it in the automation       platform vault credential after you update your online vault.<br>
4. Use the Setup - AAP - CAC job template to test your file. Once the vault file is properly formated you will get past that error.