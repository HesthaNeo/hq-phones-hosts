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
            <p>- Next we will place calls between each phone by dialing the extensions from each phone.</p>
                <img width="1748" height="880" alt="Screenshot 2026-04-14 170113" src="https://github.com/user-attachments/assets/33df0337-9cc1-4668-be6a-786c0ab90553" />
                <img width="1739" height="881" alt="Screenshot 2026-04-14 170223" src="https://github.com/user-attachments/assets/f729314f-ac38-45f6-8c33-69096d9c8944" />
            <p><em>- We are successfully able to call between all 3 ephones.</em></p>
        <h3>Step 5: Test Outbound Dialing To The PSTN Test Phone 8885551111</h3>
                <img width="1750" height="879" alt="Screenshot 2026-04-14 170432" src="https://github.com/user-attachments/assets/8eee39c7-1495-4d7f-b29d-6378ab25e786" />
            <p><em>- Successful.</em></p>
        <h3>Step 6: Test Inbound Dialing To HQ External Phone Number(s) <em>(Lab Configuration Not Supported)</h3>
        <h3>Step 7: On The HQ Server Access The DHCP Services And Configure DHCP For The Data Network</h3>
            <p>- Next, we will add a server to the topology and configure NTP and DHCP services.</p>
                <p>- A: We'll start by adding the HQ-Server and testing network connectivity.</p>
                <img width="942" height="762" alt="Screenshot 2026-04-14 170840" src="https://github.com/user-attachments/assets/a3543f89-f961-49a6-93ce-bd69eaad2282" />
                <img width="871" height="883" alt="Screenshot 2026-04-14 170958" src="https://github.com/user-attachments/assets/9f2c376e-0385-4f92-9be6-393e50b17cff" />
                <img width="872" height="881" alt="Screenshot 2026-04-14 171054" src="https://github.com/user-attachments/assets/c3d6c242-0866-416e-b7cd-2deb4e3faa20" />
                <img width="872" height="902" alt="Screenshot 2026-04-14 171244" src="https://github.com/user-attachments/assets/1d39b398-1ecf-4154-89d5-b095898d8851" />
            <p><em>- We are able to successfully ping our default gateway and google dns server.</em></p>
                <p>- B: Now we'll configure network timing protocol.</p>
                <img width="868" height="898" alt="Screenshot 2026-04-14 171634" src="https://github.com/user-attachments/assets/7895884b-6be2-455b-bd42-4049c70906f0" />
                <p>- C: Lastly, we'll configure DHCP service for the data network.</p>
                <img width="1351" height="903" alt="Screenshot 2026-04-14 171917" src="https://github.com/user-attachments/assets/cc034cfb-3427-44de-8e10-a9d274479cb4" /> 
        <h3>Step 8: Connect A Host Directly To Each Of The Three Cisco 7960 VoIP Phones That Were Just Connected To The Network</h3>
                <p>- Next, we'll add 3 DHCP Hosts to the topology and confirm they pull addresses and have network access.</p>
                <img width="518" height="897" alt="Screenshot 2026-04-14 172927" src="https://github.com/user-attachments/assets/60d9eeab-d2f1-4e64-b2e1-0018a30d0c52" />
                <img width="869" height="1472" alt="Screenshot 2026-04-14 172537" src="https://github.com/user-attachments/assets/62400697-7f6e-4499-9813-54cc6fb2faf6" />
                <img width="869" height="1476" alt="Screenshot 2026-04-14 172708" src="https://github.com/user-attachments/assets/f7861111-5a2e-4399-81a9-457446234141" />
                <img width="872" height="1128" alt="Screenshot 2026-04-14 172819" src="https://github.com/user-attachments/assets/7def71d4-c2a7-4910-b01e-c2069c0cfd3d" />
            <p><em>- Successful.</em></p>




            
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
                
                


                




















            












 





