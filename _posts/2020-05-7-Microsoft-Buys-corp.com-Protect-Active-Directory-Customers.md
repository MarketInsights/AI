---
layout: post
title:  Microsoft Buys “corp.com” to Protect Active Directory Customers
categories: Economic
comments_id: 24
---

In February it was reported that the owner of the domain name <corp.com> had announced that he’s selling that domain name.  Why should anyone care about that?  Of course, if he were selling <mycompany.com>, no one would.

But <corp.com> is different, and the reason it’s different has to do with how Microsoft Active Directory works: companies using Active Directory that didn’t set their configuration properly are likely using an old default “domain” of <corp> – something that used to be benign back in the days when the number of top-level domains (TLDs) were limited, and things like <example.corp> couldn’t happen.  That’s not a wise thing to do now with widespread use of Generic TLDs, but it’s still OK at the moment because the <corp> TLD has not been assigned to anyone and is not delegated in the Domain Name System (DNS).  Someone using their Active Directory client from outside the company, on the open Internet, would be trying to resolve <corp> through the DNS and would get an NXDOMAIN (non-existent domain) response.

But there’s another wrinkle: in order to make life easier, network stacks, including the one in Microsoft Windows, respond to situations such as this by “guessing” what domain you might actually be looking for, appending certain known suffixes.  Can’t find <corp>?  Maybe that was a typo: let me try <corp.com> and see if I can find that.

In comes Mike O’Connor, owner of <corp.com>.  O’Connor has set things up so that when you do try a DNS query on <corp.com>, you get a harmless response – nothing bad happens.  Because O’Connor is a Good Guy.  A Bad Guy might send you to a computer he owns, one which is set up to steal everything on your computer that Active Directory will let him access – and, in fact, O’Connor and others tested this, years ago, and quickly shut down tests when they realized how much access this provided.  And he’s kept that domain name sheltered ever since.

On Microsoft’s side, they have released a number of Active Directory updates to mitigate this situation, but those updates are not widely installed because of the impracticability of shutting down an entire Active Directory network for a significant period of time while the updates are installed and tested, and because the updates are likely to be incompatible with other older, out-of-service software that many companies continue to use and depend upon.

Once O’Connor announced that he’s selling the domain name, for a starting bid of $1.7 million, the security community became rightfully concerned that it not be bought by a Bad Guy.  An immediate call came out to Microsoft, on the “You broke it, you bought it,” principle: Microsoft created the mess with their choice of using <corp> in the first place, so they should pony up the money to buy the domain name and protect it themselves.

Well, now they have: in mid-April, Microsoft announced that they will buy <corp.com> from O’Connor (who clearly had been holding out, unwilling to sell it to the wrong parties), specifically to protect their customers.  Microsoft will then become the steward for the domain name, and will themselves become responsible for keeping users of their Active Directory software clear of this exposure.

There is still an impending problem with the use of <corp> in Active Directory: should another round of TLD sales from ICANN result in the sale and delegation of <corp> itself (as opposed to <corp.com>), we would see the same exposure – a general issue called namespace collision, where a name that had been used for one purpose (in this case, private, unauthorized use by Active Directory) starts being used for another (authorized delegation as a public domain name).  The ICANN Security and Stability Advisory Committee (SSAC) is working on a multi-year effort, the Name Collision Analysis Project (NCAP), to identify issues, mitigations, and recommendations with respect to the more general name collision problem.

References:
[Corp.com is up for sale – check your Active Directory settings!](https://nakedsecurity.sophos.com/2020/02/14/corp-com-is-up-for-sale-check-your-active-directory-settings/)
[Microsoft Buys Corp.com So Bad Guys Can’t](https://krebsonsecurity.com/2020/04/microsoft-buys-corp-com-so-bad-guys-cant/)
[Name Collision Analysis Project (NCAP) Study 1](https://www.icann.org/public-comments/ncap-study-1-2020-02-13-en)
