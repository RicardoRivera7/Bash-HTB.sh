# Bash-HTB.sh

A script that runs openvpn to use in Hackthebox to connect to any machine, easy to customize to account for any username and filepath

<h1>Script Output</h1>
<img src="https://i.imgur.com/YBsaXjV.png" height="80%" width="80%" alt="Bash HTB"/>
<br/>
<br/>

<h1>Script Code</h1>

```
#!/bin/bash
# @Author: RicardoRivera
# @Date:   2025-10-21 15:03:22
# @Last Modified by:   RicardoRivera
# @Last Modified time: 2025-10-21 15:17:47
#
#	HackTheBox VPN Launcher
#	=======================
#	A small script that runs Openvpn and connects to the machine for whichever lab, Sherlock, or CTF room you're in



#Internal Variables (don't change)
RED="$(tput setaf 1)"
GREEN="$(tput setaf 2)"
YELLOW="$(tput setaf 3)"
MAGENTA="$(tput setaf 5)"
NC="$(tput sgr0)"


# compiles all functions together 
	function main()
	{
		Aesthetic

		Verify_root

		VPN 

		exit 0

	}
	
	
# Makes the program look a little nicer and lets user know its running
	function Aesthetic()
	{
		echo "$0:${YELLOW}"
		echo " ------------------------------------------------"
		echo "|                                                 |"
		echo "|                                                 |"
		echo "|                                                 |"
		echo "|${GREEN}     HackTheBox VPN is Being Configured... ${NC}${YELLOW}	  |"
		echo "|                                        	  |"
		echo "|                                                 |"
		echo "|${MAGENTA}            Please Wait :)                   ${NC}${YELLOW}    |"
		echo "|                                                 |"
		echo " ------------------------------------------------ ${NC}"
	}
	
	
# Handles any unknown errors and aborts the script in case
	function ErrorHandler()
	{
		echo "$0:${RED} An Unknown Error has occured :( aborting Script... ${NC}"
		exit -1
	}
	
# Makes sure script is run as root as it requires sudo privileges
	function Verify_root()
	{
		if [ "$UID" != "0" ]; then
			echo "$0:${RED} Error you must be root to run this script, try running script as sudo :( ${NC}"
			exit -1
		fi
	}
	
# Activates the HacktheBox openvpn 
	function VPN()
	{
		ErrorHandler=ErrorHandler
	
		Filepath="/home/kali/Downloads/" #Edit the file path to whereever you store your file
		Filename="lab_S0ggySlapper.ovpn" #to adjust for your own account enter your own username at this part lab_{enter_username_here}.openvpn
		Finalpath=$Filepath$Filename
		sudo openvpn $Finalpath || ErrorHandler 
	}

	main $0

```
