# SSH Key Generation & Server Setup Guide

A simple, step-by-step guide for developers to generate a secure SSH key pair and register it on a remote server.

---

## 1. Generate a New SSH Key Pair

We recommend using **Ed25519** as it is more secure and faster than RSA.

Open your local terminal and run:

```bash
# 1. Create the .ssh directory if it doesn't exist
mkdir -p ~/.ssh
chmod 700 ~/.ssh

# 2. Generate the key pair
# (Replace your_email@example.com with your actual email)
ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519_server -C "your_email@example.com"
```

* **Passphrase:** Press **Enter** to leave it empty (recommended for automated deployments/scripts), or type a passphrase for extra security.

This generates two files in `~/.ssh/`:
- **Private Key:** `id_ed25519_server` (Keep this secret! Never share or commit this file)
- **Public Key:** `id_ed25519_server.pub` (This is safe to share and register on servers)

---

## 2. Register the Public Key on the Server

To log in without entering a password, you need to copy your **Public Key** (`.pub`) to the target server.

### Option A: Using `ssh-copy-id` (Easiest)
Run this command from your local machine:
```bash
ssh-copy-id -i ~/.ssh/id_ed25519_server.pub user@server_ip
```
*(Replace `user` with the server username, e.g., `root`, and `server_ip` with the server's IP address).*

### Option B: Manual Registration (If `ssh-copy-id` is not available)
1. Print and copy your public key content:
   ```bash
   cat ~/.ssh/id_ed25519_server.pub
   ```
2. Log in to your server and run:
   ```bash
   # Create the .ssh directory on the server if it doesn't exist
   mkdir -p ~/.ssh
   chmod 700 ~/.ssh

   # Open the authorized_keys file
   nano ~/.ssh/authorized_keys
   ```
3. Paste the public key string into a new line, save, and exit.
4. Set the correct permissions on the server:
   ```bash
   chmod 600 ~/.ssh/authorized_keys
   ```

---

## 3. Test the Connection

Verify that you can connect using your new key without a password prompt:

```bash
ssh -i ~/.ssh/id_ed25519_server user@server_ip
```

---

## 4. (Optional) Simplify with SSH Config

To avoid typing the full command and key path every time, you can configure your SSH client.

1. Open (or create) the config file locally:
   ```bash
   nano ~/.ssh/config
   ```
2. Add the following block:
   ```text
   Host my-server
       HostName server_ip
       User user
       IdentityFile ~/.ssh/id_ed25519_server
   ```
3. Now you can connect simply by running:
   ```bash
   ssh my-server
   ```
