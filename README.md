

# Bootstrap new server
prepare the server (raspberry with debian) for ansible using the bootstrap script

Before you can use the script, you need to copy your public ssh key into the server you want to configre.
You can do this with the following command:
```
ssh-copy-id username@destinationServer
```
> Note: If you dont have a ssh-key, you can generate on with the command below (press enter on all prompts that are asked when executing this command)
```
ssh-keygen
```

bootstrap/bootstrap hostnameOrIpAddress Username
```
> This creates an Ansible user with passworless sudo rights

# Change ip address to your server
In the **hosts** file, I set the name of the Raspberry Pi and set it's IP Address. Change this to your setup 

# Variables for the docker containers Octoprint
In the file **octoDocker.yml** located in the folder "roles/octoprint/tasks/", you can find 3 different variables I used for creating specific settings for each printer. The **name** of the printer, the **port** of the printer on the raspberry pi and the **ttyUSB** port. Last one is needed for serial connection to your printer via usb. You have to set your own serial devices. 

1. Connect your printer to your Raspberry and turn the printer on.
2. Login (ssh) to your raspberry pi to find the serial devices. You can do this with the following command:
```
ls -la /dev | grep tty
```
This should print all your devices and filters on the **tty** argument. Search for something with USB in it like: **ttyUSB0** or **ttyACM0**
If you cant find anything similar, your serial connection is probably not working

## Change variables in octoDocker.yml
Change the variables in the file octoDocker.yml (located in roles/octoprint/tasks/), to your specific setup

Run Ansible with:
```
ansible-playbook site.yml
```
# octomilti
# octomilti
