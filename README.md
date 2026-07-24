# NixOS-KDE-PJATK-VPN-Configurations-For-MSSQL
To any PJAIT student losing their minds over a tiny VPN setting mismatch, our school only provides a guide for Debain based Gnome system. 

**Provided as-is for informational purposes. Use at your own risk.**

# Guide

You can copy the file named "PJWSTK VPN" and fill here with your student mail.
user=sXXXXX@pjwstk.edu.pl 

It is very hard to get this right under KDE because of the naming differences and most importantly requiring MPPE or using it very confusing. Not to mention confusing routing and similar panes.

The file doesn't include UUID, OS autogenerates it, if not you can run uuidgen in your terminal and add uuid=YOUR_UUID under [connection] section in your configuration file. Your password is also handled by your DE secrets manager. 
So basically copy the VPN file content, fill your mail, paste it into the file under "/etc/NetworkManager/system-connections/PJWSTK VPN", like `sudo cp "PJWSTK VPN" "/etc/NetworkManager/system-connections/PJWSTK VPN"` or `sudo nvim "/etc/NetworkManager/system-connections/PJWSTK VPN"` for editing. then run the following 
1. `sudo chmod 600 "/etc/NetworkManager/system-connections/PJWSTK VPN"` 
2. `sudo chown root:root "/etc/NetworkManager/system-connections/PJWSTK VPN"`
3. `sudo nmcli connection reload`
4. `sudo nmcli connection up "PJWSTK VPN"`
    - If you havent tried connecting before, go to your KDE or any network settings and give it your password in the VPN settings, it will store it for you, and click connect.
5. If there are no errors test your connection to database with `nc -zv db-mssql.pjwstk.edu.pl 1433`  
6. *Try in DataGrip* by first choosing User&Password authentication method in the dropdown and in the user section write PJWST/sXXXXX and give your pass too. It will give error and turn automatically to Domain credentials. Hit test, it will download drivers, and you should be all set! `._.)/\(._.`

![Screenshot for DataGrip Database Configurations](DataGrip_Setup.png?raw=true)

