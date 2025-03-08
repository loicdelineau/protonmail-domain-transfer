# Protonmail Domain Transfer
If you are currently using a domain (TLD or ccTLD) on your protonmail
account and you would like to swap it to another protonmail account with
a different subscription plan, this repo is for you.

This repo filters all emails that came (or left) from one specific domain
and all email addresses associated to it from the rest of your personal emails.   
Here is exactly how it works:

1. Backups all your emails locally
2. Renames that directory to all/
3. Asks you for the domain name
4. Make a new directory with that domain name
5. Filters all emails associated to that domain name
6. Restores that filtered directory to your new account

## STEP 0 - Prerequisites
This repo is designed for a Linux system running Ubuntu with a BASH shell.

- Tried and tested on Ubuntu 24.04
- Should work for all other versions of Ubuntu
- Might work for Debian based systems 
- Could work for other Linux systems
- Won't work on Windows or MacOS

Clone this repo:
```
git clone https://github.com/loicdelineau/protonmail-domain-transfer.git
```

Navigate to it:
```
cd protonmail-domain-transfer
```

## STEP 1 - (B)ackup Using Protonmail's Script
Start by backing up your emails from your previous mailbox onto your device. 

We will use Protonmail's CLI script for this, as it is GNUv3, I have included it
inside of this repo but if anything is broken, you can find it
[on their website.](https://proton.me/support/proton-mail-export-tool)

Run it with:
```
./protonmail-cli
```

Enter your **old** protonmail account email address and password. 

```
>> Username: my-protonmail-email@proton.me
>> Password:     (type it in blind)
```
Enter B for (B)ackup:
```
B
```

Let the script do it's job, it will take awhile. 


## STEP 2 - Setup Directory
You will now have to rename the folder Protonmail's script has created:

```
# Make sure to change this to your own email address!!
mv my-protonmail-email@proton.me all 
```

You have now renamed the file with all your emails to all/. 

## STEP 3 - Run Migrate Script
This script will:

1. Prompt your for the name of your domain you would like to migrate
2. Make a new directory with that domain name
3. Copy all emails that have this domain name inside of them to the new directory

```
./migrate
```

Enter your domain name and enjoy!

## STEP 4 - (R)estore Using Protonmail's Script
Now you have a fresh repo full of the emails with that domain, you can
restore them into your new protonmail account, we will use Protonmail's script
again for this. 

Run it with:
```
./protonmail-cli
```

Enter your **new** protonmail account email address and password. 

```
>> Username: my-new-protonmail-email@proton.me
>> Password:     (type it in blind)
```
Enter R for (R)estore:
```
R
```

Give the path to the sorted directory (printed in the previous step). 
```
...
```



