Lecture 2/10/26

# Side Channel Attacks
A security exploit that does not attack the programmer's code/logic directly. Instead, it exploits unintended information leakages from a system.
EXAMPLES: Timing attacks, power analysis attacks, cryptanalysis attacks, cache-based side channel attacks

# Side Channel Attacks vs True Attacks
Focus: Side channel attacks target the implementation of a system, true attacks target the system itself
Methodology: Side channel attacks rely on physical characteristics of the system like power consumption, timing, electromagnetic radiation, etc to extract information
Detection: Traditional security monitoring may not detect side channel attacks, they are non-invasive and can occur without interference with the system's normal operations

# Classification
Physical Source of Leakage: timing, power analysis, other
Attack Techniques: Flush & Reload 

# Timing Attacks
Mechanism: SCA where an attacker infers secret information by measuring how long the system takes to process different inputs
Information Leak: Different input lengths result in different verification time
Example: A password verification function that returns false immediately upon a wrong first letter but takes longer if the first letter is correct
Vulnerable Code: Different execution time depending on the input
Countermeasure: Constant time execution independent of the input (Use XOR to compare characters, no early exit)

# Power Analysis Attack
Mechanism: SCA where the attacker monitors the electrical power consumption of a hardware device like a smart card or microcontroller while it performs cryptographic operations
Information Leak: Different CPU instructions and data values consume different amounts of power

# EM and Acoustic Attacks
EM mechanism: by measuring the radio frequencies radiated by the device's components (CPU, memory, buses)
EM advantage: Less intrusive than power analysis, does not require physical contact with the power supply
Acoustic mechanism: by listening to the sound produced by electromagnetic components... *go back to this slide*

# Cache Based Attacks
Cache Hierarchy + Data Fetching: CPU Core asks for data, L1 Cache is checked first, L2/L3 caches are checked if L1 misses, main RAM is accessed if all caches missed.
Cache Hit: data available in one of the cache levels
Cache Miss: data is not in any of the cache levels, CPU must fetch the data from main memory or RAM

# Cache Timing
L1: ~1 nanosecond
L2: ~2 nanoseconds
L3: ~10-20 nanoseconds
Memory: ~50-100 Nanoseconds

# Memory to Cache Mapping
Each physical address maps to a cache line
Limited space in cache
Evict lines to make room
Three main types of cache mapping:
1. Direct: Each memory block maps to exactly one cache line
2. Fully Associative: Any block can go into any cache line
3. Set Associative: Cache divided into sets, each block maps to a set and can occupy any line within it

