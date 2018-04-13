To get root access on Moto e4, first I tried some apps like Kingroot, which can simply root Android without connecting with PC.
But it seems Moto e4 is not in their database. So we need to connect to PC (or Mac) to get root access.

Step 1: Get Developer Option:
  First open the setting app of Moto e4, go to About phone, and tap build numbers multiple times. 
  Then we can see the developer option appers. Go into Deloper option and enbale OEM UNLCOKING and USB DEBUGGING.
  Once done, power off the phone.
  
Step 2: Downlaod FastBoot:
  Because I am using Mac, so here I use Fastboot. There is also a guide on how to use fastboot on Windows.
    Fastboot for Mac: https://thetechslugs.com/wp-content/uploads/2017/08/android-fastboot-mac-linux.zip
    Fastboot for Window: https://forum.xda-developers.com/showthread.php?t=2317790
    
Step 3: Unlock Moto e4
  Before we can install or boot our Moto e4, we need to unlock it. (Note that some phones may already be unlocked)
  First we need to download and install Moto USB driver from https://mobilesupport.lenovo.com/ca/en/solution/MS88481 
  Then connect Moto e4 with the computer using USB, and hold the power and volume down button at the same time to power on and access FastBoot.
  
  Then open the terminal (command line in Windows) and cd into the FastBoot folder we just downloaded at step2.
  There is a file called fastboot. Run the following commands:
  
      ./fastboot oem get_unlock_data
  It will show the bootloader numders of your device.
  Go to https://motorola-global-portal.custhelp.com/app/standalone/bootloader/unlock-your-device-a, follow the instructions and get the unlock code.
  Then run:
      ./fastboot oem unlock [unlock code]
  To unlock the phone.
    
Step 4: Download Magisk for Moto e4:
  For me, I will use Magisk to manage the root access. There maybe some other apps as well.
  Here is a download link for Magisk 16.0:
  https://forum.xda-developers.com/apps/magisk/official-magisk-v7-universal-systemless-t3473445
  Once done, store it on the Moto e4 storage.
  
Step 5: Boot Moto e4 from TWRP:
  First we need to download TWRP. Here is a link for TWRP 3.1.1-0:
  http://www.androiddevs.net/downloads/

  Then please make sure your Moto e4 has been encrypted. (Which means it must have a password)
  Run the following command using terminal:
      
      ./fastboot boot [downloaded TWRP.img]
  
  Then a window will pop up in the phone which requires password. (If not, please check your phone is encrypted)
  After entering the password, we can install Magisk using TWRP.
  
Step 6: Install TWRP.
  Click install and selet the correct storage to find the Magisk we just download. Select it and swipe to flash.
  Note that I faced some problems at this step. 
  If the flash failed, you can try to wipe the cache data. Or try another version of Magisk (Because first I failed with Magisk 13.3 but 16.0 works)
  Also flash no-verity-opt-encrypt using the same way (download link: https://androidfilehost.com/?fid=24459283995297893)
  Once down, reboot the system.
  Then we can see a Magisk installed with two checked mark here, which means we already have the root access.
  
  

      
