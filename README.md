# Raspberry-Pi-5-OS
Raspberry Pi 5 OS System Administration Basics with systemd &amp; Python3

Notes:

* The inxi command (with options) on my Debian Trixie Raspberry Pi OS
   yields the following partial output-

  System:

   Host: raspberrypi Kernel: 6.12.47+rpt-rpi-2712 arch: aarch64 bits: 64
    compiler: gcc v: 14.2.0 Desktop: LXDE v: N/A Distro: Debian GNU/Linux 13 (trixie)

   Machine:
   Type: ARM System: Raspberry Pi 5 Model B Rev 1.0 details: N/A rev: ...

* If you want to run the Debian Trixie version of the Raspberry Pi OS,
   you should do it as a bare metal install on a fresh microSD card,
   and then transfer it to a NVMe SSD as shown in the book.
   I'm in the process of verifying everything in the book on the new
   version, and will keep you posted about any differences (if any)
   between the Debian Bookworm version and the Debian Trixie version.

* In Chapter 2, page 210, the sudo who -r command can be replaced with
  the following bash command to obtain the legacy run level:

  systemctl get-default | sed -E 's/.target$//' | awk '

  $0=="graphical"     {print 5; exit}

  $0=="multi-user"    {print 3; exit}

  $0=="rescue"        {print 1; exit}

  $0=="emergency"     {print 0; exit}

  {print "unknown"}'

* In Chapter 3, whenever you're using Way 3 (Import Script Mode)
   you must remember to give execute privilege to the file you are
   going to import into Python3 with the command:

   chmod u+x filename 

* Section 1.2.4 works exactly as shown in the Trixie version of
   the Raspberry Pi OS. In step 4.d. on page 50, the reboot then
   happens from the uninitialized NVMe device, so you have to go
   through the steps to setup the system on the NVMe device.

* The website for this book at Taylor & Francis is as follows-
   
   https://www.routledge.com/Raspberry-Pi-5-System-Administration-Basics/Koretsky/p/book/9781041099031

* I've added all of the Python 3 code examples, they're in the file

   py_code.zip

* I added all of the In-Chapter Exercise solutions, as the following-

   Chap0_ICE.docx, Chap1_ICE.docx, Chap2_ICE.docx, Chap3_ICE.docx

Last modified 11/5/2025
