# Level 0 ==> Level 10

---
> after every ssh you have to exit and again ssh into the next level
---

## Level 0

### The Goal:
The goal of this level is for you to log into the game using SSH. The host to which you need to connect is `bandit.labs.overthewire.org`, on port `2220`. The username is `bandit0` and the password is `bandit0`. Once logged in, go to the Level 1 page to find out how to beat Level 1.

### Commands we use:  
ssh

### Solution:  
```bash
> ssh bandit0@bandit.labs.overthewire.org -p 2220
```
> Password: bandit0

<img width="860" height="547" alt="image" src="https://github.com/user-attachments/assets/b0d0f864-ae93-48a1-a0ec-5825f8666533" />


---

## Level 0 - Level 1

### The Goal:
The password for the next level is stored in a file called `readme` located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

### Commands we use:  
ls , cd , cat , file , du , find

### Solution:  
```bash
> ssh bandit0@bandit.labs.overthewire.org -p 2220
> Password: bandit0  
> ls
> cat readme
```

<img width="860" height="547" alt="image" src="https://github.com/user-attachments/assets/d2828e49-b4fa-49ce-b1d3-bfe7d33acf7d" />

---

## Level 1 - Level 2

### The Goal:
The password for the next level is stored in a file called `-` located in the home directory

### Commands we use:  
ls , cd , cat , file , du , find

### Solution:  
```bash
> ssh bandit1@bandit.labs.overthewire.org -p 2220
> Password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
> ls
> cat ./-
```

<img width="860" height="547" alt="image" src="https://github.com/user-attachments/assets/58d75030-c6d9-444c-9de1-1fe8f314097f" />

---

## Level 2 - Level 3

### The Goal:
The password for the next level is stored in a file called `--spaces in this filename--` located in the home directory

### Commands we use:  
ls , cd , cat , file , du , find

### Solution:  
```bash
> ssh bandit2@bandit.labs.overthewire.org -p 2220
> Password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
> ls
> cat ./--spaces\ in\ this\ filename--
```

<img width="860" height="547" alt="image" src="https://github.com/user-attachments/assets/2a8f5cef-678a-47f2-8055-361b3beeb94f" />

---

## Level 3 - Level 4

### The Goal:
The password for the next level is stored in a `hidden file` in the `inhere` directory.

### Commands we use:  
ls , cd , cat , file , du , find

### Solution:  
```bash
> ssh bandit3@bandit.labs.overthewire.org -p 2220
> Password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
> ls
> cd inhere/
> ls -lah
> cat ...Hiding-From-You
```
<img width="860" height="547" alt="image" src="https://github.com/user-attachments/assets/16527bce-7593-4458-accd-8220f84bcda0" />


---

## Level 4 - Level 5

### The Goal:
The password for the next level is stored in the only `human-readable file` in the `inhere` directory. Tip: if your terminal is messed up, try the “reset” command.

### Commands we use:  
ls , cd , cat , file , du , find

### Solution:  
```bash
> ssh bandit4@bandit.labs.overthewire.org -p 2220
> Password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
> ls
> cd inhere/
> ls
> file ./*
> cat ./-file07
```
<img width="860" height="547" alt="image" src="https://github.com/user-attachments/assets/d6308588-71a9-4de2-9d49-4fef05f2d557" />

---

## Level 5 - Level 6

### The Goal:
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

`human-readable`  
`1033 bytes in size`  
`not executable`  

### Commands we use:  
ls , cd , cat , file , du , find

### Solution:  
```bash
> ssh bandit5@bandit.labs.overthewire.org -p 2220
> Password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
> ls
> cd inhere/
> ls
> find . -type f -size 1033c -not -executable
> cat ./maybehere07/.file2
```
<img width="860" height="547" alt="image" src="https://github.com/user-attachments/assets/faec3b2b-9463-44e8-a78c-66765e4f4d20" />

---

## Level 6 - Level 7

### The Goal:
The password for the next level is stored somewhere on the server and has all of the following properties:

`owned by user bandit7`  
`owned by group bandit6`  
`33 bytes in size`  

### Commands we use:  
ls , cd , cat , file , du , find , grep

### Solution:  
```bash
> ssh bandit6@bandit.labs.overthewire.org -p 2220
> Password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
> find / -type f -user bandit7 -group bandit6 -size 33c
> cat /var/lib/dpkg/info/bandit7.password
```
<img width="921" height="731" alt="image" src="https://github.com/user-attachments/assets/f0e6dc2e-ca7f-444c-8287-8549ca437944" />
<img width="921" height="579" alt="image" src="https://github.com/user-attachments/assets/2112197b-4539-4822-84a2-04eb253cc90f" />


---

## Level 7 - Level 8

### The Goal:
The password for the next level is stored in the file `data.txt` next to the word `millionth`

### Commands we use:  
man, grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

### Solution:  
```bash
> ssh bandit7@bandit.labs.overthewire.org -p 2220
> Password: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
> ls
> grep millionth data.txt
```
<img width="920" height="579" alt="image" src="https://github.com/user-attachments/assets/4043b950-cc43-4a8e-8c2a-f59c8adc1127" />


---

## Level 8 - Level 9

### The Goal:
The password for the next level is stored in the file `data.txt` and is the only line of text that occurs only once

### Commands we use:  
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

### Solution:  
```bash
> ssh bandit8@bandit.labs.overthewire.org -p 2220
> Password: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
> ls
> cat data.txt | sort | uniq -u
```
<img width="920" height="579" alt="image" src="https://github.com/user-attachments/assets/2548f5f7-40b2-4e78-a73a-dbf160f321be" />

---

## Level 9 - Level 10

### The Goal:
The password for the next level is stored in the file `data.txt` in one of the few human-readable strings, preceded by several `=` characters.

### Commands we use:  
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

### Solution:  
```bash
> ssh bandit9@bandit.labs.overthewire.org -p 2220
> Password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
> ls
> cat data.txt | strings -e s | grep ==
```
<img width="920" height="579" alt="image" src="https://github.com/user-attachments/assets/3ec0feed-da79-4a77-9dea-b786a823bc52" />

---

## Level 10 - Level 11

### The Goal:
The password for the next level is stored in the file `data.txt`, which contains `base64 encoded data`

### Commands we use:  
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

### Solution 1:  
```bash
> ssh bandit10@bandit.labs.overthewire.org -p 2220
> Password: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
> ls
> cat data.txt
```
- Head over to <a href="https://gchq.github.io/CyberChef/" target="_blank">here</a> and drag in `From Base64` into the `Recipe` section and paste the content of `data.txt` into `Input`
  
<img width="920" height="579" alt="image" src="https://github.com/user-attachments/assets/88bc690d-288f-410f-bb5b-67cb9590194a" />
<img width="961" height="964" alt="image" src="https://github.com/user-attachments/assets/e2d13731-fcd5-49c8-a948-1c0c5f87ee2f" />

### Solution 2:  
```bash
> ssh bandit10@bandit.labs.overthewire.org -p 2220
> Password: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
> ls
> cat data.txt | base64 -d
```
<img width="920" height="588" alt="image" src="https://github.com/user-attachments/assets/2d9fd910-a236-4589-b160-2682ce74cbb9" />

---

### License / Author
Author: <a href="https://github.com/cookiesn1ffer" target="_blank">cookiesn1ffer</a>   
License: MIT — see root `LICENSE` file.
