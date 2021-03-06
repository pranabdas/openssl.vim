# openssl.vim 

#### Installation: 
Check that you have vim plugin folder in your home directory: 
```
ls ~/.vim/plugin
```

If it does not exist, create one: 
```
mkdir -p ~/.vim/plugin
```

Download the openssl.vim to the plugin folder:
```
wget https://raw.githubusercontent.com/pranabdas/openssl.vim/master/plugin/openssl.vim \
-O ~/.vim/plugin/openssl.vim
```

#### Quick start 
Create new or open existing AES encrypted file: 
```
vi my_secret_file.aes
```

#### Things to keep in mind: 

- First save the file without writing any content. The swap file is disabled for
`.aes` filetype, but if the file is not yet saved to the disc and only in the 
buffer, it will still create swap files and save the un-encrypted content to the 
disc. 

- You need to provide the encryption password every time you save the file. Be
careful to use same (intended) password. The program does not check whether 
a new password is used (that is not the same as the one previously used). 
Content cannot be recovered if you do not remember the password you used last 
time to save the file. 

- You may see some characters (for me first two characters of second line) are 
missing when opening a file. Please reload by pressing `Ctrl + L`. 

- MacOS (tested on Big Sur) ships with LibreSSL. This plugin is not working with
LibreSSL. Solution: install OpenSSL via brew `brew install openssl` and add 
following to your `.zshrc`:
```
export PATH="/usr/local/opt/openssl@1.1/bin:$PATH"
```

***

#### Original README

This is a mirror of http://www.vim.org/scripts/script.php?script_id=2012

== Edit OpenSSL encrypted files and turn Vim into a Password Safe! ==

This plugin enables reading and writing of files encrypted using OpenSSL.
The file must have the extension of one of the ciphers used by OpenSSL. For
example:

   .des3 .aes .bf .bfa .idea .cast .rc2 .rc4 .rc5

This will turn off the swap file and .viminfo log. The `openssl` command
line tool must be in the path.

== Install ==

Put this in your plugin directory and Vim will automatically load it:

   ~/.vim/plugin/openssl.vim

You can start by editing an empty unencrypted file. Give it one of the
extensions above. When you write the file you will be asked to give it a new
password.

== Simple Vim Password Safe ==

If you edit any file named '.auth.bfa' (that's the full name, not just the
extension) then this plugin will add folding features and an automatic quit
timeout.

Vim will quit automatically after 5 minutes of no typing activity (unless
the file has been changed).

This plugin will fold on wiki-style headlines in the following format:

    == This is a headline ==

Any notes under the headline will be inside the fold until the next headline
is reached. The SPACE key will toggle a fold open and closed. The q key will
quit Vim. Create the following example file named ~/.auth.des3:

    == Colo server ==

    username: maryjane password: esydpm

    == Office server ==

    username: peter password: 4m4z1ng

Then create this bash alias:

    alias auth='view ~/.auth.des3'

Now you can view your password safe by typing 'auth'. When Vim starts all
the password information will be hidden under the headlines. To view the
password information put the cursor on the headline and press SPACE.

Thanks to Tom Purl for the des3 tip.

I release all copyright claims. This code is in the public domain.
Permission is granted to use, copy modify, distribute, and sell this
software for any purpose. I make no guarantee about the suitability of this
software for any purpose and I am not liable for any damages resulting from
its use. Further, I am under no obligation to maintain or extend this
software. It is provided on an 'as is' basis without any expressed or
implied warranty.

