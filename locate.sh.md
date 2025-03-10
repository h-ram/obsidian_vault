#command 

used to **quickly find files and directories** by searching a pre-built database instead of scanning the entire filesystem. It is much faster than [[find.sh]] because it relies on an **index** rather than a real-time search.
```
locate [options] filename
```
---
### **Options**

```bash
# locate a file
locate filename1.txt

# update the database
sudo updatedb

# Case-insensitive search
locate -i file.txt

# limiting output
locate -n 5 filename
```
---
### **Difference Between `locate` and `find`**

| Feature                | `locate`             | `find`                             |
| ---------------------- | -------------------- | ---------------------------------- |
| Speed                  | Fast (uses database) | Slow (real-time search)            |
| Real-time Search       | No                   | Yes                                |
| Needs Updated Database | Yes (`updatedb`)     | No                                 |
| Recursive Search       | Implicit             | Must specify (`find / -name file`) |
