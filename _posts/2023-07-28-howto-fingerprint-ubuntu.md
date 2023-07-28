---
title: Configure fingerprint reader on Ubuntu 22.04
tags: howto fingerprint ubuntu dell
---
My Dell Latitude 5430 notebook comes equipped with a fingerprint sensor, but unfortunately, the default settings of Ubuntu 22.04 (in my case) do not allow its utilization, even though the *lsusb* command confirms its presence as a *Broadcom Corp. 58200* device.  
This issue has been quite bothersome as I repetitively had to type my password whenever I needed to log back in, again and again. And again. Facial recognition doesn't work, don't even mention that (yes, I have tried [Howdy](https://github.com/boltgolt/howdy), my results were very flaky, unreliable).  
Yesterday I dedicated a few hours to find a solution for enabling biometric authentication and I succeeded. Here is what I did:  
> sudo apt install fprintd libpam-fprintd  
> wget http://dell.archive.canonical.com/updates/pool/public/libf/libfprint-2-tod1-broadcom/libfprint-2-tod1-broadcom_5.12.018-0ubuntu1~22.04.01_amd64.deb  
> sudo apt install ./libfprint-2-tod1-broadcom_5.12.018-0ubuntu1~22.04.01_amd64.deb  
> sudo pam-auth-update  
  
Here go down to *Fingerprint authentication*, hit a space and then a TAB to jump on OK and hit Enter. Now open the Settings --> Users, hit the Unlock button in the top right corner and enable the Fingerprint Login. Enroll your finger/s, lock your machine and test if it works. My notebook's security and user experience have truly been elevated to the next level.  
  
P.S.: there are other fingerprint drivers on [http://dell.archive.canonical.com/updates/pool/public/libf/](http://dell.archive.canonical.com/updates/pool/public/libf/), check which one is compatible with yours.
