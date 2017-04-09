raspbian-ip-mailer
==================

Mail ip to you after system boot in raspbian, orginal version is [http://elinux.org/RPi_Email_IP_On_Boot_Debian](http://elinux.org/RPi_Email_IP_On_Boot_Debian).

This version can: 

1. Try several times to connect smtp server, because the Wifi may be not ready yet.
2. Print progress infomation while connect, login and sending mail.
3. Install as a service automatically.

Deploy
---------------------
1. Download [deploy.sh](https://github.com/shenjia/raspbian-ip-mailer/raw/master/deploy.sh) and run it.

	```
	wget https://github.com/shenjia/raspbian-ip-mailer/raw/master/deploy.sh
	sudo chmod +x deploy.sh
	./deploy.sh

	```
2. Update your mail account in `/usr/local/bin/raspbian-ip-mailer.py`:

	```
	# Mail account settings
    send_to = 'username@gmail.com'
    mail_user = 'username@gmail.com'
    mail_password = 'password'
    ```
    
    If you don't use gmail, update those also:
    
    ```
    # Mail server settings
	smtp_server = 'smtp.gmail.com'
	smtp_port = 587
	```

3. Reboot and enjoy it!
-------------------------------------------
thanks to author: shenjia , but I failed to auto-start the service when reboot, so I use another way:

a) only download and edit the python script

b) sudo vi /etc/rc.local , add '  /usr/bin/python /usr/local/bin/raspbian-ip-mailer.py ' before ' exit 0 '
   (please note: use absolute python path, beacuse when reboot the system variable may not be loaded)
