#To connect Windows and Kali Linux via IP address using the ping command while configuring Windows Defender Firewall, follow these steps:

Step 1: Find the IP Addresses of Both Machines
Before setting up the connection, you need to find the IP addresses of both Windows and Kali Linux.

On Windows
Open Command Prompt (Win + R → type cmd → press Enter).
Run the command: ipconfig
Look for the IPv4 Address under your active network adapter (e.g., 192.147.1.100).

Then on Kali Linux open Terminal.
Run: ifconfig
Find the IP address under the active network interface (e.g., 192.147.1.101).

Step 2: Test Connectivity Using ping command
Now, use the ping command to test the connection between the two systems.

From Windows to Kali
Open Command Prompt.
Run: ping <Kali-IP-Address>
Example: ping 192.147.1.101

Then from Kali to Windows
Open Terminal.
Run: ping <Windows-IP-Address>
Example: ping 192.147.1.100
If the ping fails, it’s likely due to Windows Defender Firewall blocking ICMP requests.

Step 3: Allow ICMP (Ping) in Windows Defender Firewall
By default, Windows blocks incoming ICMP (ping) requests. You will need to allow them by setting your Windows Defender Firewall:

Option 1: Allow Ping via Windows Defender Firewall GUI
Open Windows Defender Firewall:
Press Win + R, type firewall.cpl, and hit Enter.
Click Advanced settings on the left panel.
In the Windows Defender Firewall with Advanced Security, click Inbound Rules.
Locate the rule File and Printer Sharing (Echo Request - ICMPv4-In).
Right-click and choose Enable Rule.

Click Advanced settings (on the left panel).
Select Inbound Rules.
Click New Rule (right panel).
Choose Custom → Click Next.
Select All programs → Click Next.
Under Protocol and Ports, select Any.
Under Which local IP addresses does this rule apply to → select These IP addesses and click Add on the right conner
Under This IP address or subnet: enter your IP with this formart →  192.147.1.0/24 and click ok
Do the same on bottom session as well and click ok. → Click Next
Leave at Allow the connection. → Click Next
Click Next and select Allow the connection.
Apply the rule to Domain, Private, and Public networks.
Name the rule (e.g., "Allow Ping" or "Kali Allow All") and click Finish.

Step 4: Verify Connectivity
Try pinging again after making the changes.
If successful, you can now use networking tools like SSH (ssh from Kali to Windows using OpenSSH Server) or file-sharing (smb).
Let me know if you need further troubleshooting! 
