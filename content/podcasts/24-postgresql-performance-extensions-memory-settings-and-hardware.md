---
title: "PostgreSQL Performance Extensions, Memory Settings, and Hardware - Percona Podcast 24"
description: "Matt and Ibrar talk about the impact of 3rd party extensions, memory settings, and hardware."
short_text: "The Percona HOSS Matt Yonkovit sits down with Ibrar Ahmed, Senior Software Engineer, at Percona to talk about PostgreSQL Performance! Matt and Ibrar talk about the impact of 3rd party extensions, memory settings, and hardware. Get a bit more detail behind Ibrar’s talk he delivered at Percona Live 2021. The full recording of his Percona Live session entitled: “High-Performance PostgreSQL” is now available."
date: "2021-06-17"
podbean_link: "https://percona.podbean.com/e/the-hoss-talks-foss-_-ep-24-with-ibrar-ahmed-senior-software-engineer-percona/"
youtube_id: "jCKnETLljK0"
speakers:
  - ibrar_ahmed
aliases:
    - "/podcasts/24/"
url: "/podcasts/24-postgresql-performance-extensions-memory-settings-and-hardware"
---

## Transcript

**Matt Yonkovit:**
Hi, everybody! Matt Yonkovit, the “HOSS Talks FOSS” is back with another exciting episode today we're here with Ibrar. And I have my Postgres hat on just to talk about Postgres. Ibrar, how are you doing today? 

**Ibrar Ahmed:**
Yeah, I'm fine. What about you?

**Matt Yonkovit:** 
I'm good as well. I do have an elephant on my head. So it is a little weird. And it is a heavy elephant too, which is kind of...

**Ibrar Ahmed:**
It is not weird, it looks cool.

**Matt Yonkovit:** 
Yeah, I think it does. This does have a distinctive look. But appreciate you coming on today. If you haven't heard any of the Ibrar’s talks before, he has talked several times at several different conferences, including Percona Lives, but also Postgres Vision, the regular Postgres conference circuit tour. He is February's blogger of the month, which he got an awesome hat that I designed for him. So I'm very excited about those types of things as well. But even though you've been in this Postgres space for a long time, you are the resident expert on all things Postgres here at Percona. And we're really excited to talk to you about some of the things you already talked about at Percona Live. So if you want to catch Ibrar’s talks, they are on YouTube right now, so you can go check them out. 

But why don't we talk a little bit about his talks around high performance, Postgres and querying other databases, outside of Postgres, so, two exciting topics. But figured we'd start with the performance, because, let's be honest, who doesn't like a charging elephant? Right? That's always good. Right? The faster the elephant charges, the better it is. Or maybe not? I don't know. But I think that you had a great talk, I was able to catch most of it. And, you know, maybe tell us just a little bit about what you have done over the years to kind of come up with all that Postgres awesome knowledge around performance and making Postgres kind of home. This is many different war stories in one, right, it's taken a long time to get to where you are. 

**Ibrar Ahmed:**
I have been in the software industry since 1999. And for my Postgres journey starts in 2006, when I joined EnterpriseDB as associate architect, and then software architect and senior software architect, and now I'm in Percona three years back, so three years now in percona. So I have, I think, 15 years now, in PostgreSQL now. 

**Matt Yonkovit:** 
Yeah, you have as much time in the Postgres world as I have in the MySQL world. So congratulations. As old school database folks, we have to stick together. Now, what I found really interesting is a lot of the same things that I know for the MySQL space, apply to Postgres as well. And it seems like many of the same Postgres DBAs out there trying the same tricks. You mentioned in your talk that you can always add more hardware as one of the solutions that people pick. But that's not the best solution, isn't it? 

**Ibrar Ahmed:**
It's not the best, obviously, because it costs you money.

**Matt Yonkovit:** 
It does, especially in the cloud space, right? Because now it's just more money, swipe your credit card and go to the next biggest instance size, this Postgres scale well with hardware, though. So as you add more hardware, is there a point where Postgres just tends to not do as well? I mean, is there a limit to how much you can add or?

**Ibrar Ahmed:** 
No, as far as I know, there is no limit to that. But look after your PostgreSQL to match the hardware to,

**Matt Yonkovit:** 
Right. And so you have to tune and configure. So it's not just adding more memory and everything just works? No, you have to go in and you have to adjust and tune the parameters and things. 

**Ibrar Ahmed:** 
Yeah, absolutely. Because PostgreSQL is designed by default to work on the low minimum hardware, if you just install it, it will start working. If you have more hardware, then you have to tune your database to use the hardware.

**Matt Yonkovit:** 
Okay. And so that vertical scalability in systems is there, but you have to know what you're doing. And there's a lot of what your talks are about is the three different areas that you can look at, which is obviously, the database engine, and tuning the configuration and tuning the database itself. But then also tuning the application to fix the code and to adjust the code to be more performant and also tuning those queries. Now, obviously, you've got the OS side, but I'm going to leave that out because that's a whole another discussion in and of itself.

