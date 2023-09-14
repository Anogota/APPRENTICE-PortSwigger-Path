Here i will share the APPRENTICE path from PortSwigger

First we can see Path traversal, there we can see the description for Path traversal:

![obraz](https://github.com/Anogota/APPRENTICE-PortSwigger-Path/assets/143951834/02c2cfb6-bbf6-41bf-ba55-2e38b3adac85)

Reading arbitrary files via path traversal.

Imagine application with cat picture, can clikc in some cat and on ur URL you can see something like this http://cat-picture?filename=cat-with-coke.png
When you check your source code you can see something like this <img src="/loadImage?filename=cat-with-coke.png">

The imagine server can be running on Linux, and this is regular path on linux where saving on image with cat

/var/www/images/cat-with-coke

Now just imagine terminal, and you are into /var/www/images, you on the website and you wanna leave from this path, you can see 3 directory, now like on your terminal do this on website in URL this can be look like this

http://cat-picture?filename=/../../../etc/crontab

This /../ sequence helping me out from this path and see what's on going /etc/crontab
On the Windows this look similar, but if you have some expiernce you know on Windows instead / there is \ this is example URL, how this well be look

http://cat-picture?filename=\..\..\..\Users\Anogota 

Lab:File path traversal, simple case
First what we need to do is turn on burp suite and intercept the traffic
We need to view, some product and in URL can see this parametr GET /product?productId=1

![obraz](https://github.com/Anogota/APPRENTICE-PortSwigger-Path/assets/143951834/c73f7aa3-d19e-4803-a3c6-7fe3112bb183)

If you read cerfuly, this what is write upper, you now know, this paramiter can be vuln, let's test this out.

Or not i test this and nothing, but i have another plan and this will be work for 100%, open the image In the next tab, and we can see there something more intresting /image?filename=30.jpg
there we need to do this and we got:

![obraz](https://github.com/Anogota/APPRENTICE-PortSwigger-Path/assets/143951834/02798a79-b5e5-4271-9242-1e7b7dce98c6)

Contratulations, you solved the lab!

What is access control

![obraz](https://github.com/Anogota/APPRENTICE-PortSwigger-Path/assets/143951834/f3f93b1d-2ec4-45f8-b13e-221dee4c29e3)

Lab: Unprotected admin functionality
This lab is so simply, first what we need to do is go to /robots.txt and there we can see this:

![obraz](https://github.com/Anogota/APPRENTICE-PortSwigger-Path/assets/143951834/ee848358-aee6-4511-8361-fee970b2336f)

Now we need to trafic into this /administrator-panel 
We now, on the administrator-panel without any rights and can delate users, after when you delete the user carlos you can see:

Congratulations, you solved the lab!

Lab: Unprotected admin functionality with unpredictable URL

When we access into this website, check the source code, there we can see something intresting:

![obraz](https://github.com/Anogota/APPRENTICE-PortSwigger-Path/assets/143951834/7188db92-f669-4d6e-a5c8-b225829e0933)

is this a admin panel, let's check this out.
Yep, we are admin, and we can delete ths carlos user

Lab: User role controlled by request parameter

We need to intercept the traffic with burp suite, and if you right way admin=false chance it admin=true, and you can get your admin rights
And go into admin panel and delete carlos

![obraz](https://github.com/Anogota/APPRENTICE-PortSwigger-Path/assets/143951834/3b801475-c427-4ec4-a02c-b62e6916168b)

you need to only change this paramiter from false to true 
