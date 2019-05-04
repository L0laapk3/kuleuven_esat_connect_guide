# SSH to vierre64 with X11 forwarding

### Programs required
* [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
* [Xming](https://sourceforge.net/projects/xming/) (for windows, for linux/mac there exist similar programs.)

### Setting up Putty
Set the following settings in putty:
* Host name: `ssh.esat.kuleuven.be` Port: `22`
* Under `Connection > SSH > X11`: Enable X11 forwarding, and use `X display location`: `localhost:0.0`.
* Under `Connection > SSH`: Use remote command `ssh vierre64.esat.kuleuven.be -X`.
* (optional) Under `Connection > Data`: Fill in your `Auto-login username` [r or u number].
* (optional) Generate an SSH key for your machine:
    1. Use the `keygen` button on the bottom, then click `generate`.
    2. Follow the instructions. You do not have to use a passphrase.
    3. Save the public key string. Copy the string from the text box, and save it to an appropriate file like `C:/Users/<you>/.ssh/id_rsa_esat.pub`
    4. Save the public key. Click the button, make sure to give it an appropriate name like `id_rsa_esat`.
    5. Save the private key. Click the button, make sure to give it an appropriate name like `id_rsa_esat.ppk`.
    6. Under `Connection > SSH > Auth`: Select your private key for authentication [`C:/Users/<you>/.ssh/id_rsa_esat.ppk`].
    7. When you log in to the SSH server later, copy the contents of `C:/Users/<you>/.ssh/id_rsa_esat.pub` to the end of the `~/.ssh/authorized_keys` file. You can edit it using the command `nano ~/.ssh/authorized_keys`.
* (Optional) Generate an SSH key to connect to vierre64. I'm too lazy to write this out.
* **MAKE SURE TO SAVE THE CONNECTION PROFILE!** Go back to `Session`, Give it a name and press save.

### Setting up Xming
* Just install Xming normally.
* Open Xming so the status icon shows on the bottom right.

### Connecting to the GUI
To connect to the GUI, you will have to take the following steps:
1. Use Putty to connect to esat using the previously created session settings.
2. You can now start programs using the terminal. Once you start a graphical program, their GUI should automatically forward to your desktop after a couple of seconds.