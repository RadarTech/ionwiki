# Local Lightning

**What inspired your team to work on Local Lightning?**

At the time of the hackathon, I wasn't sure what to build. I spent a couple hours after hearing the "Social Good" prompt just brainstorming ideas and speaking to a few friends about it. Patrick Stanley from Blockstack had actually sent me a Blockstack post about a list of applications that could be built on Blockstack and one of the first ones was a decentralized Local Bitcoins. As soon as I saw that, I knew it was what I had to do. I already have some experience building a P2P decentralized application on Blockstack, so I knew a simple MVP of Local Lightning would work out well and definitely has a real-world use case, which mattered a lot to me. I'm all about marketplace freedom, which unfortunately with Local Bitcoins and with many crypto projects implementing KYC, is needed more and more each day.

**In three sentences or less, tell us about your project.**

Local Lightning is a website designed to get local sellers and buyers of bitcoin interacting with each other on the Lightning Network. By focusing on sellers/buyers interacting via the Lightning Network, what we'll see is quick engagements that end as soon as cash changes hands and the Lightning payment button is clicked. Instantly verifiable, \(near\) fee-less transactions with no need for escrows or waiting 10-60 minutes for block confirmations.

**How did you build Local Lightning?**  
  
I built Local Lightning on top of Blockstack \(which allows for decentralized logins and data ownership for users\) and Lightning Charge. Lightning Charge made it easy to accept and query invoices via my own c-lightning node. For the hackathon, I made it a simple skeleton VueJS application, but have since put a lot of design effort into it to make it pretty.

**What were the biggest development challenges?**  
  
The biggest challenge wasn't so much the development at all, but the interactions with Lightning tools. When I was trying to implement WebLN \(a web standard for browser plugin lightning payments\), I had a hard time finding things that supported c-lightning. Seems like a lot of tools/wallets in this space support LND instead of c-lightning. I was about to give up on trying to implement WebLN until fiatjaf \(another hackathon participant\) pointed out that he made a c-lightning WebLN compliant plugin \(kWh\), which worked out really well.  
  
**What operational challenges have you run into since launch?**  
  
I've never been the strongest at design and frontend in general, but I'd have to say that Lighting Channel management has been pretty challenging since launching. Luckily, with BTCPayServer, setting up a production level Lightning Node was easy, but since I am using c-lightning instead of LND, I miss out on a lot of channel management features like Loop Out. I have some ideas to bring more liquidity channels to my Lightning Node, without relying on people to open channels with me directly \(though there have been a couple kind souls that have already!\), but in general it hasn't as easy to deal with so far.  
  
**What are your plans for the project post hackathon?**

The first plan was to design and launch, which I'm super excited that I was able to do so! Moving forward though, I hope to add possible core features such as messaging, review systems, and maybe even basic wallet support for connecting to your own nodes in app. Besides that, I hope to integrate with the community and provide an app and features that people want to use.  


**What daemon features are you most excited about?**

It just technically launched, but I'm really excited to try out Loop Out with LND. My home node is using LND, so I planned on upgrading soon to try it out. Besides that, I wanted to look into what plugins exist for c-lightning and what might come soon there as well.  


**What projects are you most excited about this next year?**

I'm really excited about the idea of submarine swap exchanges with lightning. I recently found out about SparkSwap and their Lightning exchange, so I'm looking forward to seeing it grow and using it.  


**Where can we find code or working application of your project?**

Website: [https://www.locallightning.net](https://www.locallightning.net)

Github: [https://github.com/AnthonyRonning/Local-Lightning](https://github.com/AnthonyRonning/Local-Lightning)  


