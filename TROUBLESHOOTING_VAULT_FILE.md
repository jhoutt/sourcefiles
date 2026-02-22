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