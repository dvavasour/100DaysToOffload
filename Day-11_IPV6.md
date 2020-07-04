# Working with IPV6

*"Day 11: we embrace the 21<sup>st</sup> Century"*

## The Story So Far
Humanity has been running IPV4 for 40 years, since a time when computers were expensive, network connections were expensive and 32 bits of addressing space was considered infinite.

It quickly became clear that computers were getting cheaper, networking was getting cheaper, and that this infinite addressing space could no longer be considered infinite. And so two things happened in parallel:

* Workarounds were devised to eke out IPV4 space (CIDR, NAT)
* A new protocol with a bigger address space was devised (IPV6)

*(I'm not going to explain CIDR and NAT  here - there are good articles to be found that will do a better job than I can.)*

The world responded to these two things in exactly the way you'd expect: grasped onto every bodge that would keep IPV4 alive and ran it into the ground.

## Why is IPV6 better than IPV4?
Firstly there's the [Spinal Tap](https://en.wikipedia.org/wiki/Up_to_eleven) answer: it's two better.

Secondly there are speed benefits: IPV6 headers don't include checksums (these usually exist at layers 2 and 4, so can be omitted at layer 3); IPV6 packets can't be fragmented, so the headers and processing for fragmentation can be omitted.

And thirdly, there are enough IPV6 addresses (2<sup>128</sup> instead of 2<sup>32</sup>) that there is no need for NAT anywhere: every IP address is fully qualified. This is a big deal because almost every IPv4 connection passes through multiple layers of NAT, so connection tracing for diagnostic or security purposes is frustrated.

## How do I use IPV6 as a client?
Sign up for an ISP that includes IPV6. In Great Britain that includes [Zen Internet](www.zen.co.uk), [Sky](www.sky.com) in most cases and my ISP [Andrews and Arnold](www.aa.net.uk). My home is allocated a /48 block of RIPE address space (IPV6 network aggregations are always on 4 bit boundaries and subnets are always /64, so a /48 block allows 4 layers of subnetting) and I have actually active a single /64 network.

Almost every device running an IP stack from the 21<sup>st</sup> century will support IPV6 out-of-the-box (Windows, GNU/Linux, iOS, Android, Sky box, Nintendo Switch, my Sony Bravia telly ...) so you don't need to do anything.

#### How does my client know whether to connect with IPV6 or IPV4?
When any piece of software needs to resolve a name into an IP address it places a system call. This will normally spill over into a DNS call.

In an IPV6 connected system, the DNS client will search for an `AAAA` record first which, if resolved, will return an IPV6 address. If the `AAAA` request returns `not found`, it will then search for an `A` record which returns an IPV4 address.

It's instructive to add the extension *IPVFoo* to either Chrome or Firefox. This extension shows the names resolved in rendering a page, and the associated IP addresses.

## The easy way to use IPV6 as a server in AWS
The reason why you should use IPV6 for your IaaS in AWS is the converse of why JFK said we should go to the moon. We use IPV6 in AWS *not because it is hard, but because it is easy.*

The short version in AWS:

* Tick the IPV6 box when you create your VPC
* Add routeing rules so that your /56 is internal and the default route (`::/0`) is your Internet Gateway
* Allocate IPV6 ranges as well as IPV4 when you create subnets
* Add IPV6 rules in your Network ACLs alongside your IPV4 ones (usually allowing traffic from `::/0`
* Include IPV6 rules on the Security Groups you create

And that's it. When you create instances in this VPC, they will have IPV6 addresses as well as IPV4. And **the IPV6 address is the same both from inside and outside the VPC**.

You can then add both A and AAAA records to your nameserver. I'll normally add two AAAA records, one to match the A records and another with the prefix `ipv6.<fqdn>` for debugging purposes.

The lazy sysadmin will, of course, put all this into a set of Terraform modules.

## Is there anything else I should know?
Yes. Raw IPV6 addresses contain colons (e.g. `2a05:d01c:4bf:3100:0123:4567:89ab:cdef`). There are many contexts in which the use of colons already has a different meaning (e.g. in a URI). In these cases you should enclose an IPV6 address in square brackets, so a URI would look like `http://[2a05:d01c:89ab:cdef:0123:4567:89ab:cdef]:8000/here/is/Splunk/on/port/8000`.


## Why am I writing this post?
For many technical people IPV6 is considered a bridge too far, a closed book, not wanted on voyage. But there really will come a day when IPV4 can be switched off, like analogue television, and unless you're a networking professional it's really not hard to use.

This post is day 11 of my #100DaysToOffload challenge. Visit https://100daystooffload.com to get more info, or to get involved.