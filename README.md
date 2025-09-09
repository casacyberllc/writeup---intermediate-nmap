# writeup---intermediate-nmap
<img width="726" height="194" alt="image" src="https://github.com/user-attachments/assets/e5d55a7c-b460-4af4-9713-25f09383771c" />


## Information given:
- The machine is listening on a high port
- If you connect to the high port, you might be able to give you information
  -  This information can allow you to connect to the lower port commonly used for remote access.

**Tools Needed**
- nmap

<hr />

**Step 1**
We're going to note the IP address and probe what ports are open with nmap. We're going to use `nmap -A -p- <ipaddress>`
Ok it looks like a lot of ways didn't work to see what ports were open. 

The following commands returned nothing:

`sudo nmap -A -p- <ipaddress>`
`sudo nmap -sS <ipaddress>`
`sudo nmap -Pa -sN <ipaddress>`

But the following command showed what ports are open on the server:

`nmap -sV <ip-address>`

<img width="1253" height="336" alt="image" src="https://github.com/user-attachments/assets/bf42389b-4c47-4584-9e99-14622bb17f68" />

I now see port 22, 2222 and 31337 is open. I'm not sure exactly what service is runningon 31337 but if I scroll to the bottom of the output it shows a Linux Kernel, so whatever it is is running on Linux. 

<hr />

**Step 2**

I'm interested to see what is on port 31337. I'm going to use a wget command to see what that returns. 

`wget ipaddress:31337`

I got whatever was returned saved into an index.html file. The following was in the index.html file:

<img width="286" height="87" alt="image" src="https://github.com/user-attachments/assets/41cd9b93-f0d2-40ff-9995-86541edc892a" />

So I have a username and password saved here. 

In case I forget - user:pass
ubuntu:Dafdas!!/str0ng

<hr />

**Step 3**

I have a username and password on here. Let's try to use it to log onto the machine via SSH. 


<img width="682" height="242" alt="image" src="https://github.com/user-attachments/assets/e75884e4-b97e-4dee-a0f9-0ed29a232ae2" />


<hr /> 

**Step 4**

I logged into the system via ssh using the credentials I found. I used `ls` to see if I could see anything but the results didn't show anything. I figured it might just not have anything in the directory I landed on, so I used `pwd` to confirm where I was in the system. I went backwards and changed the directory to the other user on the server. There, I was able to find the flag. 


<img width="687" height="521" alt="image" src="https://github.com/user-attachments/assets/9329574e-3bbe-4651-8ab6-3570a160b382" />














