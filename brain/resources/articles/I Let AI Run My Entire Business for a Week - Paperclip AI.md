---
captured: 2026-03-14
source_url: https://www.youtube.com/watch?v=qwCH8nyRBCw
category: transcript
author: Aaron Friends
source: YouTube
type: video
---

# I Let AI Run My Entire Business for a Week — Here's What Happened (Paperclip AI)

## Summary

Aaron Friends documents his week-long experiment using Paperclip AI (Dot Dada's project) to automate his entire business operation — from company setup to development, documentation, and management. The project was built around an existing traffic exchange script business he runs with his wife Sharon, and demonstrates how AI agents can autonomously handle complex business tasks.

## Key Insights

- **Paperclip AI setup:** Started with the CEO heartbeat initialization and company context
- **Full automation achieved:** Created brand identity, documentation, skills, website, and agents autonomously
- **GitHub integration critical:** Keeping entire company folder in version control for transparency and rollback
- **iCloud warning:** Mac users need to disable "Optimize Mac Storage" for the agents folder — or files get offloaded breaking the system
- **Traffic exchange script:** The test business — exact match domain (trafficexchangescript.com) already ranking #1 on Google within days
- **Folder structure:** Company folder → development (source code), website (HTML), agents (auto-created), documentation (auto-generated)

## The Paperclip Workflow

### Initial Setup

1. **Installed Paperclip locally** with custom adjustments
2. **Created company heartbeat** using Claude Cloud (20x max plan) for enhanced context
3. **Provided minimal context:** Just development folder with source code + a few HTML design files
4. **Let AI take over:** Agents created folders, documentation, skills, and website autonomously

### Company Structure Created

```
traffic-exchange-script-company/
├── development/           # Source code (original input)
├── website/              # index.html + designs (original input)
├── agents/               # Auto-created by Paperclip
├── documentation/        # Auto-generated customer docs
├── skills/               # Auto-created capabilities
└── design/               # Auto-created style guide
  └── brand/
    └── style-guide.md     # Based on HTML input files
```

### Git Integration

**Critical tip:** Initialize git in the company folder and sync to GitHub:
- Complete version control log
- Can review changes on phone from couch
- Paperclip auto-creates branches and merges
- Easy rollback if something breaks

**iCloud warning:** Disable "Optimize Mac Storage" — offloaded files break Paperclip agents.

## What Paperclip Built Autonomously

- ✓ Brand identity and style guide (from a few HTML pages)
- ✓ Complete documentation (from source code with no prior docs)
- ✓ Website refinements and new pages
- ✓ Skills for various business functions
- ✓ Agent configurations and workflows

## Business Context

**Company:** Aaron and Sharon (husband-wife team)  
**Projects:** Domain portfolio management, affiliate marketing, traffic exchange script  
**Domain:** trafficexchangescript.com (exact match domain)  
**Result:** Ranking #1 on Google for "traffic exchange script" within days of sitemap submission

## Key Quotes

> "I don't really want to create competition for myself."

> "I've seen already some people in the Discord where some files of the agents were missing... If you're using a Mac with iCloud, it tends to offload files into your iCloud and then remove them locally, which causes the entire thing to break."

> "I keep this entire thing downloaded. That's the little check mark you want to check on the main working folder for your project."

> "I git initialized that and synced it to GitHub. So the entire company folder is on GitHub and version control... that way I have an easy log on my phone when I'm on the couch."

> "It actually made this style guide... I'm like, 'Oh man, that's fun.'"

## Full Transcript

<details>
<summary>Click to expand full transcript</summary>

Hey, what's up everyone? It's Aaron Friends. Uh, this is a little bit of an awkward intro. I normally have like a company or brand name, but today I don't. Um, first of all, my apologies for doing it this way. Um, I was supposed to go live and do this in a live stream on the Discord and, um, truth of the matter is, uh, this is all so new that even even to me that I'm sort of worried about sort of doxing myself or exposing stuff that I don't want to. So, this recording gives me a little bit more control about what I share out there and what I don't. Um, so this is about paperclip. It's about the cool new project from Dota Dada. Sorry if I mentioned your name right or wrong, but um yeah, I'm trying. First of all, thanks to you for releasing this and unleashing this onto the community. Um it's been an insane ride for me. Um I actually started it last week on Friday. Um and oh, it's Friday the 13th. It's a great day to record this video. Um so, um so I want to look sort of back with you, bring you along with my ride to see what I've achieved with Paperclip. And hopefully along the way you'll be able to to you know extract some learnings from it. Um the original plan was to set up a new company but uh I don't really want to create competition for myself. Uh I don't also don't want to yap too much uh about myself or whatever I'm doing. U but I just want to go show you what I've done and uh how I did it so that you can do it too in your business. Right. So using paperclip of course using the uh uh the paperclip um you know application. So, uh, first of all, um, I've been working from home with my wife Sharon. Uh, our company name is Aaron and Sharon. And under Aaron and Sharon, we have a lot of projects. Uh, one of which is, uh, is basically managing our domain names and just snashing up cool ones that we like. We're also in the affiliate marketing business among many other things. And one of the softwares that we've been playing with over the past 10 to 12 years, it's called a traffic exchange script. And uh for those of you who get triggered immediately, I'm sorry, but it's, you know, it's just a fun project for me to work on. Uh for those who don't know, are there are the sites where you sign up, you browse other people's websites that gets you credits, and then you can promote your websites, which other people's uh other people will be browsing. Um and a couple years ago, I actually managed to snatch up the domain traffic exchangecript.com, which is of course the EMD, the exact match domain, uh uh for people that are searching for that on Google. Uh actually I just noticed that uh that that the the URL the domain is already ranking on the first page in the first position for the keyword traffic exchange script again within just a couple of days. I think I submitted my sitemap yesterday. Um so let's take a look. So first of all I installed uh paperclip. That's what I started with and then I went through the onboarding uh and uh let's go to issues. And if we scroll all the way down we go. I started on March 6th. Let's see why this finder keeps popping up. All right, let's scroll down. Move something out of the way for my recording session if you don't see. Um, and then it's it's created, as you can see here at the bottom of the screen, uh, create your CEO heartbeat. That is what, uh, I started with, just like you did. And if we go and look into what I've done, I've actually uh copied out um the default heartbeat text and I provided a bunch of context in a new cloud conversation at cloud.ai. Um I'm on the 20x max plan and I just said, "Hey, you know, here's the heartbeat that I want to set up. Um uh uh can you incorporate all of the data and information that I already have?" So it basically did that. I didn't even bother reading it. I just copied that and chucked it in. Uh and it's, you know, a couple minutes later said done. You know, I've set up the uh the company to head, etc., etc. So, that's what happened there. Um from there, um require phone signing off. Um I provided some brand identity uh for the uh uh for the project. And how I did that was on my hard drive. I have the Finder open here. Uh, I have a paperclipip folder uh where I plan to manage all of my companies. I have a local installation of paperclip where I've made some adjustments as you can see here on the screen. I have some icons here to to hide projects, pause agents, add some stuff um uh just to make management of agents easier uh for me at this at this point in the in the whole process of of automating a a business. And the traffic exchange script idea was just a test to see if it if I could pull it off. So I created a folder uh my working folder on GitHub is just traffic exchange script which is all private. Um and I said I thought well let's just add company at the end and add that into a new folder. So then I added a development folder where I've here added my folder that is the source code um of the traffic exchange script and I added a website folder and which was the post index HTML. This was the original uh HTML that I had Claude design as well. Obviously based on some of the findings of the of the software that it that I had earlier created with with Claude as well and with Ralph, but that's for another video, another conversation. But this was the original page that I'd made. Uh I did, you know, some work for the check. I was like, "Oh, I was a checkout skill. All right, just do that." And then I had the blog and Okay, so there's a whole bunch of of little designs that I made. Um, and I to my recollection, um, that's basically all I gave it, uh, inside of this folder. I saw it create the agents folder. A quick tip, uh, I've seen already some people in the Discord where some files of the agents were missing. Now, if you're using uh a Mac with iCloud, uh it tends to offload files into your iCloud and then remove them locally, which causes the entire thing to break because uh it's going to be missing files that are not needed that it thinks are not needed. It's going to offload that. Uh so, for example, I've seen some people say, "Hey, all I have left is a life folder or all I have left is heartbeat.Md and yeah." So, you go back and then uh on agent. So, first of all, I keep this entire thing uh keep that downloaded. But that's the little check mark you want to check uh on the main working folder for your project. Um but I highly recommend you you put your whole working folder for your uh company in a folder and then what I did was I git initialized that uh and synced it to GitHub. So the entire company folder is on GitHub and version control as well. So that I can always look back and it's creating branches and merging into each other. it's doing that automatically. Um, but that way I have a an easy log on my phone when I'm on the couch or something like that, right? Um, so then um because my terminal is already connected with GitHub, it just started using it on its own, right? Um, so that was a development folder and it basically went from there. I think the documentation there came later. um skills all came later and it basically just started creating these folders on its own um because it has full access to this folder. Um so let's go back to paperclipip. Let me try to trace some things back. I added some brand identity uh the head of design uh uh actually started creating that. It went and created a design folder and it went for brand and a whole style guide based on those few HTML pages. It actually made this. I'm like, "Oh man, that's that's fun." Right? We've se we've all seen Claude uh do this. Okay, this is interesting. So, um that way it was able to to piece together how I wanted the entire thing to look, right? Um then the documentation, so I had the software in the development folder, but I had no documentation for customers. So, I delegated with the CEO. I said, "Hey, can you have the can you hire a head of support and have a head of support uh uh write the entire documentation." And I came back and there was just you know a huge you know I had just had a brand new documentation folder with you know proper documentation in MarkDown and everything so that I can you know basically uh get this thing done.

[Transcript continues...]

</details>

## Related

- [Paperclip AI](https://github.com/dotdada/paperclip) - Dot Dada's project
- [Claude Cloud](https://claude.ai) - Used the 20x max plan for context
- [Traffic Exchange Script](https://trafficexchangescript.com) - The actual site (ranking #1)
