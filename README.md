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
        <h3>Step 9: Test Each Host By Pinging Around The HQ Network From Each Host And Between Each Host</h3>
                <img width="870" height="342" alt="Screenshot 2026-04-14 173542" src="https://github.com/user-attachments/assets/12edeccd-33e6-4a84-9530-a5d388bdd05d" />
                <img width="872" height="338" alt="Screenshot 2026-04-14 173628" src="https://github.com/user-attachments/assets/dc404566-cde9-4759-8438-57a289678ab5" />
                <img width="871" height="346" alt="Screenshot 2026-04-14 173700" src="https://github.com/user-attachments/assets/2cdc4c1d-db2e-43ba-be29-3907caece447" />
            <p><em>- Successful.</em></p>
        <h3>Step 10: Test IP Connectivity To The Internet By Pinging Google Server 8.8.8.8</h3>
            <p><em>- Successful. (See Step 8)</em></p>
        <h3>Step 11: Test DNS And Website Connectivity By Using The Web Browser On Each Host To Access Www.Google.Com</h3>
                <img width="540" height="548" alt="Screenshot 2026-04-14 173901" src="https://github.com/user-attachments/assets/df7de72c-5af4-4fc3-afa2-dbd10b001b4d" />
                <img width="526" height="650" alt="Screenshot 2026-04-14 173943" src="https://github.com/user-attachments/assets/6496d9e0-e8eb-44c2-9c34-147ce170856a" />
                <img width="487" height="660" alt="Screenshot 2026-04-14 174020" src="https://github.com/user-attachments/assets/5916bf89-8480-42e8-8990-8cf437cb89ad" />


                

                
                


                




















            












 





