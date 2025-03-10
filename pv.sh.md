#command 


**`pv` (Pipe Viewer)** allows you to **view the progress** of data being transferred through a pipeline. 
By default, `pv` provides a simple progress bar, but it can also display various statistics such as the transfer rate, time elapsed, and total data processed.
```bash
pv [options] <inputfile> outputfile
```
You can also pipe data directly into `pv` from other commands.
```bash
<command> | pv
```

---
# **Options**

|**Option**|**Description**|
|---|---|
|`-p`|Show progress as a percentage bar.|
|`-t`|Show elapsed time (time spent processing data).|
|`-e`|Show the estimated time remaining.|
|`-r`|Show the transfer rate (speed of data transfer).|
|`-b`|Show the total number of bytes processed.|
|`-i`|Set the interval (in seconds) to update the progress bar (default is 1 second).|
|`-s`|Display a "spinner" instead of a progress bar.|
|`-f`|Show progress in a "formatted" form, displaying human-readable units (e.g., MB, GB, etc.).|
|`-n`|Show the number of records (lines or bytes) processed.|
|`-l`|Show the length of data processed.|
|`-a`|Use an alternative output format (e.g., use `-a` for a non-interactive mode or log to a file).|
|`-q`|Quiet mode—disables the progress bar and all output except errors.|
|`-c`|Clears the screen before outputting the progress bar.|
|`-h`|Show a help message with a list of options and descriptions.|

> [!NOTE] NOTE
> By default `pv` is using the `-ptreb` options together, so specifying one option (e.g `pv -e` ) will only use that. 

---
# **Usage**
### **File Transfer Progress**
```bash
# Viewing Progress of a File Transfer
$ pv largefile.txt > largefile_copy.txt
10.2MB 0:00:05 [ 2.04MB/s] [========================>] 100% ETA 0:00:00
```
- **`10.2MB`** → The total amount of data processed (file size).
- **`0:00:05`** → The elapsed time (5 seconds in this case).
- **`[ 2.04MB/s]`** → The current transfer rate (2.04 MB per second).
- **`[===========================>] 100%`** → The progress bar, showing 100% completion.
- **`ETA 0:00:00`** → The estimated time remaining (0 seconds, as the operation is complete).

### **Compression Progress**
```sh
pv largefile.txt | gzip > largefile.txt.gz
```
### **Piping Data Between Multiple Commands**
```sh
cat largefile.txt | pv | gzip | ssh user@remote_host 'cat > remotefile.gz'
```
This will:
- **`cat`** the file,
- Show progress as it’s being piped through `pv`,
- Compress the data with `gzip`,
- Send it over SSH to a remote server.
---
# **Installation**
```sh
sudo apt-get install pv
sudo yum install pv
sudo dnf install pv
sudo pacman -S pv
brew install pv
```