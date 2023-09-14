# Bash_Script_3
## Create a menu to provide user with information on different resources and processes within server.

###### Use 'echo' command to create menu name, options, and description of choices
###### Use 'read -p' to record user's input when a choice is entered to forward them to the correct information they asked for; use 'choice' as input variable
###### Use case statement to define the variable 'choice' to execute specific commands when a certain choice is chosen [i.e: 1-13]
###### Encase the previous commands described within a while loop so that the user can stay in the menu until they decide they want to exit

**#!/bin/bash**

###### 'do' is included in Bash while loop to initiate loop 
**while true; do**

  **echo "Sys Info Menu: "
  echo "What information would you like to check?"
  echo "1. Currently logged users"
  echo "2. Your shell directory" 
  echo "3. Home directory"
  echo "4. OS name & version"
  echo "5. Current working directory"
  echo "6. Number of users logged in"
  echo "7. Show all available shells in your system"
  echo "8. Hard disk information"
  echo "9. CPU information" 
  echo "10. Memory information"
  echo "11. File system information"
  echo "12. Currently running processes"
  echo "13. Exit"**


  **read -p "Choose your option [1-13]: " choice**

  **case $choice in
   1)
    echo "Currently logged in users: $users" 
    users=$ whoami
    ;;**

  **2)
    echo "Shell directory path: "
    echo "$SHELL"
    ;;**
   **3)
    echo "Home directory: "
    echo "$HOME"
    cd ~
    ls -la
    ;;**
   **4)
    echo "OS name and version: "**
###### prints out OS, kernel, version, and other detailed info
   **uname -a**
###### shows linux os name and version & distribution software based in Linux 
    lsb_release -a
    ;;
   **5)
    echo "Current working directory: "
    pwd
    ;;**
   **6)
    echo "Number of users logged in w/ usernames: $users"
    users=$ who -q
    ;;**
  **7)
    echo "All available Shells in OS: "**

###### path that shows all available shells in the OS and sorts them in alphabetical order
   cat /etc/shells | sort
    ;;
   **8)
    echo "Hard Disk Information: "**
###### displays size of files in directory
    du -a 
###### displays listed info more easily readable
    du -h
    ;;
  **9)
    echo "CPU Information: "**
###### displays detailed CPU specs
    lscpu
###### displays active CPU usage information including per core usage
    top
    ;;
  **10)
    echo "Memory Information: "**
###### displays memory usage in a human reasable format
    free -h
    ;;
   **11)
    echo "File system information: "**
###### displays a full list of files in OS
    df -a
###### displays sizes of files in directory
    du -a
    ;;
   **12)
    echo "Currently running processes: "**

###### snapshots a view of running processes on system; 'e' selects all processes and 'f' displays full format listing
    ps -ef
   ;;

    13)
      echo "Exit"

    ;;
###### non-numerical choice or not an option, user will be told the following message:
   *)
    echo "Invalid choice. Please choose again. "

 ;;

###### 'esac' closes case statement
  esac
###### the if statement below exits out of the menu if the choice entered is the number 13 or greater (numbers outside of available options) 
  if $choice -ge 13; then
    echo "Exiting..."
    break
###### 'fi' closes if statement
  fi

###### 'done' closes while loop 
done
