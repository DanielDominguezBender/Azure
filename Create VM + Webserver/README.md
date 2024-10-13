
# Labs-Azure-Create-a-VM-machine

On this lab I will create a VM machine and run a web server that will be accessible via a public ip assigned by Azure.
I have split this lab in 3 parts:

1) Creation of VM machine
2) Connection to VM machine via RDP
3) Install the web server and access it

**1 - Creation of the VM machine:**

I've created a VM machine in the AZURE portal by entering to https://portal.azure.com/ and using my Microsoft credential to access.

![image1](imgs/image1.png)

Also activated the TFA for more security.

![image2](imgs/image2.png)

Once inside Microsoft Azure, I selected the Virtual Machine icon. On the next page selected **Create >> Azure virtual machine**.
![image3](imgs/image3.png)

![image4](imgs/image4.png)

Once the new configuration windows opens, I started filling out the following fields.
I did it like follows:

- Subscription: Azure for Students
- Resource group: AZ-900L01-newVM-GR
- Virtual machine name: myVM
- Region: North EU
- Availability options: No Infrastructure redundancy required
- Image: Windows Server 2019 Datacenter - x64 Gen3
- Size: Standard D2s v3
- Username: azureuser
- Password: "create something easy to remember as it's for testing purpose only"
- Select inbound ports: HTTP(80), RDP(3389)

Now selected **Next: Disks >**
![image5](imgs/image5.png)

Once in the new page, I selected the option **Networking** and checked again for the **Public inbound ports**, just in case something changed (it should be still HTTP(80) & RDP(3389)).

![image6](imgs/image6.png)

Then selected **Next: Management >**

On this new page, I selected **Monitoring** and looked for the option **Boot diagnostics**, I selected **Disable** option.

![image7](imgs/image7.png)

Let the other fields as they are per default and clicked on the button (in blue color) **Review + create**.

After the validation, I could see how much the VM will cost in **currency / hr**.
Clicked on **Create** to proceed.
![image8](imgs/image8.png)

**2 - Connect to VM via RDP:**

On this part I will connect to the vm machine using RDP. 
Once deployment succeeded, I clicked on **Go to resource**.

![image10](imgs/image10.png)

On the next page, clicked on dropdown list **Connect** and selected **Connect** again.

![image11](imgs/image11.png)

On this page, I kept everything as it is per default in order to connect with the public address over RDP (3389).
Clicked on **Download RDP File** and opened the downloaded file.

**Note**: In case you are using a MAC like I do, please download the **Windows App** by following the steps explained in this link: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-mac<br>
Once you have downloaded the app, you will see that the icon of the downloaded RDP file has changed to something like:

![image13](imgs/image13.png)

I double clicked on it to open the RDP session. It opened a prompt asking for  credentials of the VM.

![image14](imgs/image14.png)

Also asked for accepting the certificate for the connection.

![image15](imgs/image15.png)

Once done, I could start enjoying my VM.

![image20](imgs/image20.png)

**3 - Install Web-Server and access it via Public IP:**

Once inside the VM machine, I opened **Powershell** with admin rights in order to install the Web-Server.

![image17](imgs/image17.png)

The command used in Powershell:
```powershell
Install-WindowsFeature -name Web-Server -IncludeManagementTools
```

![image18](imgs/image18.png)

I could see the instalation process starting.

![image19](imgs/image19.png)

I was sure all was successfully installed once I saw the following prompt:

![image21](imgs/image20.png)

To check the Web-Server, I just went back to the overview page in Azure and opened a new browser page using the Public IP assigned to my machine.

![image22](imgs/image22.png)

By entering the IP in the URL I could see my Web-Server running. :)

![image23](imgs/image23.png)

Now in order to avoid the machine running after this testing, I just clicked on **Stop**. 

![image24](imgs/image24.png)

And as a last step I made sure to delete the machine.

![image26](imgs/image26.png)

Just made a **refresh** to be sure the machine was deleted.

![image27](imgs/image27.png)
