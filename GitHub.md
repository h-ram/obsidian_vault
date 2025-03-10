# Authenticating Git
### **1. HTTPS with Personal Access Token (PAT)**
GitHub **no longer allows password authentication** over HTTPS. Instead, you need a **Personal Access Token (PAT)**.
1. Generate a token:
    - Go to **GitHub > Settings > Developer settings > Personal access tokens**
    - Click **Generate new token** (with necessary scopes like `repo` for private repos).
2. Use the token instead of a password when pushing/pulling:
```sh
    git clone https://github.com/username/repo.git
```
When prompted for a password, **enter the token instead**. (username doesn't matter)
3. **Cache the credentials** (so you don’t enter the token every time):
	```sh
    git config --global credential.helper store  # Enabled credentials saving
	# The next time you enter your token it will be saved.
	```
---
### **2. SSH Authentication**
1. **Generate an SSH key** (if you don’t have one):
    ```sh
    ssh-keygen -t rsa -b 4096 -C "your.email@example.com"
    ```
2. **Add the key to GitHub**:
    - Copy the key:
	```sh
    cat ~/.ssh/id_rsa.pub
	```
    - Go to **GitHub > Settings > SSH and GPG keys** > **New SSH Key**, then paste the key.
3. **Test the connection**:
    ```sh
    ssh -T git@github.com
    ```
4. **Use SSH URLs instead of HTTPS**:
    ```sh
    git clone git@github.com:username/repo.git
    ```
---
### **3. Git Credential Manager (GCM)**
Git Credential Manager (GCM) securely saves your credentials and supports authentication via:
- GitHub username + PAT
- OAuth
 **Install Git Credential Manager (If Not Already Installed)**
	- Windows: Comes with Git for Windows.
	- macOS/Linux: Install with:
```sh
    brew install git-credential-manager
```
 **Enable GCM in Git**
```sh
git config --global credential.helper manager
```
When pushing/pulling, Git will open a browser for authentication.

---
### **4. OAuth with GitHub CLI (`gh`)**
GitHub CLI (`gh`) provides an easier way to authenticate via OAuth.
**Set Up GitHub CLI Authentication**
8. Install GitHub CLI:
    ```sh
    gh auth login
    ```
9. Follow the prompts to authenticate via browser or SSH.
10. Git commands (`clone`, `push`, `pull`) will automatically use the authentication.
---