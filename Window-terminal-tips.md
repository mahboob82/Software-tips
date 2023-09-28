# How can you start CMD with a multiple panes layout?

## First way:
### Create a shortcut on desktop
Layout in mind: Three panes: 1 on the left and 2 on the right (vertical)
        
Steps: 
1. Right click anywhere on the desktop
2. Go to New > Create a shortcut
3. Copy and paste the following command
   ``` {cmd}
    C:\Users\mahboob\AppData\Local\Microsoft\WindowsApps\wt.exe -d C:\Users\mahboob\Documents ; split-pane -p "Command Prompt" -d C:\Users\mahboob\Documents\R-project; split-pane -p "Command Prompt" -d C:\Users\mahboob\Documents\Github
   ```  
4. OR,
 ``` {cmd}
   C:\Users\mahboob\AppData\Local\Microsoft\WindowsApps\wt.exe ; new-tab -p "Command Prompt"; split-pane -p "Command Prompt" -d C:\Users\mahboob\Documents\R-project; split-pane -p "Command Prompt" -d C:\Users\mahboob\Documents\Github
   ```
5. Go to next
6. Give a name of the shortcut
7. Try the shortcut. Yes, there you are.

### Important

```
  1. This path_str must not be more than 260 character. Windows shortcuts are limited to only 260 chars.
  2. Do not put a semicolon at the end of the path_str. Otherwise, it will add an extra CMD tab at the end which is annoying.
  3. After exe path put an extra space before semicolon such as "\wt.exe ; "
  4. ```Option 3``` path_str do not add an extra cmd tab
  5. ```Option 4``` path_str does add an extra cmd tab
  6. Explanation of the option 5 path_str
     ```{cmd}
     C:\Users\mahboob\AppData\Local\Microsoft\WindowsApps\wt.exe ;        # exe path
     new-tab -p "Command Prompt" -d C:\Users\mahboob\Documents;           # adds a new tab and sets its path to Documents folder
     split-pane -p "Command Prompt" -d C:\Users\mahboob\Documents\R-project ; # Then splits the pane on right horizontally and sets path to R-project folder
     split-pane -p "Command Prompt" -d C:\Users\mahboob\Documents\Github      #  Again splits the pane on right but vertically and sets path to Github folder
   ```


C:\Users\mahboob\AppData\Local\Microsoft\WindowsApps\wt.exe -d C:\Users\mahboob\Documents; split-pane -p "Command Prompt" -d C:\Users\mahboob\Documents\R-project ; split-pane -p "Command Prompt" -d C:\Users\mahboob\Documents\Github ;
