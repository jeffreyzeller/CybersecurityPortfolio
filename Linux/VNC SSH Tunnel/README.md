# Steps to establish an SSH tunnel for VNC:
1. Ensure VNC Server is configured (optional, but recommended for security):
2. Configure the VNC server on the remote machine to listen only on localhost (e.g., vncserver -localhost). This prevents direct, unencrypted connections to the VNC server.
3. Create the SSH Tunnel:
4. On your local machine, open a terminal or command prompt and execute the following command:

**Code**

> `ssh -L <local-port>:localhost:<remote-vnc-port> <user>@<remote-host>`


**`<local-port>:`** A local port number on your machine where the VNC client will connect (e.g., 5901, or any unused port).

**`<remote-vnc-port>:`** The port on the remote machine where the VNC server is listening (typically 5900 + display number, e.g., 5901 for display :1).

**`<user>:`** Your username on the remote machine.

**`<remote-host>:`** The IP address or hostname of the remote machine.

The **`-L`** flag specifies local port forwarding.

The **`-N`** flag (optional) prevents remote command execution, keeping the SSH connection solely for tunneling.

The **`-f`** flag (optional, for Linux/macOS) sends the SSH process to the background.

*Connect with VNC Viewer: Open your VNC client and connect to localhost:<local-port> (using the same local port number you specified in the SSH tunnel command).*

## How it works:
The SSH tunnel forwards the traffic from the specified local port on your machine to the VNC server's port on the remote machine, all within the encrypted SSH connection. This means your VNC client connects to your local machine, and the SSH tunnel handles the secure communication to the remote VNC server.

## We can make this into an executible .sh command if needed.

1. Create VNC-TUNNEL.sh

> `nano VNC-SSH-TUNNEL.sh`

2. Copy the following code and change local-port, remote-vnc-port, user and remote-host to the approprate values for the server you are connecting to.

> `ssh -L <local-port>:localhost:<remote-vnc-port> <user>@<remote-host>`

3. Save the file by pressing `ctrl + x`

4. Make the file executable

> `chmod +x your-script.sh`

5. To run the file run `./VNC-SSH-TUNNEL.sh`

6. Connect with VNC Viewer: Open your VNC client and connect to `localhost:<local-port>` (using the same local port number you specified in the SSH tunnel command). 
