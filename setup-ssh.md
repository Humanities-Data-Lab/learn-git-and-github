# Setting Up Git with SSH on Mac

## 1. Check for Existing SSH Keys
```bash
ls -al ~/.ssh
```
If you see `id_ed25519.pub` or `id_rsa.pub`, you already have a key.

---

## 2. Generate a New SSH Key
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
Press Enter to accept the default file location, then set a passphrase (recommended).

---

## 3. Add the Key to the SSH Agent
```bash
eval "$(ssh-agent -s)"
ssh-add --apple-use-keychain ~/.ssh/id_ed25519
```
> **Note:** If you get an error, the `--apple-use-keychain` flag was renamed in newer macOS versions. Try the following fallbacks:
> ```bash
> ssh-add -K ~/.ssh/id_ed25519
> # or
> ssh-add ~/.ssh/id_ed25519
> ```

---

## 4. Configure `~/.ssh/config`
Open or create the file:
```bash
nano ~/.ssh/config
```
Add the following:
```
Host github.com
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519
```
> **Note:** The `UseKeychain yes` line can cause issues on some macOS versions. If you get an error, either remove that line or add `IgnoreUnknown UseKeychain` above it:
> ```
> Host github.com
>   AddKeysToAgent yes
>   IgnoreUnknown UseKeychain
>   UseKeychain yes
>   IdentityFile ~/.ssh/id_ed25519
> ```

---

## 5. Copy Your Public Key
```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

---

## 6. Add It to GitHub
Go to **GitHub → Settings → SSH and GPG keys → New SSH key**, paste it in, and save.

---

## 7. Test the Connection
```bash
ssh -T git@github.com
```
You should see:
```
Hi username! You've successfully authenticated...
```

---

## 8. Configure Git Identity
```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
```

---

That's it! From now on, clone repos using the SSH URL (`git@github.com:user/repo.git`) and you won't need to enter a password each time.
