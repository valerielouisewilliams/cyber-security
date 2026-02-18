### Cache Timing Attacks: Insights
* Victim program has memory access behavior that is strongly correlated to some secret (like a password)
* Attacker reverse engineers physical addresses corresponding to victim's memory access possibilities (since we wanna find out the location of the secret!)
* Attacker tries to create cache conflicts with these physical addresses
* Victim access of a physical address creates a timing signature for an attacker (i.e. cache hit vs miss). The difference in timing is realted to the type of attack being done.
### Cache Timing Attacks: Difficulty 
* When mapping of secret to memory access is not direct, it requires statistical inference

### DRAM-Based Attacks
* Rowhammer: A vulnerability in modern DRAM (Dynamic Random Access Memory) modules where repeatedly accessing specific memory addresses causes electromagnetic interference.
* Mechanism: This inference causes electrical charges to leak, which can cause a bit flip. 

### DRAM Row Hammer Attack Flow:
1. Locate Target: the attacker identifies two aggressor rows that sandwich a victim row in physical memory.
2. Hammer: the attacker rapdily and repeatedly accesses (reads) the aggressor rows.
3. Cache bypass: the attacker must use clflush (on x86) or other techniques to bypass the CPU cache, ensuring every access goes directly to the DRAM.
4. Bit flip: The electrical charge leaks in the victim row, causing a bit to flip.
This can allow you to become a privileged user (like ROOT in linux machines!!!!!!). Then, you can literally do anything you want. 

### Requirements:
1. Attacker must run code on the same machine as the victim (no network required)
2. Attacker needs knowledge of DRAM physical addressing

### Exploitation Examples:
1. Privilege Escalation: Flipping a bit in a PTE (page table entry) to point to physical memory controlled by the attacker, gaining root access.
2. Data Corruption: Modifying sensitive cryptographic keys or data structures in memory
3. Sandboxing Bypass: Flipping bits in security checks within a web browser or virtual machine.

### Usage
1. Identifying Physical Memory Layout
2. Evading Security Monitors
3. Covert Channels (Data Exfiltration)

### Countermeasures
1. Hardware (DRAM):
* Increased refresh rates: refreshing memory more frequently to restore leaked charges before they cause a flip
* Target Row Refresh: Intelligent DRAM controllers that 


### DELETING A FILE
* When you delete a file from your computer, the OS deleted the inode but not the actual data. So your deleted data is still on the disk somewhere.

### Cold Boot Attack
* Type of physical side channel attack
* Steals encryption keys and other sensitive data from a computer's RAM by leveraging data remnance, which is when memory contents persist for seconds or minutes after power is lost. 
* Attackers force a reboot, dump the RAM contents for their use, and bypass full disk encryption.
* Mechanism: exploits the fact that DRAM and SRAM do not instantly lose their data when power is removed, especially if cooled, which allows data to remain readable.
* Purpose: Used to steal encryption keys like Bitlocker or Filevault keys
* Mitigation: disable hibernation/sleep and set devices to fully shut down which will clear the encryption keys from ram, use hardware based solutions like full memory encryption (found in modern CPUs), BIOS/UEFI security to password protect the BIOS to prevent loading from external media.
