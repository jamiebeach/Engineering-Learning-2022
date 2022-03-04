### 2022-03-03
- Haven't updated this log because I've been pretty distracted over the last week, but I've been continuing to work through the quetions in the exam prep from examtopics. Have also been continuing through the John Savill study cram.
- Originally was supposed to have az104 exam today, but pushed it out to next week due to still not feeling fully comfortable with all the content.

### 2022-02-24
- Found this https://pulse.microsoft.com/en/skill-forward-en/na/fa1-get-rewarded-for-gaining-tech-skills-and-free-certifications-at-the-microsoft-spring-skills-challenge/
- Continued Exam Topics practice test. Each question takes a very long time as I'm also trying to make sure I fully understand the answer. Only about 10% through all 300+ questions there.

### 2022-02-23
- Did a few more questions today from Exam Topics. Not many though - distracted.

### 2022-02-22
- Spent a couple hours going through az104 questions on one of the question sites ([Exam Topics](https://www.examtopics.com/exams/)).
- At work helped solve an issue in Azure related to security roles for Databricks that the team had been dealing with for a number of months.
- Watched more of the Savill cram video
- Pushed out the exam another week.

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