So when you see that you've got these options, when you've got the different nodes, you can turn, you can tune the configuration, you can adjust your application, you can tune the queries individually, do you really have to do all three? Or is there one that's more important than the others?

**Ibrar Ahmed:** 
The most important is the database. This is a much bigger tune, because there are multiple applications, maybe you have multiple applications correct for that with that database. So if your database is not properly tuned, all the applications will not work properly. But if your database is tuned perfectly, maybe one application, which is not properly tuned, will not work perfectly. But some applications which are tuned in for, quite frankly, that database. So database tuning is the main thing, then it comes to the application, and then its security and all of the stuff. 

**Matt Yonkovit:** 
Okay. And so really that configuration, setting up the database properly, ensuring that your hardware and your database systems match - that's the foundation for anything, and it is the first thing you have to do. That's what you're saying.

**Ibrar Ahmed:** 
Yes.

**Matt Yonkovit:** 
Okay. And one of the differences I know between Postgres and MySQL is the model of processes versus threads. And this is something that you do talk about, because a lot of the tuning that you can do is even down to the per process, so you can tune the session variables for a lot of different memory configurations, individually as you open up sessions. Now, because you're spawning off a new process for every client, is there a risk that… Maybe you're going to the larger concurrency, you might have more memory usage? And it might consume more than is needed? And might you have to look at something like connection pooling externally to try and reduce that work, memory footprint? 

**Ibrar Ahmed:** 
Yes, actually, it all depends on your hardware also. I|f you have too connection that there is a some stage that you weren't able to connect to the more connection to that server, so you need connection pooler. Because sometimes you need to think about your active users. So you need to have some kind of a pooler and PgBouncer is the one of the best poolers available. So you have to put the bouncer and then you can use the database. But if you have not a very big connection then don't use the pg pooler, you can directly use the database. But if you have a large number of connections, then I think PgBouncer is the one of the best solutions. 


