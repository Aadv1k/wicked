Title=Email platforms are terrible, so I built my own
Date=2023-05-14
Order=3

as a developer Email is notoriously hard to work with, if you manage navigate through the ever changing maze of complex UI, you will then have to deal with similar issues when trying to integrate it into your app. The issue emboldens when you just want to send a quick email and don't want to set up the infrastructure yourself.

### Because email is hard

EMail is something that has turned into a highly centralized consortium where your email will likely never see the face of the primary inbox, this makes sense since email spam is very common, it's funny how most of the spam is usually sent by major outlets such as news sites and/or google with their persistent updates, email has turned into a messy subject. Users want to spend less and less time dealing with the much dreaded "10K" emails they have yet to manage and corporation who still keep spamming your inbox with the email you gave them a decade ago. I have an experience with the first hand, building my own newslettere [Cybernated](https://github.com/aadv1k/cybernated) what the first instance of when I had to deal with this subject, I soon learn there there were **no** solutions that fit the following bill

- Cheap (and free), likely no more than a 100 emails a day
- Simple; I am not a email marketer or own some kind of modern recipe blog that I have to send campaings 
- Developer-centric: I do not give a fuck about a contact list, all I need to do is send email in a predictable manner

So my solution with this was to simply send emails via a centralized inbox, literally just control the SMPT server programatically, following this I thought that well I I can control this, why can't every user control a centralized inbox? There are potential issues such as spam, rate-limiting etc But if we can get through that we gucci? Yes. 

### ZapMail: a simple solution for a simple problem

So I decided to just that, I setup an express app, hooked up some routes and created a parameter that uses [nodemailer](https://nodemailer.com/about/) to send mails via a quick burner outlook account I set up. Now if you think about this for more than a second you can see how this app may crash and burn as soon as it is exposed to the web, For that I decided to implement rate limiting with a timer of 20 seconds, this will deter most scammers, and for the highly persistent once, we cap their daily senidng limit to 200. The worst case scenario in this case, is that the outlook account will get blocked by microsoft, from my research there isn't exactly a cap on this, but time will tell. 

For now, I will personally be using [ZapMail](https://github.com/aadv1k/zapmail) in my future projects, because of it's simplicity. Feel free to give it a go and maybe break it.
