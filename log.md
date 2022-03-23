### 2022-03-22
- Again, did a number of modules on MSLearn for the AI-900 cert. I have about 7 modules left now.

### 2022-03-21
- Did a couple of modules on the AI-900 Azure AI fundamentals path. Tonight it was Computer Vision.
- Also signed up for an AI-900 virtual learning for April 7. Not sure how I'll pull it off though because it is at 3am EST!

### 2022-03-18 to 2022-03-20
- So I took a break on Friday, for the most part.
- Saturday and Sunday were somewhat lazy but I worked through some Kubernetes training.
- Found a couple of really great resources for interactive K8s courses. Listed them on my learning resources page.
- Also renamed the repo to be Eng learnings for 2022, rather than specifically Azure.
- For the rest of March, I'll be focusing on finishing up the AI-900 (Azure AI Fundamentals) MS Learn material with a hope of completing the AI-900 exam in April to earn the cert for free.

### 2022-03-15 to 2022-03-17
- **PASSED AZ-104!** Got 907, which was a pretty good score considering that 700 is a pass.
- I think it was between the 15th and 16th where I had an opportunity to redo most of the 300+ practice questions from exam topics and take a test from a course I purchased on Udemy that got me to that point. The focused effort over the better part of a 24 hour period really helped me memorize some things.
- Specifically what was most challenging (I found) was the monitoring things. Each of the capabilities in Network Watcher, specifically, overlap in various ways but each have their strengths. Beyond that, I really found that you really need to read the questions a couple of times. Missing a key part of the question could mean a different answer. Attention to detail is so important. 
- All that said, many of the questions are nearly word for word from the practice tests that can be picked up - either from examtopics or from other sites like whizlabs or udemy. Overally, examtopics is probably the most comprehensive.
- Also you can't forget about the case studies. I got through all the questions... or so I thought. And then suddenly I had another case study to do and I had left only about 15 minutes to do it!!!
- Anyway, super stoked that I finally got that out of the way.
- Next will be trying to finish off the AI-100 certification and get some tutorial videos out there (or try anyway).
- And when that is done, I will be moving on to the full architecture certification, and may try to get the kubernetes and blockchain certs in there as well.


### 2022-03-13
- finally complete all the questions on the exam topics practice test. Over 300 questions!! 
- feeling ok about the exam coming up on Thursday. It was a great day to book it.
- will spend the next few days re-reviewing some of the harder questions and topic areas.
- I spent some time with kuberbetes today too. I think that will be the next challenge - setting up and deploying to an AKS cluster. I'm also thinking of doing a tutorial to deploy an ipfs node to AKs.

### 2022-03-10
- Nearly done all the questions from examtopics.
- Feeling pretty good, actually, about taking the 104 exam next week.
- Would like to actually do a few labs before then.

### 2022-03-09
- Almost through all the 341 questions on examtopics. Taking forever because whenever I don't get the correct answer, I find myself going through all the comments and essentially trying to understand where I went wrong. And that happens frequently enough.
- Listended to the latest Azure Fridays podcast today. Talked about some recent changes to DNS availability\resiliency.
- Also read up on Azure HSM, including the dedicated payment HSM currently in preview.

### 2022-03-04 to 2022-03-08
- Still studying for the 104 exam, but had to push out the date another week because I'm still not quite ready. Last time pushing out.
- Continuing to go through the examtopics questions. Also nearly done the John Saville exam cram.
- Things that I need to doule down on :
  - the Network Watcher things (IP Flow, Next Hop, Packet Capture, etc)
  - Backup
- Feeling pretty comfortable with VNets and NSGs.

