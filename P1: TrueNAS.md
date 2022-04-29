# Part 1 : TrueNAS

Okay so to get started you will need a computer to install TrueNAS Core onto, anything with more than 8gb of RAM and 2 Storage Devices is sufficient (One HDD and a USB also works)

I instlled it on a Lenovo ThinkCenter machine for my prod instance, it has an i5 16GB RAM, 256gb Internal SSD, 8GB USB Boot Drive and a 1TB External HDD
I have also installed it on my Dell Poweredge T110 II with an i3 and 8GB RAM, This is ideal as is has more drive bays but for spouse approval we went the MiniPC Route

Firstly, Download the latest TrueNAS Core Stable Build

[TrueNAS Core](https://www.truenas.com/download-truenas-core/)

Also while that is downloading, you should also install these two applications to make life easier for this part;

[Balena Etcher](https://www.balena.io/etcher/)

[Angry IP Scanner](https://angryip.org/)

## Installing TrueNAS

Now we have all of that downloaded, open BalenaEtcher and select the trueNAS ISO, then select your install USB and click Flash. This will take a few minutes then you will get a notification when complete

Insert the USB into the machine you will be using, boot this machine up and keep tapping the key to boot into the boot selection menu (On my T110 its F11 but it changes depending on the make and model of your Motherboard/Computer so you might have to google or try a few times to find the right key to hit)

Once you select the USB from the boot menu, the initial TrueNAS install screen appears, hit ***1*** to boot the installer

On this Blue screen hit ***1*** again

Select the drive you want to boot from by hitting ***Space*** then ***Enter*** (you wont be able to use this drive to store data so use the smallest drive/USB stick)

Now enter a Root Password, this is the main password you wil use to adminsiter the server so make it memorable or you will be locked out, once filled in hit ***Enter***

Select either UEFI or BIOS boot (I think this picks the right option automatically, but usually new consumer machines are UEFI but servers or enterprise is BIOS) and hit ***Enter*

Also hit ***Enter*** to create a SWAP Partition (this helps with Linux Performance)

The machine will install TrueNAS Core, and prompt you to restart

## Setting Up TrueNAS

When you connect the machine to your network, and restart the machine, give it 5 or so minutes to boot, and obtain and IP Address

To find the IP Address, you can use ***Angry IP Scanner*** to search your network, it should auto configure the subnet settings so just click start. Once it finishes you will get a list of all IP Addesses in the range. Click the ***Ports*** heading and sort by ports. You are looking fof the name "truenas.local" with ports 80 and 443 open

Take the listed IP Address and punch it into a web browser in the below format

<code> https://xx.xx.xx.xx/ </code>

You will then get a certificate error in Chrome, hit ***Advanced*** and ***Continue Anyway***

You will see the TrueNAS login screen, Login with the Username ***Root*** and the Password you set in the installer

If all is well you will see the TrueNAS Dashboard!

Now we are in, we need to make some Network changes first

Go to ***Network>Global Configuration***

In this screen you need to set the following settings 

- Hostname: Name you want to call the Server
- DNS Servers: Set atleast Nameserver 1 and 2 (I use the Google DNS 8.8.8.8 8.8.4.4 but you can use any DNS Provider like CloudFlare 1.1.1.1)
- Default Gateway: IP Address of your Router (you can find this from a windows machine command prompt by running the `ipconfig` command and looking for Default Gateway

Next we want to set the static IP by selecting ***Network>Interfaces*** and expanding the ***em0*** interface (may vary) then selecting ***Edit***

In this page make the following changes

-Uncheck DHCP
-Fill in the IP feild (I just use the IP that it was originally assigned)

Once you complete these settings, select ***Apply, test, and save*** the settings

That is it for the Network Settings

Next is to Create the Storage Pool

Go to ***Storage>Pools***

In this page click ***Add*** then ***Create Pool***

Give the Pool a Name, then ***check the disks*** you want to add to the vDev Pool and vlick the Arror

Because we are using Stripe (Most capacity, no redundancy) you will need to check ***Force*** then ***Confirm***

The Pool will generate then become avaliable for data, that's it for the Storage settings

Now we are going into ***Accounts>Groups***

Select ***Add*** and Name the group, no need to change anything else

Now go to ***Accounts>Users***

Select ***Add*** and fill in the settings listed

-Full Name
-Username will auto generate
-Password and Confirm Password (will be used to access the shares)
-Uncheck ***new Primary Group*** and select the group you created before
-Select the Pool you created in the ***Directories and Permissions*** section

Once done, hit ***Submit***

Finally we need to setup a Windows SMB Share (Compatible with Windows, Linux and MacOS) By going to ***Sharing>Windows Shares (SMB)***

Click ***Add***

Select the Pool from the ***Basic*** Area

Enter a ***Name*** then click ***Submit***

And thats everything to make the drives accessible on the Network

Connect to the share by entering the IP Address and name of the Share into a Windows Explorer window in this format `\\xx.xx.xx.xx\SHARE\`


Thanks for reading, come back for Part 2: Installing PLEX





  
