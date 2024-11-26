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
2. Create a **Virtual Network** and Subnet.  
3. Create the Domain Controller VM (Windows Server 2022) named `DC-1`:  
   - **Username**: `labuser`  
   - **Password**: `Cyberlab123!`  
4. After the VM is created, set the **Domain Controller’s NIC Private IP address** to be static.  
5. Log into the VM and disable the **Windows Firewall** (for testing connectivity).  

---

## Setup Client-1 in Azure  
1. Create the Client VM (Windows 10) named `Client-1`:  
   - **Username**: `labuser`  
   - **Password**: `Cyberlab123!`  
2. Attach the Client VM to the **same region and Virtual Network** as `DC-1`.  
3. After the VM is created, set `Client-1`'s **DNS settings** to `DC-1`’s Private IP address.  
4. From the **Azure Portal**, restart `Client-1`.  
5. Log in to `Client-1`.  
6. Attempt to **ping `DC-1`’s private IP address**:  
   - Ensure the ping succeeded.  
7. From `Client-1`, open **PowerShell** and run `ipconfig /all`:  
   - Verify that the DNS settings show `DC-1`’s Private IP Address.  

---

## Finish the Lab  
- Do not delete the VMs in Azure, as they will be used in upcoming labs.  
- If you are done for the day and want to save money, simply **“Stop”/turn off the VMs** within the Azure Portal.  

---