### 2022-03-03
- Haven't updated this log because I've been pretty distracted over the last week, but I've been continuing to work through the quetions in the exam prep from examtopics. Have also been continuing through the John Savill study cram.
- Originally was supposed to have az104 exam today, but pushed it out to next week due to still not feeling fully comfortable with all the content.
- [Simon Brown](https://twitter.com/simonbrown) has a bunch of great videos here : https://simonbrown.je/

### 2022-02-24
- Found this https://pulse.microsoft.com/en/skill-forward-en/na/fa1-get-rewarded-for-gaining-tech-skills-and-free-certifications-at-the-microsoft-spring-skills-challenge/
- Continued Exam Topics practice test. Each question takes a very long time as I'm also trying to make sure I fully understand the answer. Only about 10% through all 300+ questions there.

### 2022-02-23
- Did a few more questions today from Exam Topics. Not many though - distracted.

### 2022-02-22
- Spent a couple hours going through az104 questions on one of the question sites ([Exam Topics](https://www.examtopics.com/exams/)).
- At work helped solve an issue in Azure related to security roles for Databricks that the team had been dealing with for a number of months.
- Watched more of the Savill cram video
- Pushed out the exam a week.

### 2022-02-21
- Amazing study cram video from Youtube by John Savill: https://www.youtube.com/watch?v=VOod_VNgdJk&t=2775s
- Got through an hour of this video.
- Also went through some of the areas of the last practice exam that I took and re-learned some of the specifics -moving resources, vnet pairing, specifically.

### 2022-02-20
- Did another wizlabs practice test, but did _not_ score well. Will see how I'm doing closer to mid-week, but not looking good for a Feb 25 exam.

### 2022-02-19
- Spent some time on Azure Portal setting up a file share. Azure Portal was causing me some issues, but was able to setup with CLI.
- Also had trouble mounting the Azure fileshare on my desktop. Either on Windows or Linux. Kept getting timeouts which indicated to me that there was a local network issue - Windows firewall was not blocking outbount 445 port. Maybe my router or ISP was? I don't know.
- So I setup a VM on Azure and opened port 22. Created a local SSL tunnel through the VM and forwarded port 445 on localhost to the fileshare endpoint. That worked. A Point-to-Site VPN would probably have worked as well, but I didn't want to set that up.

### 2022-02-17 through 2022-02-18
- Worked more on the az104 cheatsheet
- Listened to latest Azure podcast
- Worked through more practice tests.
- At this point, still unsure if I will be ready to take the az104 exam on the 25th.

### 2022-02-16
- Added more to az104 cheatsheet and finished another practice test, scoring about 70%. Getting closer. After the practice test, I'm going through the incorrect answers and adding more to the cheatsheet.
- Obviously the cheatsheet is for studying and not actually cheating.

### 2022-02-15
- Found this interesteing and reflecting on how Azure Well Architected framework and the Assessment can fit into an architecture practice : https://www.youtube.com/watch?v=xDhaHSK7mgM
- Azure Well Architected Framework: https://docs.microsoft.com/en-us/azure/architecture/framework/?WT.mc_id=azureenablement-ch9-cxa
  - Video series, here: https://www.youtube.com/watch?v=UpQHmWxkVEU&list=PLLasX02E8BPCLAbeb31iT79Ml_a-LC7tZ
- Another architecture podcast possibly worth listening to. Not specific to Azure : https://podcasts.apple.com/gb/podcast/the-architecture-advice-process-with-andrew-harmel-law/id1106971805?i=1000551090745
- Created a basic load balancer and added some virtual machines behind. Only really tested with ssh, but get the idea. I struggled to figure out how to ensure that there was no public ip address enabled for the vm's. Just finally figured it out by re-watching a whizlab video. You can go into the network interface for the VM's and disable the public ip address. Easy peasy. I was trying to create a network rule such that only the load balancer could talk to the VM.
- Read through "What is gitops": https://www.weave.works/technologies/gitops/

### 2022-02-14
- While I'm working through Azure related things, I did come across a post about passing the CKA (Kubernetes) exam [on reddit, here](https://www.reddit.com/r/kubernetes/comments/ssk065/passed_my_cka_exam_first_time_here_are_my_tips/). Some neat links from within.
- Finished the whizlabs video course for az104
- Added some beginning details about the compute resources on the cheat sheet.

### 2022-02-13
- Almost completed the video portion of the whizlabs az104 course. About 15 minutes to go, really.
- Read through some of the things on the PowerApps roadmap here: https://docs.microsoft.com/en-us/power-platform-release-plan/2021wave2/power-apps/planned-features?ocid=AID3045259


### 2022-02-12
- Worked more on the az104 cheatsheet.
- Really great episode of Azure Podcast: 411 - Event Driven Architectures on Azure - https://azpodcast.azurewebsites.net/post/Episode-411-Event-Driven-Architectures-on-Azure
- Video: **Azure Cosmos DB extension for Azure Functions update with AAD support | Azure Friday -** [https://youtu.be/w002dYaP9mw](https://youtu.be/w002dYaP9mw)
- Free O'Reilly ebook : Azure AI Services at Scale for Cloud, Mobile, and Edge [https://azure.microsoft.com/en-us/resources/azure-ai-services-at-scale-for-cloud-mobile-and-edge/en-us/](https://azure.microsoft.com/en-us/resources/azure-ai-services-at-scale-for-cloud-mobile-and-edge/en-us/)
- Neat framework that sits on Teraform as sort of an abstraction layer. Not sure how much being used: Opta [https://docs.opta.dev/](https://docs.opta.dev/)
- Secure baseline AKS architecture: https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/containers/aks/secure-baseline-aks

### 2022-02-10
- Made it through some more whizlabs videos for az104 - virtual networking, load balancers, application gateway and vpn
- Updated the [learning resources page](https://github.com/jamiebeach/100-Days-of-Azure/blob/master/certifications/Learning-Resources.md) with some links to some practice exams and courses.

### 2022-02-08
- Started working on a ["cheat sheet" of sorts, for az104 certification here.](https://github.com/jamiebeach/100-Days-of-Azure/blob/master/certifications/az-104-Azure-Administrator/cheatsheet.md)

### 2022-02-07
- Continued down az104 path with attempting a practice exam on whizlabs. Only went through half the questions but managed to get nearly all of them. Mostly policies, locks, moving resources, etc...
- Also went through the rest of the networking course videos on whizlabs for the same az104.
- Listened to latest Cloudcast and [Azure podcasts](https://www.podchaser.com/podcasts/the-azure-podcast-725242/episodes/episode-410-fusion-dev-128109256).
- Azure podcast had a couple of neat things. 
  - First that there are Microsoft Global Black Belt Solutions specialist
  - There is a new HSM based service
  - Functions can be created with powershell on linux now
  - Containers can use virtual network
