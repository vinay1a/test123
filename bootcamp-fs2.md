**NOTE: USE ONLY SET SHARE PATH ,SHARE PERMISSION ,OWNERSHIP IN ACL SETTING
Create NAS disks disk1(for normal shares),disk2(for projct Quota) and BIO disk3(for ISCSI) .** 

## 1. Create 5 shares on disk1 and 8 users 

### Shares:

1. Artwork_Ingest 
2. Raw_data 
3. Final_data 
4. Final_edit 
5. Editor

### Users:

1. artwork 
2. admin 
3. editor 
4. satypal 
5. nagendra 
6. umesh 
7. rahul 
8. trendra


|share/users| Artwork_Ingest | Raw_data  |  Final_data |   Final_edit  |Editor|
| :------- | ----: | :---: |:------:  | :-----:|:-----:|
|  admin   | RW    |RW     |  RW      |RW      |RW     |
|  artwork | RW    |R      | RW       |    R   | R     |
|  editor  | R     | R      | RW      | RW     |  RW   |
|satypal   |  R    |  R     |   X     |  R     |  RW   |
|nagendra  |    X  | R      | R       |    RW  |   RW  |
|umesh     |    X  |  R     |  X      |  RW    | RW    |
|rahul     |  RW   |  RW     | RW     |   RW   |  RW   |
|trendra   |  RW   |  RW     | RW     | RW     |   R   |

R—Read only
RW—Read write both

* Take a screenshot of dispalying all users in FS2 and share upload in git

  - user.png
  - share.png

* login as  admin and create admin directory in all share and show property of admin folder in all share by right click and upload the image in git.

  - artwork_ingest.png 
  - raw_data.png 
  - final_data.png 
  - final_edit.png 
  - editor.png

## 2. Create a share netweb on disk1 Give ownership to admin.

* Create two directory in netweb FBD and delhi 
* rahul can do  
  - Read write in delhi.
  - Read only on FBD .
* umesh can do 
  - Read write on FBD.  
  - Read Only on delhi.

* take screenshot of rahul access  delhi share name it 
  - rahul_delhi.png
* take a screenshot of failure access of rahul_fbd.png

set the limit for each user 10 GB.
Login as rahul and try to copy 15 GB file error should come 
take screen shot upload as rahul_limit.png

3.Create one share final, deny this share by specific IP
try to login with one unrestricted IP and create one folder data upload access_ip.png
try to login with restricted IP and upload screen shot deny_ip.png

4.Create ISCSI target and connect disk3 on it and access it on windows with the specific initiator .
Take screenshot of Manage disk showing that disk upload image as iscsi_disk.png

5.On disk1 create any nfs share and mount it on linux system using nfs.
Put the output of command df -h in nfs_mount.md file

6.Configure one FTP share for Public aceess on disk1. (use share name NTIPL)
upload ftp_public.png
and secound share tyrone only authenticated user admin can read wirte
upload ftp_user.png

7.Lun masking iscsi initiator resticted to windows share in question 4 try to mount in linux system and put error in iscsi_lun_masking.md .


8.In Question 1 do recycling and auditing enable on final_data create and delete few files from final data and upload image recycle.png and put output of message file from audit share in audit_log.md

9.Create Share FIT on disk2 and allow the admin with full permision on  it but this share should have the limit of 10 GB .
Copy 15 GB data on this folder it will give error upload project_quota.png file.

Bonus Questions:
10.Connect ADS Server with FS2 .
Create a share ADS_TEST give permission to peg user from ADS server on this share. 
