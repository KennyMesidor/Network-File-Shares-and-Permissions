# Network-File-Shares-and-Permissions

<p align="center">
<img src="https://i.imgur.com/AeiqMDZ.png" alt="Traffic Examination"/>
</p>

In this lab, we will share resources over a network by creating files and configuring permissions to allow read, write, or deny access for individual users and groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Domain Controller/Client Machine)
- Remote Desktop
- Shared Network Files

<h2>Operating Systems Used </h2>

- Windows 10</b>

<h2>List of Prerequisites</h2>

- A Virtual Machine used as a Domain Controller with AD DS
- A Virtual Machine used as a Client 

<h2>Lab Steps</h2>

<p>
<img src="https://i.imgur.com/IX7eI1M.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Sign in to DC-1 using the domain administrator account (mydomain.com\ken_admin) and log into Client-1 with a standard user account (mydomain<someuser>).
On DC-1, open the *C:* drive and create four folders:

read-access

write-access

no-access

accounting
</p>
<br />

<p>
<img src="https://i.imgur.com/YpWvuuh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On DC-1, set up the folder permissions and shares as follows:

For the read-access folder, grant the Domain Users group Read permissions.

For the write-access folder, grant the Domain Users group Read/Write permissions.

For the no-access folder, grant the Domain Admins group Read/Write permissions.

Leave the accounting folder unchanged for now—no permissions need to be configured yet.
</p>
<br />

<p>
<img src="https://i.imgur.com/mJLXlBj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Uuy43Na.pngg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On Client-1, sign in using a standard user account and open File Explorer. In the address bar, enter \dc-1 to display the shared folders. Test access to each folder:

You should be able to open the read-access folder, but only view its contents—you won’t be able to modify anything.

The write-access folder should allow full access, meaning you can create, edit, and delete files.

Access to the no-access folder will be blocked, since it is limited to Domain Admins only.
</p>
<br />

<p>
<img src="https://i.imgur.com/xsdCaQp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On DC-1, open Active Directory Users and Computers (ADUC). Create a new organizational unit (OU) called _GROUPS. Inside this OU, create a new security group named ACCOUNTANTS.
</p>
<br />

<p>
<img src="https://i.imgur.com/cZo9Poi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Back in ADUC on DC-1, add several domain users to the newly created ACCOUNTANTS group. To do this, right-click the ACCOUNTANTS group, choose Properties, go to the Members tab, and add the users you want included.

After adding the members, grant the ACCOUNTANTS group Read/Write permissions on the accounting folder.
</p>
<br />

<p>
<img src="https://i.imgur.com/HzkNmDO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Restart Client-1, then sign in using the user account you added to the ACCOUNTANTS group. Open File Explorer and enter \dc-1 in the address bar to view the shared folders. Try opening the accounting folder—because the user is now a member of the group with Read/Write permissions, access should be granted.
</p>
<br />
