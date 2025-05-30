# Task-4
In this task, the objective is to understand and configure a firewall using UFW (Uncomplicated Firewall) on Kali Linux. Firewalls play a crucial role in network security by filtering traffic and enforcing rules based on IP addresses, ports, and protocols. UFW is a user-friendly interface for managing iptables, the default Linux packet filtering system.

The task involves:
Step 1: Installing UFW
Before configuring any rules, UFW must be installed (if not already available):

sudo apt update
sudo apt install ufw -y

Once installed, we can check the status by using following command

sudo ufw status verbose

Step 2: Next, I used the command nc -l -n -v to test the firewall rules by checking whether a specific port was open or blocked.This helped verify if the firewall was correctly allowing or denying traffic as configured.

Step 3: Adding a Rule to Block Inbound Traffic on a Specific Port (e.g., Telnet – Port 23)
To enhance system security, I added a rule to block all inbound traffic on port 23, which is commonly used by the insecure Telnet service.

This was done using the following UFW command:

sudo ufw deny 23/tcp

This command explicitly denies incoming connections to port 23 from all interfaces.

To verify that the rule was successfully added, I used:

sudo ufw status verbose

This confirms that the firewall is actively blocking inbound Telnet traffic, thereby preventing unauthorized or insecure remote access attempts on that port.

Step 4: Testing the Newly Added Firewall Rule
To verify whether the rule blocking inbound traffic on port 23 was effective, I used the following command to open a listener on port 23:

sudo nc -lvnp 23

This command attempts to listen for incoming connections on port 23. If the firewall rule is working correctly, any connection attempts to this port should be blocked.

Step 5: Adding a Rule to Allow SSH Traffic (Port 22)
To ensure secure remote access to the Linux system, I added a firewall rule to allow inbound SSH connections on port 22. This is essential for managing the system remotely via SSH.

The command used was:

sudo ufw allow 22/tcp

This rule permits incoming TCP traffic on port 22, enabling SSH access while maintaining firewall protection for other ports.

After adding the rule, I verified it by running:

sudo ufw status verbose

Which confirmed that SSH traffic was allowed.

Step 6: Deleting All Firewall Rules to Restore Original State
After completing the tests, I deleted all the previously added firewall rules to return the firewall to its original default configuration.

This was done using the following command:

sudo ufw status numbered
sudo ufw delete 1

After deletion, I verified the firewall status using:

sudo ufw status verbose

Confirming that the firewall rules were removed and the system was back to its original state.




