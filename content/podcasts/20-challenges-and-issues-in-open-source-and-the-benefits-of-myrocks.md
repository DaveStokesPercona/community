---
title: "Challenges and Issues in Open Source, and the Benefits of MyRocks - Percona Podcast 20"
description: "The HOSS sits down with Technical Account Manager and long time MySQL DBA Mike Benshoof to talk about the key challenges and issues enterprises are facing today, the benefits of MyRocks, and of course Philadelphia Cheesesteaks!"
short_text: "The HOSS sits down with Technical Account Manager and long time MySQL DBA Mike Benshoof to talk about the key challenges and issues enterprises are facing today, the benefits of MyRocks, and of course Philadelphia Cheesesteaks!"
date: "2021-05-06"
podbean_link: "https://percona.podbean.com/e/the-hoss-talks-foss-_-ep-20-with-mike-benshoof-percona-tam/"
youtube_id: "0kYiGAeZiuE"
speakers:
  - mike_benshoof
aliases:
    - "/podcasts/20/"
url: "/podcasts/20-challenges-and-issues-in-open-source-and-the-benefits-of-myrocks"
---

## Transcript

**Matt Yonkovit:**
I'm here today with Mike Benshoof, my good friend from many, many years ago and our current technical account manager here at Percona. Mike, how are you doing today? 

**Mike Benshoof:**
I am doing great. How are you doing, sir? 

**Matt Yonkovit:**
Great. Now, Mike, we've known each other for what, seven years now? It's been. You've been here seven, eight years, right?

**Mike Benshoof:**
I actually just had the ninth anniversary like two weeks ago. 

**Matt Yonkovit:**
So last year, how did I lose it? I don't I don't understand. 

**Mike Benshoof:**
But they fly by.

**Matt Yonkovit:** 
Yes. So I remember Mike, when he first joined. I hired Mike years and years ago, and he had to come out to my little office in St. John's, Michigan. And so it's in the middle of nowhere Michigan. It really is. There's nothing there. I mean, I don't know if you remember Mike, we sat in that little tiny office that was an old movie theatre.

**Mike Benshoof:**
Oh, yeah. I remember the large plane into Lansing, there were I think myself on the other six people that were on it. 

**Matt Yonkovit:** 
So yes, yes. Yes. Yeah. So it was a good time. Good times. Now. Now. So Mike, you've been here nine years, I apologise for cutting a year or two off your sentence here. You know, and I realised that you have done a lot of different things, you started at Percona, you came from a development background first. Right? 

**Mike Benshoof:**
Right. So I started with PHP development, and then our DBA moved on to different pastures. And our lead developer asked if I wanted to make the switch from the comfortable desk in development down to the pit in the data centre. And so yeah, so from that point on, it was databases all the time. And it was nice, because we got to keep some of the development background in work on kind of automating our tooling, because it was right around the time when the DevOps movement was starting. So that was kind of the goal was to take that development background, understand the app and apply that on the operation side, but it also meant I got to be on call. So that was lovely.

**Matt Yonkovit:** 
Yeah, no, and I mean, like, coming over to Percona, though, you went full in on being a consultant. So your job was to kind of like parachute into these crazy situations all over the place whether it was remote or in person, and help people solve their problems? 

**Mike Benshoof:**
Right. That was a lot. That was a lot of fun, too. 

**Matt Yonkovit:** 
Oh, yeah. I remember because we sat and we were doing performance audits, the first a few months we would go through performance audits, and fix people's stuff together. I mean, it was it was good times.

**Mike Benshoof:**
Yeah, it was and then obviously, from there, that first on call shift, and when we did the on call consulting, and getting to do a data recovery, and all those fun things. That was exciting.

**Matt Yonkovit:**  
Yes, yeah, data recovery, we had to go do lots of little forensic data recovery things look for corruption and, and things like that. But then you kind of continue to evolve from the consulting position, you moved to the technical account manager position, tell us all what technical account manager does.

**Mike Benshoof:**
I don't know, if we have enough time in this podcast to go through, I think the main thing is understanding our client's needs, and kind of translating that to what technically they need, making sure that we're guiding them in the right direction, and making sure that they can really use all of our services. You know, sometimes I get to put the technical hat on from time to time. But a lot of it really is hey, share with me your ideas, where are you going, let's make sure that you're on the right path, so that you guys don't spend six months of work, and then find out that you chose the wrong solution, and then start from scratch again. 

**Matt Yonkovit:** 
It's really like, not only an advisor who can sit down and tell you based on what they understand about your environment, like what the best course of action is. But it's also someone who acts as kind of a database, high level database architect who's recommending the technologies and recommending hey, this is how other people solve this problem. Here's what we've done in the past, here's what you should consider.

**Mike Benshoof:**
Right? And I do get asked that a lot like, Hey, what are your other clients that are scaled doing and then you know, sharing? Okay, I saw a client that was doing this and that kind of fit your use case, maybe it's something we can look at. And so yeah, there's definitely a lot and a lot of the questions I get are, what are you seeing others in the industry do? Or we're going to try this? Do you think it's a bad idea before we even get started? Those are the general kind of questions that will get discussions going. And then we go from there. 

