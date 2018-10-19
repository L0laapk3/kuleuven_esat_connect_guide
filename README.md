# How to connect to the ESAT GUI computers from outside the kuleuven network

### Programs required
* [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
* [Proxifier](https://www.proxifier.com/)

### Setting up putty
Set the following settings in putty:
* Host name: `ssh.esat.kuleuven.be` Port: `22` [Any entry point to within kuleuven will do. Does not need to be to esat.]
* Under `Connection > SSH > Tunnels`: Add a `dynamic` port `1337`.
* (optional) Under `Connection > Data`: fill in your `Auto-login username` [r or u number].
* (optional) Generate an SSH key:
    1. Use the `keygen` button on the bottom, then click `generate`.
    2. Follow the instructions. You do not have to use a passphrase.
    3. Save the public key string. Copy the string from the text box, and save it to an appropriate file like `C:/Users/<you>/.ssh/id_rsa_esat.pub`
    4. Save the public key. Click the button, make sure to give it an appropriate name like `id_rsa_esat`.
    5. Save the private key. Click the button, make sure to give it an appropriate name like `id_rsa_esat.ppk`.
    6. Under `Connection > SSH > Auth`: Select your private key for authentication [`C:/Users/<you>/.ssh/id_rsa_esat.ppk`].
    7. When you log in to the SSH server later, copy the contents of `C:/Users/<you>/.ssh/id_rsa_esat.pub` to the end of the `~/.ssh/authorized_keys` file. You can edit it using the command `nano ~/.ssh/authorized_keys`.
* **MAKE SURE TO SAVE THE CONNECTION PROFILE!** Go back to `Session`, Give it a name and press save.

### Setting up proxifier
* (optional) You can find free licenses for proxifier by googling `proxifier license key`.
* Download the [esat.ppx](https://raw.githubusercontent.com/L0laapk3/kuleuven_esat_connect_guide/master/esat.ppx) file and import it under `File > Import profile...`.
* Alternatively, you can set it up yourself:
    * Under `Profile > Proxy Servers...`, add a `SOCKS5` proxy with Address `localhost` and Port `1337`.
    * Under `Profile > Proxification Rules...`, make sure to have at least the following rules:
        * Remote: Applications `remote-viewer.exe`, Action `Proxy SOCKS5 localhost`.
        * Browser: Target Hosts `vdi-portal.esat.kuleuven.be`, Action `Proxy SOCKS5 localhost`.
        * Default: Action: `Direct`.

### Setting up the virtual Desktop viewer
To set up the virtual desktop viewer, refer to [this](https://wiki.esat.kuleuven.be/it/VirtualDesktopAccess) guide. It basically boils down to:
1. Installing [Virt Manager](https://virt-manager.org/download/)
2. (optional) For USB redirection, installing the [UsbDk driver](https://www.spice-space.org/download.html).

### Connecting to the GUI
To connect to the GUI, you will have to take the following steps:
1. PuTTY has to be running with an SSH connection to `ssh.esat.kuleuven.be`.
2. The Proxifier has to be active.
3. Go to the [ESAT VM portal](https://vdi-portal.esat.kuleuven.be/ovirt-engine/userportal/) and start a VM. You may have to refresh first [top right corner].
4. Click `Console` and open the file.
5. Do not forget to power down your VM after you are done using it.