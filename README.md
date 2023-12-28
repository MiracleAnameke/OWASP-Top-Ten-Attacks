#  Web Security
## OWASP Top Ten Attacks

### Lab Requirements
- Internet connectivity & VMware Workstation version 15.5.7 or above
- Windows Server 2016 VM and Kali Linux VM prepared with necessary software

### Lab Tasks and Screenshots

### Part 01: IIS 10.0 Role Setup
**Task**: Install and configure IIS 10.0 on Windows Server 2016.
- **Steps**:
    1. Start Windows Server 2016 VM.
    2. Navigate to Server Manager -> Manage -> Add Roles and Features.
    3. Select Role-based or Feature-based installation and the current server.
    4. Choose Web Server (IIS) role and under Role Services, add FTP Server -> FTP Services.
    5. Confirm and Install.
    6. Verify installation by accessing the default IIS web page from Kali Linux.
- **Slide 01**: Screenshot showing default IIS web page and server configuration.
    <img src="https://i.imgur.com/UDGAMK1.png" height="400px" width="auto" alt="IIS 10.0 Role Setup"/>

### Part 02: Install OWASP Juice Shop
**Task**: Install OWASP Juice Shop on Windows 2016 Web Server.
- **Steps**:
    1. Add a network adapter to Windows Server for internet access.
    2. Download and install Node.js and Git for Windows.
    3. Clone Juice Shop repository and navigate to the directory.
    4. Run `npm install` and `npm start`.
    5. Verify by accessing `http://folusername-iis:3000` from Kali Linux.
- **Slide 02**: Screenshot showing the OWASP Juice Shop running on the server.
    <img src="https://i.imgur.com/Q0wgmqy.png" height="400px" width="auto" alt="OWASP Juice Shop Installation"/>

### Part 03: Set Up Burp Suite
**Task**: Configure and use Burp Suite for web application security testing.
- **Steps**:
    1. Open Burp Suite Free Edition on Kali Linux.
    2. Set up a new temporary project with default configurations.
    3. Configure proxy settings and ensure the correct IP and Port are assigned.
    4. Set up Firefox on Windows 10 to use Burp Suite as its proxy.
    5. Test the configuration by attempting to navigate to a website and intercepting the request.
- **Slide 03**: Screenshot showing Burp Suite intercepting HTTP traffic.
    <img src="https://i.imgur.com/hTEMax8.png" height="400px" width="auto" alt="Burp Suite Setup"/>

### Part 04: Burp Suite Interception and Certificate Installation
**Task**: Demonstrate the interception of web traffic with Burp Suite and the subsequent installation of the PortSwigger certificate to trust the CA.

**Steps**:
1. **Intercept Web Traffic**: With Burp Suite's interception feature turned on, attempt to navigate to a website (like www.google.ca) using Firefox on Windows 10. Observe the "connection has timed out" or "connecting" message due to the interception.
2. **Toggle Interception**: Click on the "Intercept is on" button in the Burp Suite (Proxy tab -> Intercept sub-tab) to toggle interception off.
3. **Observe Certificate Error**: Refresh the www.google.ca page. Due to the proxying through Burp Suite, a certificate error should appear indicating that the site's security certificate is not trusted.
4. **Export and Install Burp Suite Certificate**:
    - Navigate to http://burp to access the Burp Suite's certificate download page.
    - Click on the CA Certificate link and save the certificate to your desktop.
    - Open Firefox's Certificate Manager (Options -> Privacy & Security -> Certificates -> View Certificates -> Authorities tab).
    - Import the downloaded PortSwigger CA certificate and trust it to identify websites.
    - Refresh the www.google.ca page and ensure no security warnings are presented, indicating successful certificate trust.

- **Slide 04**: open the Certificate Manager window again and highlight PortSwigger CA certificate as shown below
    <img src="https://i.imgur.com/TgJXzN3.png" height="400px" width="auto" alt="Burp Suite Interception and Certificate Installation"/>

### Part 05: Directory Traversal
**Task**: Demonstrate a directory traversal attack on a vulnerable application.
- **Steps**:
    1. Open Firefox and navigate to Mutillidae home page on Kali VM.
    2. Explore directory structure of Mutillidae to find sensitive files or directories.
    3. Document any findings and implications of the directory traversal vulnerability.
- **Slide 05**: Screenshot showing directory listing or sensitive file access due to traversal.
    <img src="https://i.imgur.com/xpg53mO.png" height="400px" width="auto" alt="Directory Traversal"/>

### Part 06: XML External Entity Injection
**Task**: Perform an XML External Entity (XXE) injection attack.
- **Steps**:
    1. Navigate to the XML External Entity Injection page in Mutillidae.
    2. Craft and submit malicious XML to the server.
    3. Observe and document the impact of the XXE injection on the server.
- **Slide 06**: Screenshot showing the results of the XXE injection.
    <img src="https://i.imgur.com/oxQ1Wg1.png" height="400px" width="auto" alt="XXE Injection Results"/>

**Conclusion**: This lab provides practical experience in identifying and exploiting common web vulnerabilities. Understanding these vulnerabilities and how they can be exploited or mitigated is crucial for web security.