**Matt Yonkovit:** 
Okay, so if I put you on the spot now, so okay, let's see Mike sweat. He's sweating now.

**Mike Benshoof:**
I just said it's cold even though it we had record low temperatures today. 

**Matt Yonkovit:** 
Oh, yes. We have a Freeze Warning today. So it's really warm out here. And in fact, my office right now where I'm recording this is super hot. I was actually checking the air before here, but don't distract me. ask you this important question. You know, so you mentioned like people want to know what you're seeing, what other people are seeing, what other people are doing? Is this a dumb idea? So tell us, what are you seeing? Like, what are the things that you're seeing come up more and more now being that now, you're working for what is it like four or five different large enterprises on a regular basis, you're seeing the internal workings. And I'm not asking for names of specific customers or users. But like, what are those trends that are really, you know, impacting them?

**Mike Benshoof:**
I'd say the two biggest things that we're seeing now are around space, and virtualization and automation. Everyone is obviously, there's a lot of data. And that's not a new problem. But a lot of enterprises have made the switch into open source databases. You know, a lot of people will start with something like MySQL, because it's kind of easy to jump into, and all of a sudden, their data explodes. And now we're looking at how do we re architect so really dealing with dealing with space, and then also giving developers access, right, so a lot of a lot of clients are working on kind of internal clouds or allowing, empowering their developers to do faster work, right? They're not, they're not racking servers anymore. And doing that kind of dance that we used to do as DBAs, it is much more managing an infrastructure with the ability for people to spin up databases, right? Most of my clients, when they open tickets with me or start discussions, are saying, hey, my clients need this. And those are application teams that are within their enterprise that are dealing with the operations, guys.

**Matt Yonkovit:** 
So there's two things there. Number one, just to clarify, when you're talking space, you're not talking about space, the final frontier out in outer space, you're talking about disk space, you're talking about storage, you're talking about the size of these environments, right? Because everybody wants more data. And so how do you manage that data at scale, just to clarify, for those who are listening or watching, you know what you mean by that. But what's interesting is you're talking about people building their own clouds, why build their own, why not use the public cloud?

**Mike Benshoof:**
Security, everyone wants to keep everything in house, they don't want to deal with that. Now, some are doing hybrids, right, they're making their own internal cloud, but then having kind of a backup off-site, DR in a public cloud, but a lot of them, but they also already have all the equipment on hand, right? They've built data centres out, but they want to just use it in a more efficient way. So making it as an internal cloud where they can then you know, a client or developer comes in says, Hey, we're working on a project, we need a database, boom, here's your cluster, it's not I need to go buy some servers, or we need to put this up in a public cloud, because then if they start their development there, and it takes off, then they're looking at migrating it back in house and that type of things, everyone wants to keep things in house as much as they can. And really, just with the agility, right, that people are making new things and the speed the development works, being able to quickly launch that is important.

**Matt Yonkovit:** 
So they want the cloud experience. Without the cloud negatives, like they want to, they want to retain control, they want to own this. They want to make sure that they can control their own destiny. I know some of them, for instance especially when you talk about retailers, retailers just don't like to work with Amazon because they view them as competition. You know, and so if they do use the cloud, they typically go Google or Microsoft, and try to avoid AWS. So it just depends on the industry as well. But so what you're saying is, you're seeing quite a few of these companies, they're, hey, we love enabling our developers, we want that speed, we want all that cloud experience, we just want it on prem, or in a hybrid environment. We want to control where we run it when we run it, how we run it.

**Mike Benshoof:**
Yep. And again, there are cases where someone just says I'm all in public cloud and do it and they take the time, because you can architect security into that, like, it's not something it's not not it's, it's something that can be achieved, right. But it takes extra thought and extra planning and extra comfort level. And some of them when they already have the infrastructure in place. And it's just putting a virtualization layer on top of what they already have. It's easier because they already have all the in house security built and everything and they don't have to learn how to do you know, security, right with you look at all these clouds, they have this shared model of we're going to secure the infrastructure, but you're going to secure what you do within our infrastructure, right? So you have that piece that's an extra layer where all that's already controlled when you have everything in on prem. So it's definitely something you can achieve, it just an extra layer that has to be applied.

**Matt Yonkovit:** 
Okay. Okay. Well, here's another question that I'm really curious about . You work with a lot of companies, and you hear a lot of the same thing over and over again, probably. And this is your opportunity to let people know maybe that most common mistake that just drives you nuts, you just wish it would be solved. Because you know, we do have quite a large audience. We're number one in Tunisia. My podcast is number one in Egypt for the tech space. We're also number two in Madagascar. So we've got quite the reach. So what is that thing that you keep on seeing companies make the same mistake over and over again, and you just wish they would stop?

