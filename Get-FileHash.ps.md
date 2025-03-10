#command #powershell

**`Get-FileHash`** is a powershell [[cmdlet]] used to calculate and return the [[Hashing|Hash Value (Digest)]] of a file.

```powershell
Get-FileHash <file_path> [-Algorithm <hash_algorithm>]
```
### Hash Algorithms
- **MD5**: Generally used for quick file checks but is not considered secure.
- **[[Secure Hash Algorithm 1 (SHA-1)|SHA-1]]**: Also used historically but now considered insecure.
- **[[Secure Hash Algorithm - 256 (SHA-256)|SHA-256]]** (**default**):  widely used and secure.
### Usage
```powershell
# Get the SHA-256 digest of yap.txt
PS C:\Users\larry> Get-FileHash .\yap.txt 

Algorithm       Hash 
---------       ----  
SHA256          83A9561781C8D86E5E43F9F88FA62D3264BEA856A671F2D2F35E9299ABC37B46
```

```powershell
#Get the MD5 Hash value of a file with absolute path
PS C:\Users\larry> Get-FileHash "C:\path\to\file.txt" .\yap.txt -Algorithm MD5

Algorithm       Hash                           
---------       ----                          
MD5             90416817BF120DDEAD54C8639417E218 
```
