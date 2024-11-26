# Azure Lab: Setup Domain Controller and Client

This guide outlines the steps to set up a Domain Controller and a Client VM in Azure.

---

## Prerequisites  
Before starting this lab, ensure you have:  
1. An **Azure account** with sufficient permissions to create resources.  
2. A basic understanding of **Virtual Networks (VNets)** and **Subnets** in Azure.  
3. Remote Desktop Protocol (**RDP**) client installed to connect to the VMs.  
4. Access to the following credentials:  
   - **Domain Controller**  
     - Username: `labuser`  
     - Password: `Cyberlab123!`  
   - **Client-1**  
     - Username: `labuser`  
     - Password: `Cyberlab123!`  
5. The following software installed on your local machine:  
   - **PowerShell** for testing configurations.  
   - A tool to monitor or verify network connectivity (e.g., `ping`).  

---

## Setup Domain Controller in Azure  
1. Create a **Resource Group**.
   
![image](https://github.com/user-attachments/assets/bc1f53f4-fd60-4827-ada5-40f0861398d3)

3. Create a **Virtual Network** and Subnet.

![image](https://github.com/user-attachments/assets/c182a2da-5811-4886-9dad-b4ebdb556a5c)

5. Create the Domain Controller VM (Windows Server 2022) named `DC-1`:  
   - **Make sure its in the right region or it won't work** 
   - **Username**: `labuser`  (or whatever you want)
   - **Password**: `Cyberlab123!`
![image](https://github.com/user-attachments/assets/fba9844c-1338-457f-bedc-9f2e6222b313)

7. After the VM is created, set the **Domain Controller’s NIC Private IP address** to be static.
   
![image](https://github.com/user-attachments/assets/bd648639-3fce-4420-a5c8-f6eb6e8b7b4d)
  
  **Now RDP in using the public IP for DC-1**
  
9. Log into the VM and disable the **Windows Firewall** (for testing connectivity).
    - Right click the start menu
    - Then click "run"
    - type wf.msc (Windows Firewall)
      
   ![image](https://github.com/user-attachments/assets/573dbb76-afa7-465f-b2f9-04d677e26b6b)

   ![image](https://github.com/user-attachments/assets/7c21d8ab-a703-43fc-9802-562ff9a9a54f)

---

## Setup Client-1 in Azure  
1. Create the Client VM (Windows 10) named `Client-1`:  
   - **Username**: `labuser`  
   - **Password**: `Cyberlab123!`
     
![image](https://github.com/user-attachments/assets/aa33b27b-8d94-497d-8545-46fa5c9b4439)

2. Attach the Client VM to the **same region and Virtual Network** as `DC-1`.  
3. After the VM is created, set `Client-1`'s **DNS settings** to `DC-1`’s Private IP address.

   ![image](https://github.com/user-attachments/assets/f96fe297-a4cc-4e20-9e21-ddb45ce0829a)

    - This allows us to join them into a Domain.
      
5. From the **Azure Portal**, restart `Client-1`.  
6. Log in to `Client-1`.  
7. Attempt to **ping `DC-1`’s private IP address**:  
   - Ensure the ping succeeded.
     
     ![image](https://github.com/user-attachments/assets/09fbfca3-44f9-4b58-9c2a-778f08799c2b)

8. From `Client-1`, open **PowerShell** and run `ipconfig /all`:  
   - Verify that the DNS settings show `DC-1`’s Private IP Address.

   ![image](https://github.com/user-attachments/assets/ed9771b2-ddac-440b-bab4-a8a27c545f26)


---

## Finish the Lab  
- Do not delete the VMs in Azure, as they will be used in upcoming labs.  
- If you are done for the day and want to save money, simply **“Stop”/turn off the VMs** within the Azure Portal.  

---