**Mike Benshoof:**
Using the wrong tool for the round peg square hole syndrome, right? Where we've made an investment into x technology. So we're using that technology, a use case comes in that doesn't quite fit it. And so then we just fight with, it's not a good fit, and we continue to play with it is not a good fit. And understandably, right, you don't necessarily want to always spin up new technologies. But that's the beauty of these open source databases, right? They're different. They're designed for different use cases, and there's no one size fits all. But there's generally a size that really fits what you need. And because enterprises, it's not a trivial thing, right? If I say, hey, just use this technology, well, that's like a two year project to get that spun up, or it's like, well, we already have this infrastructure in place. So let's continue to use that. And then sometimes, if it's the wrong use case, it's just pain from that point on. And so I think that's one that being willing to do that and have access to those other database options, that would be a good thing. I think that's probably the biggest one that I save..

**Matt Yonkovit:** 
Okay. And so speaking of like hey, choosing the right tool, you just wrote a blog just came out on the percona blog, on using MyRocks, and some of the use cases on MyRocks. Now, RocksDB is a technology that is built into the Percona Server for MySQL, RocksDB is also popular amongst many other database applications. It's used in multiple applications elsewhere, can you tell us a little bit about RocksDB, MyRocks, and that overall technology.

**Mike Benshoof:**
So I think the biggest difference is when we talk about databases and transactional databases, we were always thinking the default go to is the B-tree, right. And so that's a structure that's well known. It's a very high performance system. But rights, and a lot of large rights are generally known as one of the problems, right, if I have an application that I'm doing a lot of bulk loading, or, and I'm not doing kind of transactional stuff, but I'm just storing a lot of data. B-trees are not the most efficient, right. And so when we look at My Rocks, MyRocks is still kind of that key value. key value storage, right, and it's using LSM trees as opposed to B-trees. So they're kind of designed more to push a lot of that actual disk writing down into the background, right. And so you're able to get data loaded faster. And when we think about that, right, that's all those two issues where we see it and the use case of I want to load a lot of data. And the key word being a lot of data. Normally your performance would be a hit and a trend, traditional B-tree. But then you also have all the space, right? And so what this LSM tree, which you know, RocksDB is trying to do is trying to minimise that space. So it's trying to give you a better, a better space footprint, and also better performance. So when we're talking about these large data's where we kind of write stuff and write it once and we're not going back and updating it a lot. Sometimes that can be a much better fit. And then you're also ending up with a smaller disk footprint overall.

**Matt Yonkovit:** 
Okay, and you're going to be giving a overview of this at Percona Live, coming up shortly, right, you're gonna have kind of a one on one session on MyRocks.

**Mike Benshoof:**
Yes. So the goal with that is really not to dive into the internals. You know, we have people that know a lot more about it than I do. But really, as the buzz starts around these types of storage engines, we want to make sure that people it's not, it's not just viewed as a Oh, this is in InnoDB plus one, it's just better than in InnoDB. They're, they're different, right? And so what we're trying to do is talk about where it might be a good fit. And and some of the pros and cons, right really just kind of talked about it at that high level, we don't want to go in and we're not trying to break down the efficiency of merge sorts and looking at all that and we're not going to be talking algorithm analysis, but just does it make sense to even look at it from my business, right? Is that something that might fit and be worth looking at?

**Matt Yonkovit:**   
Okay, and so let me ask you the important question. Which cheesesteaks place?

**Mike Benshoof:**
Oh, it's, it's Pat’s 100%. So, I'm a provolone without guy. Okay. That's my background. I tried Geno's once, and I was unable to actually finish it. And then I walked across the street to Pat's because I just I don't know, it was something I just didn't sit well with me.

**Matt Yonkovit:**  
So for those who are not from the US and don't understand cheesesteak culture, okay, so, Mike and myself share a passion for cheesesteaks and things in the Pennsylvania area. I live in Pennsylvania for a few years. He is from Pennsylvania. He's an Eagles fan. I don't hold it against him. I'm a Browns fan. Yeah. But cheesesteak culture in Pennsylvania is very important. And there are two cheesesteak rival companies that are across the street from one another. And there is this great divide . It is probably a deeper divide than Republicans and Democrats in the US. It's a deeper divide than, you know, like it's you know, proprietary versus open source. It's Pat’s or patently Geno's, it's a big thing.

**Mike Benshoof:**
And when we talk about with or without cheese steak with his with Cheez Whiz, with or without,
well, that's going to be Well, technically, with or without, it's for the onions. So you specify your cheese type. And so like a Wрiz wit would be how I would like Cheez Whiz. 

**Matt Yonkovit:**   
Yeah. So, the most important thing that came out of this talk now, the Philadelphia cheesesteak knowledge. But it's good to talk to you, Mike. It's good to catch up. We look forward to hearing your session at Percona Live. Thanks for stopping in and tell us a little bit about what you're working on and about MyRocks. Sure.

**Mike Benshoof:**
Absolutely. A pleasure as always, and yeah, have a good rest of your day. All right.

**Matt Yonkovit:** 
Wow, what a great episode that was. We really appreciate you coming and checking it out. We hope that you love open source as much as we do. If you liked this video, go ahead and subscribe to us on the YouTube channel. Follow us on Facebook, Twitter, Instagram and LinkedIn. And of course tune in to next week's episode. We really appreciate you coming and talking open source with us.

Transcribed by https://otter.ai


 