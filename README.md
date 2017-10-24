  ___ ___ ___ ___ ___ ___ _____   ___  ___   _   ___ 
 |   \_ _/ __/ __| __/ __|_   _| / __|/ __| /_\ | _ \
 | |) | |\__ \__ \ _| (__  | |   \__ \ (__ / _ \|   /
 |___/___|___/___/___\___| |_|   |___/\___/_/ \_\_|_\
                                                     

===================TABLE OF CONTENTS===================

	ANALYSIS ENVIRONMENT SETUP   1
	STATIC ANALYSIS              2
	DYNAMIC ANALYSIS             3
	CODE ANALYSIS                4
	MEMORY ANALYSIS              5
	OPEN SOURCE INTELLIGENCE     6

===================TABLE OF CONTENTS===================

==================        1         ===================

		ANALYSIS ENVIRONMENT SETUP

Please assure you have done the following.

1.  Install a virtualization software.  Check out Oracle Virtualbox, Xen,  or Vmware Workstation.  (Feel free to choose a different product.)

2.  Grab a x86 OS from: https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/

3.  Grab a copy of Remnux OVA: https://docs.google.com/uc?id=0B6fULLT_NpxMampUWlBCQXVJZzA&export=download

4.  Import the Microsoft VM and REmnux OVA.  Snapshot after install.

5.  Execute the Flare install script on the Microsoft VM.  (https://github.com/fireeye/flare-vm)

6.  Snapshot the Microsoft VM.

7.  Install the Virtualization tools for your host software on the Microsoft Guest and Remnux.

8.  Snapshot the Microsoft VM and REmnux.

9.  Update Remnux per the instructions here:  https://remnux.org/docs/distro/update/

10.  Update Flare Windows VM per the intructions here:  "cup all"  OR https://github.com/fireeye/flare-vm

11.  Snapshot the Flare WIndows VM and REmnux.

12.  Grab a copy of Scar from here: https://github.com/citizenstaar/scar/blob/master/scar.zzz 

13.  Stage a copy on the desktops of both Remnux and Flare VMs.

14.  Change the network for both hosts to "Host Only".

15.  Snapshot both VMs
 
==================        1         ===================

==================        2         ===================

		STATIC ANALYSIS

1.  Drag the unmodified scar.zzz to PEstudio

2.  Select the root node in the tree that should be titled according the current directory of scar and its file name "scar.zzz"

a.  Observe that you have CPU arch the software was developed for, logical size of the file, file type,  and the cryptographic hashes (md5/sha1)

b.  The cryptographic hash and logical size can be used to identify the file on disk or in network logs(like bro file hashes).

c.  The cryptographic hash can be used to search malware repository like Virustotal.  (See section 6 Open Source Intelligence.)

d.  The data observed in item 3 can be used from a host forensic perspective to check disk for the original file being on the endpoint.

3.  Select the node in the tree titled "Indicators".

a.  Observe the types of Indicators and notice what the creators of PEStudio percieve as malicios.

b.  Observe that 22 of 34 indicators were identified with respect to Scar.

c.  Notice that three additional files are identified with their Cryptographic hash (md5.)  Use these in conjunction with the steps in section 6

4.  Select the node for Imported Symbols.  

a.  Notice the blacklisted symbols and the associated function call and library. 

b.  Try to identify function calls that might be indicators of the software having a network communication capability.

c.  Use MSDN to research the purpose of function calls of interest.


Please note that through the example tool we were able to identify indicators for the file to include cryptographic hashes, logical size, embedded file information, and interesting function calls.   The file information can be provided back to intrustion analysts and investigtors to verify aagainst network/host logs or check host file system for indicators.  Also, you should be able to provide a hypothesis on what the capability of th software is based on your review of api calls. 

==================        2         ===================

==================        3         ===================


		DYNAMIC ANALYSIS
<TBA>



==================        3         ===================

==================        4         ===================

		CODE ANALYSIS

<TBA>

==================        4         ===================

==================        5         ===================

		MEMORY ANALYSIS

<TBA>

==================        5         ===================

==================        6         ===================

                OPEN SOURCE INTELLIGENCE

1.  Using collected Indicators of Compromise (IOC) search open repositories for more information:
    (i.e. hashes, domains, ips, etc...)
a.  https://totalhash.cymru.com
b.  https://www.virustotal.com
c.  https://www.threatcrowd.org
d.  https://www.reverse.it

2.  Checking each information source consider what behavorial, static, and comments are made that will enable you.

3.  Never upload a sample if it is related to a active incident...search on IOCs.  Remember the owner of the software
can monitor these sources just like you can.
==================        6         ===================
