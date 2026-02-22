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
```
The character that most commonly causes the error "found character that cannot start any token" in Ansible YAML files is the tab character (\t). YAML mandates the use of spaces for indentation, not tabs.
Home Assistant
Home Assistant
 +1
This error also occurs with other characters when they appear at the beginning of a line or after a colon without proper quoting, as they have special meaning in YAML:
@: This symbol is reserved for future use in YAML and cannot start a scalar (value) unless it is enclosed in quotes, e.g., foo: "@bar".
%: This character, often found in Jinja2 templates for control flow ({% ... %}), can trigger this error if the file has a .yml extension instead of .yml.j2, or if the rendered output starts with %. Quoting the string can resolve this issue.
&, *, [, {, |, >, -, ?, :: These are all special characters in YAML used for specific syntax (anchors, aliases, lists, mappings, etc.) and generally cannot start a plain scalar without being quoted.
TeX - LaTeX Stack Exchange
TeX - LaTeX Stack Exchange
 +4
How to Fix the Error
Replace Tabs with Spaces: The most frequent solution is to configure your code editor (like VS Code, Sublime Text, etc.) to use spaces instead of tabs for indentation in YAML files. You may need to manually remove existing tabs.
Use Quotes for Special Characters: If a value legitimately needs to start with a special character like @ or %, enclose the entire value in double or single quotes, e.g., from: "{{ ansible_host }}@domain.com".
Check Jinja2 Templates: If you are using Jinja2 templating, ensure the file extension is .yml.j2, and the rendered output forms a valid YAML structure.
Use a YAML Linter/Parser: To help pinpoint the exact location of the error, use an online YAML parser or a linter like yamllint.
```

Troubleshooting
============
Use :set list and :set nolist to look for speacial characters.  Make sure we don't have any tabs.
Make sure any passwords that have special characters ( @ is a special character ) are surrounded by double quotes ""
Reflecting on your vault password it should be a much stronger password.  Make sure to update it in the automation platform vault credential after you update your online vault.
Use the Setup - AAP - CAC job template to test your file. Once the vault file is properly formated you will get past that error.