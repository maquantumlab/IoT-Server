# Raspberry Pi Python APIs 

There are several APIs that have been encorperated into the PI in order to allow for users to efficently use and control different processes on the Pi. 

## Alert API:
There is a seperate page going into full detail the workings of the Alerts API which is used to communicate with Grafana to set the different threshold for alerts. 

##

## Retention Policy:

The `retentionPolicy` executable program is a subprocess that controls how long log files should stay on the Pi for. Note these files are all stored under `~/IoTServer/.DropboxData` and the system by defualt stores 35 days worth of files in order to ensure no data is lost in the dropbox uploading process. In order to change this the user must edit the environmental varible `CUTOFF_DAYS` in the `~/IoTServer/Python-APIs` folder, to do so follow these steps:

First the user must secure shell onto the raspberry pi, this goes as follows: `ssh malab@192.168.1.104` and enter in the password. Once in the user must locate the Python-APIs folder and edit the environmental varibles file:

``` bash
malab@maserver:~ $ cd ~/IoT-Server/Python-APIs/
malab@maserver:~/IoT-Server/Python-APIs $
malab@maserver:~/IoT-Server/Python-APIs $ vim .env 
```

Once in the vim editor locate the `CUTOFF_DAYS` envoironmental varible and edit to the desired number of days to store the data on the Pi for as shown below: 

``` bash
# Vim Editor
...
export SLACK_WEBHOOK_URL="..."
export SYSTEM_CHECKS_PATH="..."

export CUTOFF_DAYS="35"
...
```

To exit the vim editor use the command `:wq`. Once the file has successfully been saved the system will ensure that it doesn't delete any log files locally from `~/IoTServer/.DropboxData` for the `CUTOFF_DAYS` number of days.
