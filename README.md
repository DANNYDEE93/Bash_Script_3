### Bash script to display various information on resources and processes in the OS of a server

#!/bin/bash

while true; do

  echo "Sys Info Menu: "
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
  echo "13. Exit"


  read -p "Choose your option [1-13]: " choice

  case $choice in
   1)
    echo "Currently logged in users: $users" 
    users=$ whoami
    ;;

   2)
    Shell directory path:
    echo "$SHELL"
   echo "Shell directory path: "
    ;;
   3)
    echo "$HOME"
    echo "Home directory: "
    cd ~
    ls -la
    ;;
   4)
   echo "OS name and version: "
    uname -a
    lsb_release -a
    ;;
   5)
    echo "Current working directory: "
    pwd
    ;;
   6)
    echo "Number of users logged in w/ usernames: $users"
    users=$ who -q
    ;;
   7)
    echo "All available Shells in OS: "
    cat /etc/shells | sort
    ;;
   8)
    echo "Hard Disk Information: "
    df -a 
    du -h
    ;;
   9)
    echo "CPU Information: " 
    lscpu
    top
    ;;
   10)
    echo "Memory Information: "
    free -h
    ;;
   11)
    echo "File system information: "
    df -a
    du -a
    ;;
   12)
    echo "Currently running processes: "
    ps -ef
   ;;
  13)
  echo "Exit"
   ;;
   *)
    echo "Invalid choice. Please choose again. "

 ;;

  esac

  if $num -ge 13; then
    echo "Exiting..."
    break

  fi


done
