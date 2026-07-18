In classful addresses how is that possible to find the prefix length immediately and easily find the class?

In **classful addressing**, you can identify the **class** and the **default prefix length** just by looking at the **first octet** (the first number before the first dot).

Here's the easiest method:

|Class|First Octet Range|First Bits|Default Prefix Length|Default Subnet Mask|
|---|--:|---|---|---|
|A|1–126|0|**/8**|255.0.0.0|
|B|128–191|10|**/16**|255.255.0.0|
|C|192–223|110|**/24**|255.255.255.0|
|D|224–239|1110|Multicast (no default prefix)|—|
|E|240–255|1111|Experimental|—|

### Quick trick to remember

- **Class A → /8**
    
- **Class B → /16**
    
- **Class C → /24**
    

Notice the pattern:

- A = 1 network octet → **8 bits**
    
- B = 2 network octets → **16 bits**
    
- C = 3 network octets → **24 bits**
    

### Examples

**Example 1:** `25.10.20.30`

- First octet = **25**
    
- 25 is between **1 and 126**
    
- **Class A**
    
- Default prefix = **/8**
    

---

**Example 2:** `172.16.5.4`

- First octet = **172**
    
- 172 is between **128 and 191**
    
- **Class B**
    
- Default prefix = **/16**
    

---

**Example 3:** `200.15.8.9`

- First octet = **200**
    
- 200 is between **192 and 223**
    
- **Class C**
    
- Default prefix = **/24**
    

### Shortcut using binary (if asked in exams)

Look at the leading bits of the first octet:

- Starts with **0** → Class A → **/8**
    
- Starts with **10** → Class B → **/16**
    
- Starts with **110** → Class C → **/24**
    
- Starts with **1110** → Class D
    
- Starts with **1111** → Class E
    

### Exam tip

When you see an IP address:

1. Check the **first octet**.
    
2. Determine the **class** from its range.
    
3. Immediately write the default prefix:
    
    - A → **/8**
        
    - B → **/16**
        
    - C → **/24**
        

This method lets you determine both the class and the default prefix length in just a few seconds.