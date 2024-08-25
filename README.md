<p align="center">
<img src="https://imgur.com/nTxP9MK.jpeg" alt="DNS" width=700 height=300/> 
</p>

<h1>DNS Record Management and Cache Clearing</h1>
<p>This tutorial will guide you through managing DNS records and understanding DNS cache behavior using Active Directory and client machines. You’ll create and test DNS A and CNAME records, handle DNS cache, and verify changes.</p>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Microsoft RD Client (Remote Desktop)

<h2>Operating Systems Used </h2>

- macOS Sonoma ***(if you own Macbook Air M1 or M2; it does not matter what type of macOS you own)***
- Windows 10 or Windows 11 Home or Pro ***(if you own either of these OS)***

-----

#### 1. A-Record Exercise
1. **Log In to DC-1**:
   - Use your domain admin account (e.g., `mydomain.com\jane_admin`).

2. **Log In to Client-1**:
   - Use the same admin account (e.g., `mydomain\jane_admin`).

3. **Ping Test**:
   - On **Client-1**, attempt to ping `mainframe`. Note that it fails.

4. **Nslookup Test**:
   - On **Client-1**, perform `nslookup mainframe`. It will fail due to the absence of a DNS record.

5. **Create A-Record**:
   - On **DC-1**, create a DNS A-record for `mainframe` pointing to DC-1’s private IP address.

6. **Verify**:
   - On **Client-1**, ping `mainframe` again. It should now resolve successfully.

#### 2. Local DNS Cache Exercise
1. **Change DNS Record**:
   - On **DC-1**, update the A-record for `mainframe` to point to `8.8.8.8`.

2. **Ping Test**:
   - On **Client-1**, ping `mainframe` and observe that it still resolves to the old IP address.

3. **Check Cache**:
   - On **Client-1**, use `ipconfig /displaydns` to view the local DNS cache.

4. **Flush DNS Cache**:
   - Run `ipconfig /flushdns` on **Client-1** to clear the DNS cache.

5. **Verify**:
   - Attempt to ping `mainframe` again. The ping should now resolve to the new IP address (`8.8.8.8`).

#### 3. CNAME Record Exercise
1. **Create CNAME Record**:
   - On **DC-1**, create a CNAME record for `search` pointing to `www.google.com`.

2. **Ping Test**:
   - On **Client-1**, ping `search` and observe that it resolves to `www.google.com`.

3. **Nslookup Test**:
   - On **Client-1**, perform `nslookup search` and verify that it shows the CNAME record pointing to `www.google.com`.

### Conclusion
You now understand or learn how to manage DNS records by creating A and CNAME records, and handling DNS cache. By following these steps, you observed the effects of DNS record changes and cache clearing on name resolution and network troubleshooting.
