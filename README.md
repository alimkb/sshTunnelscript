# sshTunnelscript
SSHTunnel bash script 

,,, bash
#!/bin/bash
# MQCoder.com 
# Simple Bash script to establish SSH tunnel connection from your macOS to your server
# Replace USER@YOU-SERVER with your ssh login details
# change file permission to 755

printf '\e[1;34m%-6s\e[m' "SSH Tunnel"
printf "\nSelect an option:\n"
printf "1. Start SSH Tunnel\n"
printf "2. Stop SSH Tunnel\n"
printf "3. View The State\n\n"
printf "Enter Option Number(1 to 3) : "

while read param; do
    case "$param" in
	 1)   ssh -f -N -M -S /tmp/sshtunnel -D 1080 root@82.163.78.3 -p22 ;
  	      networksetup -setsocksfirewallproxy "Wi-fi" 127.0.0.1 1080 ; break ;;

	 2)   ssh -S /tmp/sshtunnel -O exit root@82.163.78.3 -p22 ;
	      networksetup -setsocksfirewallproxystate "Wi-fi" off ; break ;;

	 3)   networksetup -getsocksfirewallproxy "Wi-Fi" ; break ;;

	 *) printf "Incorrect value option!\nPlease enter the correct value: " ;;
    esac
done









,,,