**Matt Yonkovit:** 
Okay, and this is where Postgres has this wonderful extension ecosystem, it has wonderful tools and different things around it. Some of the extensions plug in, some of them set externally, and with some of the extensions (a lot of people have their favorite extensions that they like whether it's for a purpose like Postgres or other applications) is there any risk when you add additional extensions that the core database slows down? So, as you build out your application, you might start with just a very basic install, but then you start adding extensions on,
maybe to test, maybe to do different things, is there a risk that those could potentially slow things down?

**Ibrar Ahmed:** 
And, yes, actually, you need to trust some trusted extensions, because if you start installing the extension from a third party, and you have to look at who is building that, who is behind that, if somebody is you don't know about that and that extension is not well known extension, then there is a risk, even your database can crash.

**Matt Yonkovit:** 
Okay. So you got to be careful, because there's like several 1000 different extensions available on GitHub, probably even more. And if you don't know where they are, they can introduce performance issues, stability issues and other issues in your database. 

**Ibrar Ahmed:** 
So you have to be very careful because people don't use a third party extension, which is not written by well known people. When the social and well known company behind that, which is supporting that, so it's called it is well-written and well documented, and it's worked perfectly for them, they start using that. Otherwise, it's a risk.

**Matt Yonkovit:** 
So is this why cloud providers don't do many extensions at all? Like they don't allow you to add your own in a lot of cases. 

**Ibrar Ahmed:** 
I told you that it a risk. Sometimes if an extension is PostGIS and something like that, so you don't have to worry about that because it's a well known extension, so you don't have to worry to install PostGIS, or something like that. So, but if you are talking about some extension, which is not well known, it can cause performance issues, it can cause you the stability issue.

**Matt Yonkovit:**  
Okay. And as you start to look at those extension ecosystems and what's out there... What's maybe one of those extensions are one of those things that you really find interesting that maybe most people don't know about, is there like one that you're like “Ooh, this is really interesting. You know, I think more people should look at this”.

**Ibrar Ahmed:** 
Yeah, I really like the fdw concept. And there are several foreign data wrappers available. And you know that I am the author of three or four foreign data wrappers. So, one, the first one, I started that MySQL one, the MongoDB, the Clickhouse. Clickhouse is the Percona one.

**Matt Yonkovit:**
Okay. And those give you access to databases that are external. Excellent. Right. And so what is the downside of doing that sort of connection? Are there gotchas or things you need to watch out for? So, you try and connect to, let's say, an external MySQL or Mongo, it's not quite the same as having the data directly there. So are there things or tips or tricks that people should do in order to get better performance when they're trying to access that external information? 


**Ibrar Ahmed:**
Yeah, actually, the foreign data wrapper provides a really good interface. Translate everything you need. Like, you can also set the parameter for the MySQL side. So you can set the parameter there. So lifetime one, you have to set same timezone setting on both of them. So I did that in MySQL. So you can do that. It's very powerful tool now.

**Matt Yonkovit:**
Okay, great. Great. Well, back to performance again, because I'm a performance person. You know, one of the surprising things that I learned during your session was the recommendation for the shared buffers is only 25% of your total memory. I know like in MySQL space it's like 75 to 80%. And so the shared buffers being only 25%.. I know that you had some thoughts on that as a default, or what people recommend that it's too low. Tell us a little bit about that. 


**Ibrar Ahmed:**
Yeah, it's not default, default is very low and when you're talking about 24, or 25%, is just a documentation. Because it was documented at that time when we have a database and have an application server on the same system. So when you have an application server, and some other stuff, and database on the same system, then you cannot give a 70% to the database. So, application server or something else need memory. So that's why the percent 25% is the good one. But I'm talking about when you have a dedicated database, so why not give the maximum you can give to the database. Because usually, now a database is a standalone system nowadays. You can give 50% 70%, so you can get a really good performance. But keep in mind, you have to think about your workload. If your workload is just 30% of your total RAM, so while you are giving 70% or 60%, 30% is enough for that, because there is no advantage of getting more to the database.

**Matt Yonkovit:**
Yeah, no. And I mean, that makes sense. Because, honestly, nowadays, you're right, no one's running this shared setup, unless it's like a test environment. Because everybody's using, whether it's virtualization, or Docker or something else, they have a little bit of flexibility to segregate that out. So typically, if you are running on a virtual machine or you're going to share a physical hardware, you're still going to have a dedicated amount of memory allocated to it. So it's very rare that I see in production, you have a full stack running on a single box anymore. 

**Ibrar Ahmed:**
Yes, not nowadays. But before people were doing that.

**Matt Yonkovit:**
Okay. And I know that during your talk you walk through about a dozen different variables that people should consider and set and think about and you do show some of those performance implications versus one over the other. But really, the shared buffer was the one that you called out as the most important one. Is there another one that you would say, if you're going to only set two things, you're only gonna look at two things, look at the shared buffers and look at this other one? 

**Ibrar Ahmed:**
Yeah, the main is the shared buffer, because the other are some dedicated one, like the maintenance workman. They are all for the specific purpose, but shared buffer is the common one. If you do that, you'll have to turn your database for the as a memory concept, you own your shared buffer first.

**Matt Yonkovit:**
So, Postgres has a lot of interesting ways to adjust and tune memory. And the specific workloads, there's so many interesting different configuration variables. If you're going to sort a lot of data, set these things. If you're going to do more OLAP type things, consider these. There's a lot of those things. And so, I would really encourage everyone to maybe take a look at your session. It's an hour, it's on YouTube, it's out there for people to get a deeper dive.
But one of the questions that I often come up with, and this is something that I hear from other people, when they talk about scalability. Right now, we're in this space where people want easy scalability. So either they're going to add a whole bunch of hardware until they can't, or they're going to look for that clustered solution, they're going to scale out. And that's an area where Postgres... There really isn't a de facto standard for a cluster. Now, while there is replication and things, where is the cluster? I know that there's some different companies that have done some things, but in your opinion, is that an area that you think is going to grow and you're going to see more working? 

**Ibrar Ahmed:**
Yeah, absolutely. You're right. When we're talking about the clustering, that we have a different type oof replication, the logical application, the streaming application, so we have that options. But when we are talking about the whole cluster management, Postgres is lagging. Even if you're talking about the multi primary replications there is no option for in PostgreSQL. The different companies have their own dedicated solutions like EnterpriseDB have their own solution.. So in the community, there is no what is going on. So, I think there is a potential to work in that area. So there is a one solution that's available that is a PostgreSQL XL actually. But it's not, in my opinion, a production ready solution, but it's open source, but not production ready solution. So there is a potential in that area.

**Matt Yonkovit:**
Okay, great. So thanks for  taking some time out today to chat with me. I really would love if people check out your your talks. Like I said, there's an hour deep dive talk and how to tune and optimize your PostgreSQL environment out there right now for free. You can go watch it. It's great. There's also a wonderful talk specifically on those data foreign wrappers that you can access other databases from Postgres. And so if you want to know the ins and outs of that, that's something that's really exciting as well. Ibrar, thank you for joining us. Appreciate the time today. 


Wow, what a great episode that was. We really appreciate you coming and checking it out. We hope that you love open source as much as we do. If you liked this video, go ahead and subscribe to us on the YouTube channel. Follow us on Facebook, Twitter, Instagram and LinkedIn. And of course, tune into next week's episode. We really appreciate you coming and talking open source with us.
