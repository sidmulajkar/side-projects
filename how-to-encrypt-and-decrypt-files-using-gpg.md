1. First of all install GPG and in this gist I'm using Symmetric Encryption

> On Ubuntu, Debian or Arch based systems
```
sudo apt install gpg 
or
sudo dnf install gpg
or
sudo pacman -S install gnupg
```

2. Lets say I want to encrypt the secret.txt file and a folder named secret_folder
```
[sid@sid gpgeg]$ ls
secret_folder  secret.txt
[sid@sid gpgeg]$ cat secret.txt
Follow @sidmulajkar for more instresting stuff on tech!
[sid@sid gpgeg]$
```


3. Now how to encrypt a single file named secret.txt

```
gpg -c --no-symkey-cache --cipher-algo AES256 secret.txt
```

Enter the password/passphrase as a protection

```
[sid@sid gpgeg]$ gpg -c --no-symkey-cache --cipher-algo AES256 secret.txt
[sid@sid gpgeg]$ ls
secret_folder  secret.txt  secret.txt.gpg
[sid@sid gpgeg]$
```

Now how to verify if the encrytion is working or not
> remove the original file to trash or simply move it to another folder to check the gpg decrytion

4. This is how the decryption of works of the secret.txt.gpg

```
[sid@sid gpgeg]$ sudo rm -r secret.txt
[sudo] password for sid:
[sid@sid gpgeg]$ ls
secret_folder  secret.txt.gpg
[sid@sid gpgeg]$ gpg secret.txt.gpg
gpg: WARNING: no command supplied.  Trying to guess what you mean ...
gpg: AES256.CFB encrypted data
gpg: encrypted with 1 passphrase
[sid@sid gpgeg]$ ls
secret_folder  secret.txt  secret.txt.gpg
[sid@sid gpgeg]$ cat secret.txt
Follow @sidmulajkar for more instresting stuff on tech!
[sid@sid gpgeg]$
```


5. Moving on to the folder encryption of secret_folder using the GPG

```
[sid@sid gpgeg]$ ls
secret_folder  secret.txt  secret.txt.gpg
[sid@sid gpgeg]$
```

> There are 2 ways essentially to encrypt the folder using the gpg either to compress using the tar command or simply compress the folder using the .zip compression using the file manager or zip compresser

> using the tar command

```
[sid@sid gpgeg]$ ls
secret_folder  secret.txt  secret.txt.gpg
[sid@sid gpgeg]$ tar -cf secfolder.tar.gz secret_folder/
[sid@sid gpgeg]$ ls
secfolder.tar.gz  secret_folder  secret.txt  secret.txt.gpg
[sid@sid gpgeg]$
```
> let's encrypt the secfolder.tar.gz

```
[sid@sid gpgeg]$ gpg -c --no-symkey-cache --cipher-algo AES256 secfolder.tar.gz
[sid@sid gpgeg]$ ls
secfolder.tar.gz      secret_folder  secret.txt.gpg
secfolder.tar.gz.gpg  secret.txt
[sid@sid gpgeg]$
```

> similarly we can decrypt the tar folder as well
```
[sid@sid gpgeg]$ sudo rm -r secfolder.tar.gz
[sudo] password for sid:
[sid@sid gpgeg]$ ls
secfolder.tar.gz.gpg  secret_folder  secret.txt  secret.txt.gpg
[sid@sid gpgeg]$ gpg secfolder.tar.gz.gpg
gpg: WARNING: no command supplied.  Trying to guess what you mean ...
gpg: AES256.CFB encrypted data
gpg: encrypted with 1 passphrase
[sid@sid gpgeg]$
```

6. Or simply using the .zip 

```
[sid@sid gpgeg]$ ls
secret_folder  secret_folder.zip  secret.txt
[sid@sid gpgeg]$ gpg -c --no-symkey-cache --cipher-algo AES256 secret_folder.zip
[sid@sid gpgeg]$ ls
secret_folder  secret_folder.zip  secret_folder.zip.gpg  secret.txt
[sid@sid gpgeg]$
```

> to decrypt the .zip folder using GPG

```
[sid@sid gpgeg]$ sudo rm -r secret_folder.zip
[sid@sid gpgeg]$ ls
secret_folder  secret_folder.zip.gpg  secret.txt
[sid@sid gpgeg]$ gpg secret_folder.zip.gpg
gpg: WARNING: no command supplied.  Trying to guess what you mean ...
gpg: AES256.CFB encrypted data
gpg: encrypted with 1 passphrase
[sid@sid gpgeg]$ ls
secret_folder  secret_folder.zip  secret_folder.zip.gpg  secret.txt
[sid@sid gpgeg]$
```

Here, gpg symmetric encrytion is used as it uses passphrase and does not involve any key to be use like asymmetric. This is good for confindentialty but not for integrity.




