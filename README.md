# UltimateMediaServer

Hey All, Thanks for coming to this Repo which I will be loading written guides into as I produce videos on TikTok guiding you through how I have my home media server setup!

My plan for the parts to upload on TikTok is simple(ish)

<ol>
   <li>Installing TrueNAS Core, Network Settings, Creating a zDev, Creating a Group and User, Creating a Windows SMB share</li>
  <li>Installing Plex in a BSD Jail, Mounting the zDev to Plex, Importing some cotent</li>
  <li>Installing Linux Mint in a VM, Setting local network Settings</li>
  <li>Connecting the VM to VPN, Setting up share Mount Points</li>
  <li>Installing Jackett on the VM, Adding trackers</li>
  <li>Installing Radarr and Sonarr on the VM</li>
  <li>Setting up Sonarr/Radarr to connect to Jackett Trackers</li>
  <li>Installing Transmission-Daemon and Configuring</li>
  <li>Workflow Walkthrough</li>
  <li>Setting Up Ombi/Black</li>
</ol>

(I may also create 2x bonus parts about setting up DynamicDNS and Wireguard)

Overall the process to get this whole system setup is not too complex, it mostly involves just clicking through menus ans pasting in linux commands (main reason to write a guide). Initially my first build of this setup took me about 2 full days worth of work collating all of the information which is one of the driving forces to put this guide together, put all the distributed info in one place

The classic developer addage of;

>Why do a task manually in 6 minutes, when you can spend 6 hours failing to automate it

## FAQ

Q: Why TrueNAS?

A: I originally wanted to run just the NAS and Plex jails (I didn't know about the Servarr project) so TrueNAS Core was sufficient


Q: Why not use Streaming Services and not do all this work?

A: Well because its expensive and tedious, in Australia you realistically want 7 (Netflix $16.99, Binge $14, Stan $14.99, Disney+ $11.99, Apple TV+ $7.99, Prime $6.99, Paramout+ $8.99) all those work out to $81.94 a month which is shitloads. The ongoing cost with this setup is the VPN which I think mine works out to about ~$3 a month

