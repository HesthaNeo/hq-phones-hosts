<p align="center">
<img width="552" height="173" alt="Screenshot 2026-04-11 233006" src="https://github.com/user-attachments/assets/5eaa3e81-60d2-461d-99c7-923621ec379e" />
</p>
<h1><u>Milestone 7: HQ Server, Phones and Hosts</u></h1>
    <p>Sixth phase, we will install Cisco CP-7960 VoIP phones and configure DHCP services for the data network hosts on the data network DHCP server (HQ-Server). In this network we do not have an internal DNS server so we will use external DNS via Google (8.8.8.8). The remaining two phones will be installed along with 3 hosts that will pull their IP addresses dynamically from the HQ-Server. So, the first task will be to get the HQ-Server up and running. The HQ Server will be responsible for serving DHCP addresses to the Data network and Guest network, but for now only the Data network DHCP scope will be configured. In addition to DHCP services the server will provide network timing protocol (NTP) service for any network devices configured to pull time from it. Once the Phones are installed we will also implement Quality Service for voice traffic on the HQ-WAN-Router in preparation for our branches to be added to the topology.</p>
    <h2><strong><u>Configuration Steps</u></strong></h2>
    <p><b>Step 1: Connect One Cisco 7960 VOIP Phone To Each HQ Access Switch</b></p>
    <p><b>Step 2: Access The HQ Voice Router CLI And View The DHCP Bindings For Each Phone, Obtaining The MAC-Address Of Each Phone</b></p>
    <p><b>Step 3: On The HQ Voice Router Configure The Three Ephones That Were Just Connected</b></p>
        <p>- A. Ephone 1, Ephone 2, Ephone 3</p>
        <p>- B. Mac-Address</p>
        <p>- C. Phone Type</p>
        <p>- D. Button 1</p>
    <p><b>Step 4: Test Dialing By Extension Between Each HQ Phone</b></p>
    <p><b>Step 5: Test Outbound Dialing To The PSTN Test Phone 8885551111</b></p>
    <p><b>Step 6: Test Inbound Dialing To HQ External Phone Number(s) <em>(Lab Configuration Not Supported)</em></b></p>
    <p><b>Step 7: On The HQ Server Access The DHCP Services And Configure DHCP For The Data Network</b></p>
        <p>- A. Default Gateway</p> 
        <p>- B. DNS Server</p>
        <p>- C. Starting IP Address</p>
        <p>- D. Subnet Mask</p>
        <p>- E. Number Of DHCP Users</p>
    <p><b>Step 8: Connect A Host Directly To Each Of The Three Cisco 7960 VoIP Phones That Were Just Connected To The Network</b></p>
    <p><b>Step 9: Test Each Host By Pinging Around The HQ Network From Each Host And Between Each Host</b></p>
    <p><b>Step 10: Test IP Connectivity To The Internet By Pinging Google Server 8.8.8.8</b></p>
    <p><b>Step 11: Test DNS And Website Connectivity By Using The Web Browser On Each Host To Access Www.Google.Com</b></p>
    <h2><strong><u>Implementation</u></strong></h2>
        <h3>Step 1: Connect One Cisco 7960 VOIP Phone To Each HQ Access Switch</h3>
            <p>- First, we'll connect and configure two more phones. We'll add two 7960 IP phones to the network in the HQ network topology. We'll place one phone under HQ-ASW2 and label it "x1002" and the other phone directly under HQ-ASW3 and label it "x1003".</p>
                <img width="1440" height="884" alt="Screenshot 2026-04-14 164727" src="https://github.com/user-attachments/assets/376fa77e-2f3a-4c50-8a89-53071c3402db" />
        <h3>Step 2: Access The HQ Voice Router CLI And View The DHCP Bindings For Each Phone, Obtaining The MAC-Address Of Each Phone</h3>
                <img width="868" height="256" alt="Screenshot 2026-04-14 165814" src="https://github.com/user-attachments/assets/b3126a7d-c1d7-479e-ae16-44efa5841035" />
        <h3>Step 3: On The HQ Voice Router Configure The Three Ephones That Were Just Connected</h3>
            <p>- Next, we'll access the HQ-VOICE-RTR CLI and configure the two new ephones.</p>
                <img width="872" height="881" alt="Screenshot 2026-04-14 165250" src="https://github.com/user-attachments/assets/46cac24e-109f-44b7-bb7f-febc5e03ec58" />
            <p><em>- After reloading the router, you can see that the uck9 licensing software was installed successfully.</em></p>
        <h3>Step 4: Test Dialing By Extension Between Each HQ Phone</h3>
            <p>- Next we will configure and connect the LAN facing interface G0/0.</p>
                <img width="874" height="652" alt="Screenshot 2026-02-08 200739" src="https://github.com/user-attachments/assets/4023ef4a-9f89-4969-8668-c6d1bdf2c60f" />
            <p><em>- Both MGMT and VOICE VLAN interfaces were configured here as well.</em></p>
            <p>- Next, using a straight-through cable connect the LAN interface G0/0 to a trunk port on HQ-CORE-SW2 (i.e. FastEthernet0/21) and verify the port comes online.</p>
                <img width="1181" height="993" alt="Screenshot 2026-02-08 201116" src="https://github.com/user-attachments/assets/5e6e210a-74fb-42b4-bd23-1749358977ce" />
                <img width="875" height="382" alt="Screenshot 2026-02-08 201255" src="https://github.com/user-attachments/assets/a885e92c-abe7-4370-8495-78d226437363" />
        <h3>Step 5: Test Outbound Dialing To The PSTN Test Phone 8885551111</h3>
            <p>- Next, we will configure a default route that points to the core switch. This will be the only route required on this voice router.</p>
                <img width="875" height="401" alt="Screenshot 2026-02-08 201713" src="https://github.com/user-attachments/assets/83da3e0e-9bd4-455b-82e6-4daba2c6e72d" />
        <h3>Step 6: Test Inbound Dialing To HQ External Phone Number(s) <em>(Lab Configuration Not Supported)</h3>
            <p>- Next, we will configure DHCP for the voice network.</p>
                <p>- A: We'll start with configuring the DHCP pool including option 150 for phone TFTP Server.</p>
                <img width="867" height="286" alt="Screenshot 2026-04-11 210550" src="https://github.com/user-attachments/assets/8a869be4-94a3-4fdc-ba7d-a08a044f2b98" />
            <p><em>- The command option 150 ip 10.10.10.10 will configure a the Cisco DHCP server to provide Cisco IP phones with the IP address of the TFTP server 10.10.10.10. This will allow the phones to download necessary configuration files and firmware. Also worth noting, no DNS Server is required to be handed out to the phones in this network.</em></p>
                <p>- B: Finally, we will configure the DHCP exclusion ranges.</p>
                <img width="873" height="241" alt="Screenshot 2026-04-11 211657" src="https://github.com/user-attachments/assets/0fc18167-dcce-4623-b17d-1976dd88c167" />
        <h3>Step 7: On The HQ Server Access The DHCP Services And Configure DHCP For The Data Network</h3>
            <p>- Next, we will configure Call Manager Express, Skinny Call Control Protocol (SCCP) & directory numbers for HQ.</p>
                <p>- A: We'll start by configuring  telephony-service.</p>
                <img width="870" height="337" alt="Screenshot 2026-04-11 212840" src="https://github.com/user-attachments/assets/28bf12b5-7a42-4e5b-afa1-684474c0849a" />
            <p><em>- We use the command "max-ephones 42" to configure the maximum number of supported phones. "max-dn 144" Configures the maximum number of directory numbers. "ip source-address 10.10.10.10 port 2000" configures the SSCP gateway. "create cnf-files" generates the XML files used by the phones for booting. </em></p>
        <h3>Step 8: Connect A Host Directly To Each Of The Three Cisco 7960 VoIP Phones That Were Just Connected To The Network</h3>
                <p>- A: Next, we'll configure the HQ directory numbers x1001, x1002, x1003.</p>
                <img width="869" height="477" alt="Screenshot 2026-04-11 213814" src="https://github.com/user-attachments/assets/9152f6d6-1bc4-429e-95e8-f437acdc468a" />
                <p>- B: Next, we'll connect a single phone and test ephone registration. We'll add a 7960 IP phone to the network and place the phone near the HQ-CORE-SW1 switch and change the label to “x1001”. Using a straight-through cable, we'll connect the IP Phone to HQ-CORE-SW1 by connecting the port on the phone labeled as “switch” to any available access port on HQ-CORE-SW1.</p>
                <img width="981" height="1140" alt="Screenshot 2026-04-11 221044" src="https://github.com/user-attachments/assets/96ef8c4a-dcc3-494e-8184-c405d3fdf530" />
                <p>- C: Next, we'll return to the HQ-VOICE-RTR CLI and check that the phone has pulled a DHCP address from the DHCP pool that was recently configured.</p>
                <img width="872" height="256" alt="Screenshot 2026-04-11 221435" src="https://github.com/user-attachments/assets/383dfcc6-4755-4f94-827b-161df9bb5629" />
                <p>- D: From the HQ-VOICE-RTR CLI we'll view the ephone and check the running configuration.</p>
                <img width="868" height="353" alt="Screenshot 2026-04-11 221649" src="https://github.com/user-attachments/assets/4a7c5fac-5eab-40fa-a001-efcf12e373fb" />
                <p><em>- We notice the phone is showing up as UNREGISTERED.</em></p>
                <img width="873" height="561" alt="Screenshot 2026-04-11 221912" src="https://github.com/user-attachments/assets/b0cd518a-2252-46cd-922a-322534a19773" />
                <p><em>- We check the running config. We notice a new ephone configuration (ephone 1) was automatically added to the running-config. The MAC address of this ephone also matches the MAC address that was noted in the DHCP binding table.</em></p>
                <p>- E: Next, we'll add a phone type and button assignment to the new ephone.</p>
                <img width="868" height="417" alt="Screenshot 2026-04-11 222354" src="https://github.com/user-attachments/assets/e9a650f9-d9f2-44e7-91e2-bb33b5c412bb" />
                <p><em>- "type 7960" configures this ephone as a 7960 model. "button 1:1" assigns ephone-dn 1 to the first button on the phone. We also notice the phone has now registered properly with extension "1001".</em></p>
        <h3>Step 9: Test Each Host By Pinging Around The HQ Network From Each Host And Between Each Host</h3>
            <p>- For this step, we will configure the connection to the PSTN Provider for external phone service. We'll create an Access Control List that only allows necessary traffic from the PSTN provider. We will use this ACL to restrict traffic on the public connection to the PSTN.</p>
                <img width="871" height="419" alt="Screenshot 2026-04-11 223836" src="https://github.com/user-attachments/assets/c89622ab-1fa6-4ed7-9e55-bb34a51f36d5" />
                <p><em>- *The following access-list will allow Session Initiation Protocol, Real-time Transport Protocol and ICMP from the PSTN Provider. In addition, we have ports open that are not normally used with PSTN connections to allow the phone calls within Packet Tracer. This is because the Packet Tracer lab uses H323 signaling and ephemeral port range TCP 1024-4999. This ephemeral port range is not normally used for calls to/from the PSTN, but we will need them open for our lab to function.</em></p>
        <h3>Step 10: Test IP Connectivity To The Internet By Pinging Google Server 8.8.8.8</h3>
            <p>- Next, we'll configure and connect the Public PSTN connection by configuring the IP address, disabling CDP, and applying the PSTN access-list inbound we just created.</p>
                <img width="872" height="384" alt="Screenshot 2026-04-11 224539" src="https://github.com/user-attachments/assets/cccd3912-2265-468c-af8d-042a690adb80" />
                <p>- A: Using an Ethernet Cross-Over cable, we'll connect the HQ-VOICE-RTR Private WAN interface G0/1 to the PSTN CLOUD router interface G0/0.</p>
                <img width="1491" height="1141" alt="Screenshot 2026-04-11 224745" src="https://github.com/user-attachments/assets/388af1cf-6bfc-4be7-883a-70e1e1fcf322" />
                <img width="871" height="388" alt="Screenshot 2026-04-11 225219" src="https://github.com/user-attachments/assets/75fc0ab5-fd88-4aa1-bb2a-b450375d5948" />
                <p><em>- Connection was successful to the provider router.</em></p>
        <h3>Step 11: Test DNS And Website Connectivity By Using The Web Browser On Each Host To Access Www.Google.Com</h3>
            <p>- For this step, we will configure dial-peer for dialing to future Branch 1 extensions (Internal).</p>
                <img width="870" height="278" alt="Screenshot 2026-04-11 225633" src="https://github.com/user-attachments/assets/7eaf20fd-f9d1-4e8f-8f54-255fbdfce944" />
                
                


                




















            












 





