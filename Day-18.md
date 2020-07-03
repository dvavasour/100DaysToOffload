# My ISP
*"Day 19: You get what you pay for."*

My ISP isn't terribly expensive, but doesn't get recommended on uSwitch or CompareTheMarket. But I moved to them when one of the majority providers left me with a flaky service for two months.

It wasn't their fault. There was an intermittent fault in the cabinet that serves our village. I'm not au fait with the equipment that underpins domestic broadband, but in datacentre terms there was a flaky line card in the cabinet. It was affecting the whole village: I was having to travel 25 miles each way to my office because I couldn't reliably work at home; the vicar was leaving emails from parishioners unanswered because he couldn't read them. Maybe one in three houses were having broadband outages.

Now, as consumers we have no way to interface with BT Openreach, who operate the exchanges and cabinets - our sole relationship is with our ISP. And the ISPs lodge reports with BTOR. So we had the farce that house after house was visited by BTOR where they checked the drop cables and said that wasn't the fault - charging the ISP £75 each time. My then ISP executed a KillSession on my connection and, when it went again, said "we've done it once, we now have to leave it while BTOR investigate". I ended up writing to my MP: either BTOR were so useless that they couldn't identify an obvious pattern in their fault reports or, worse, they were leaving the fault unfixed so they could fill their boots with call-out charges to the ISPs: the fact that customers were left with no service wasn't a consideration. Eventually, one Sunday morning, everyone's broadband started working again and there were no more problems - they'd finally fixed the root cause after two months.

So I switched ISPs. The bunch I'd been with had run an IPV6 trial a couple of years previously, but hadn't taken it forward and had instead invested in carrier grade NAT. If I wanted IPV6 I was going to have to go elsewhere and, after a little market research, I opted for Andrews and Arnold (www.aa.net.uk).

They give me what __I__ want from an ISP. They:

- Let me talk to someone knowledgeable when I need to talk (and answer emails for background queries)
- Present their costs fairly and openly, with a choice of paying one-off fees up front and no lock-in or bundling them and choosing to be locked in
- Let me see the exact condition of my connection

This last is unique: their router performs a layer-2 ping on my router every second and from this and other metrics I can see in real time and up to 30 days' history:

- The upstream and downstream bandwidth usage minute by minute
- The rate of packet loss (if it is regularly more than zero for more than an instant I know, and they know, that something is wrong)
- The average and maximum ping latency at any moment: this should be constant unless I'm really spanking the line

They also let me set some connection parameters: for instance, my router can be set to use 95% of the available bandwidth, meaning that I don't cause line congestion resulting in latency and packet loss (more important than ever in these times of VOIP and video conferencing). While other ISPs have varying levels of line contention in the back-end capacity, A&A's position is that contention rates aren't important, congestion is. And they endeavour never to be the cause of congestion to customers - if they regularly see it somewhere in the network they fix it.

I also like transparency when something does go wrong: a couple of months ago there was an unplanned loss of connectivity to some areas, lasting half an hour in the afternoon. As a customer I was able to see the trouble ticket and the updates shown as they worked on it - the next day I looked again, and the fault had been properly closed out (a route table poisoning issue that wasn't possible in a firmware update that was already queued up to be implemented).

They're no technical slouches either. As well as offering IPV6, I've been able to point Firefox to their DNS over HTTPS service, taking out the plain text transmission of queries. And privacy is taken seriously: I've not inspected myself, but I believe them when I'm told "we don't log DNS queries". All part of ambient privacy: _"The details of your day to day life should not be a matter of record"_.

And finally, there's some proper nerdery behind them as well: there is a record of their Friday afternoon experiment to see what sort of ADSL bandwidth could be got from a length of wet string - turns out the answer is over 1Mb/s.

You can keep your BT Internet or Plusnet or Talk Talk or Sky - whatever the price comparison sites may tell me, it's A&A for me.


*This post is day 18 of my #100DaysToOffload challenge. Visit https://100daystooffload.com to get more info, or to get involved.*