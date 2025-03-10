
Job control is a feature in Unix-like operating systems that allows users to **start, stop, pause, resume, and manage multiple processes (jobs) in a single shell session**. It is particularly useful when working with multiple tasks in the terminal.
```sh
$ jobs -l
[1]  + 12345 Running    ping google.com > output.txt &
[2]  - 12346 Stopped    nano file.txt
```
---
# **Job Statuses**

| **Status**     | **Description**                                                                               |
| -------------- | --------------------------------------------------------------------------------------------- |
| **Running**    | The job is actively executing in the foreground or background.                                |
| **Stopped**    | The job is paused (suspended, CTRL+Z) and not executing until resumed.                        |
| **Terminated** | The job has finished execution or was manually killed.                                        |
| **Done**       | The job completed successfully.                                                               |
| **Killed**     | The job was forcefully terminated using `kill` or `Ctrl + C`.                                 |
| **Exited**     | The job finished, either successfully (`exit code 0`) or with an error (`nonzero exit code`). |
| **Continued**  | The job was previously stopped but has now resumed execution.                                 |

---
# **Job States**
A Job can be in one of two states:
1. **Foreground**: Running interactively in the terminal.
2. **Background**: Running but detached from the terminal, allowing other commands to be executed.
---
# **Managing Jobs**
### **Start a Process in the Background**
```sh
$ command &
# Example
$ ping google.com > output.txt &
$ cat file.txt &
$ vim file.txt &
```
### **View Running Jobs**
```sh
$ jobs -l
[1]    12345 Running    ping google.com > output.txt &
[2]  - 12346 Stopped    nano file.txt
[3]  + 12347 Stopped    vim file.txt
```
- `+` marks the most recent job.
- `-` marks the second-most recent job.
### **Move a Running Process to the Background**
If you start a process normally but want to send it to the background **Pause it** using `Ctrl + Z` (suspends the process) Then **Resume it in the background** `bg`
```bash
$ ping google.com
PING google.com (172.217.171.238) 
64 bytes: icmp_seq=1 ttl=114 time=45.9 ms
64 bytes: icmp_seq=2 ttl=114 time=45.0 ms
^Z
[1]+  Stopped                 ping google.com
$ bg
```
### **Bring a Background Job to the Foreground**
```sh
$ fg %job_number
```

```bash
# Example
$ jobs -l
[1]    12345 Running    ping google.com > output.txt &
[2]  - 12346 Stopped    nano file.txt
$ fg %1
64 bytes: icmp_seq=356 ttl=114 time=45.9 ms
64 bytes: icmp_seq=357 ttl=114 time=45.0 ms
```
### **Killing a Job**
```sh
kill %job_number
```
Alternatively, use `kill` with a **PID** (Process ID):
```sh
kill 12345
```
To forcefully terminate:
```sh
kill -9 12345
```
### **Stopping a Job**
Press `CTRL+Z` while the process is on the forground or use `kill -l %job_number`
```bash
$ kill -l %job_number
```
### **Resuming a Stopped Job**
To resume in **foreground**:
```sh
$ fg %job_number
```
To resume in **background**:
```sh
$ bg %job_number
```
---
# **Job Control Shortcuts**

| Shortcut       | Description                                  |
| -------------- | -------------------------------------------- |
| `Ctrl + Z`     | Suspend (pause) the foreground job           |
| `Ctrl + C`     | Kill the foreground job                      |
| `Ctrl + D`     | Exit the shell (if no jobs are running)      |
| `fg`           | Resume the most recent job in the foreground |
| `fg %N`        | Resume job **N** in the foreground           |
| `bg %N`        | Resume job **N** in the background           |
| `jobs`         | List all background and suspended jobs       |
| `disown -h %N` | Keep job running after logout                |
| `kill %N`      | Kill job **N**                               |

---
# **Example Workflow**
1. **Start a Process**
    ```sh
    nano file.txt
    ```
    (You realize you need the terminal free.)
2. **Suspend the Process**  
    Press:
    ```sh
    Ctrl + Z
    ```
    (Job is now "Stopped.")
3. **Send it to the Background**
    ```sh
    bg %1
    ```
    (`nano` continues running in the background.)
4. **List Active Jobs**
    ```sh
    $ jobs -l
    [1]  + 4567 Running    nano file.txt &
    ```
5. **Bring `nano` Back to the Foreground**
    ```sh
    fg %1
    ```
6. **Kill the Job**
    ```sh
    kill %1
    ```
---