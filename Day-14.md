# My Portfolio Project
*"Day 14: A bit of Python, a bit of Splunk."*

I've been tinkering for a while with a Splunk development instance. It sits in AWS on a *t3a.medium* spot instance on a 50GB volume, and costs me about $0.55 per day. It's a bit of a kitchen sink where I try stuff out, and every few months I have to remember to renew my Splunk development licence.

I've also been tinkering with a Raspberry Pi 3B. Among other things, I attached a GPIO sensor from Pimoroni, which measures air temperature, pressure, relative humidity and gas resistance (which is an indicator of air quality).

I've got the RasPi forwarding the measurements to Splunk. Previously I'd installed a Universal Forwarder, but for these regular measurements it made more sense (and gave a learning opportunity) to send them using the HTTP Event Collector (HEC). I found a Python module to toss events to HEC, though from what I now know it would be as simple to generate a payload for the Request module. So I set this up to take readings every 5 seconds and forward them as events to HEC - I was then able to produce a pretty little dashboard.  
  
Next I wanted to send them to Splunk as metrics rather than events: metrics were introduced in Splunk7 and are typically 2-3 orders of magnitude faster for numerical data. After a bit of fnurgling I was able to lob the readings at HEC in a format suitable for a metrics index. My code for this end is not pretty: it's all at a single level with parameters hard coded at the top of the file. The script also hangs every few days - I think it stalls when reading from the device, as the data stream to Splunk just stops.

So I need to do some work on this code. It needs to be properly structured, and I'm going to add a periodic request to Dead Man's Snitch, so I get notified when it hangs.

I've also been tinkering with an eInk display on a separate Pi Zero. This is now putting a request onto the REST API of Splunk (authorised with a token) and displaying values on the eInk. This code is more recently written, so is somewhat better structured and has the parameters in a config file - it is single pass, so a cron job runs it every 5 minutes to update the eInk.

I've set up a Github repository and some of the code is in there. My intention is that I make it all presentable enough that I can offer it as a three component portfolio piece:

1. The code to read the sensor and forward it to Splunk
2. A Splunk app where all the relevant Knowledge Objects are held
3. The code to run the display

I'll then also need to create an overarching README to show how it hangs together, together with a README for each component describing how it works and documentation strings once my code is properly structured.

While the problem space is relatively trivial, getting it from *"Oh look, it works"* to *"Here's something I'm prepared to show people"* is going to need quite some time. Hope to have that done before my 100 Days/Posts are up!

**This post is day 14 of my #100DaysToOffload challenge. Visit https://100daystooffload.com to get more info, or to get involved.*


