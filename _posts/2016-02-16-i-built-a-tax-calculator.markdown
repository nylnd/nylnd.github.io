---
published: true
title: I built a tax calculator
layout: post
---
**(This is a repost from an old blog dated 26 July 2014)**

I built an SDLT NPV calculator - a little "tax bot" that takes rents due under a lease, calculates the net present value of those rents, and then calculates the UK stamp duty land tax (SDLT) that applies to the aggregate net present value.

Many of my subsequent postings on this blog - and my talk at Pydata Berlin - are likely to set out how.

This post is a guide as to why I built the Overlap, Rent-free and VAT Integrated Lease Liability Engine (or "ORVILLE", for short).

As a project, this might appear to be an odd thing to do with perfectly good spare time (and two kids to keep entertained of a weekend). After all, HM Revenue & Customs (or "HMRC", the UK taxation authority) already provide a perfectly serviceable webapp calculator, and it will eventually get you to the correct figure (eventually). So why bother to reinvent the wheel?

It's a perfectly legitimate question which I asked myself, and which my colleagues asked of me when I mentioned to them that I was doing this (or when they caught me hacking away on the train). But there were, I felt, a few reasons, and I have set these out below.

#1) Papercuts

SDLT is a tax on land transactions, designed by people who had no great grasp of the practice of property law, even though their grasp of the theory of property law is better than that of most conveyancers. Put simply, SDLT looks at leases in the way that a legal textbook looks at them - not like a legal practitioner does. But SDLT is a tax that must be handled by legal practitioners.

One of the funny things about SDLT - and specifically about the net present value calculator, is that it does work well on its own terms: you enter the term commencement date of the lease, its end date, and information on the highest rent in each of the first five years of the term. So far, so good - but one of the important points is that there are a surprising number of steps that you have to go through before you can ever get to the stage of undertaking this manual data-entry exercise.

The process leaves a lot of the work to the person doing the calculation. This is for several reasons, chief amongst which is that SDLT counts the term of a lease (for calculatory purposes) as running from the later of (a) the date of grant and (b) the term commencement date, in accordance with the venerable case of Bradshaw -v- Pawley (which is perfectly reasonable), whereas the lease documentation often sets an artificial back-date to ensure that the lease expires at the right time (perhaps in sync with the landlord's other leases at the property, for various legal and administrative conveniences). This artificial date is typically the one from which liability is then counted. The first five years from the term commencement date of the lease (which property lawyers count from) is almost never over the same window of time as the first five years from the effective date of the grant of the lease (which the tax man counts from).

The consequence is that people often have to undertake laborious manual calculations on paper to reconcile the differences between those two dates, and to determine the rent in each of the first five years of the lease - and only then can the relevant data be entered into HMRC's webapp and the NPV in question be determined.

#2) Rent-frees: not hassle free

Another particular 'pleasure' involved in getting to the basic data-entry is that there are, often, rent-free periods in leases. Again, in practical terms the HMRC webapp doesn't have any meaningful way to reduce rent payable by the amount of the rent-free period: again, you have to work it out yourself first. Typically this is done by working out the amount of rent that is ordinarily due, the number of days of the first year of the lease for which no rent is payable (manually, using a calendar, or perhaps alternatively using a website such as the excellent timeanddate.com).

Again, this results in another round of back-of-the-envelope calculations. One slip, and if this element of the calculation is incorrect, then the whole calculation again needs revisiting.

#3) The VAT of the land

SDLT is payable on VAT-inclusive rents, and VAT is charged on commercial rents with-ever increasing frequency. But the problem with that is that the VAT rate has been up and down over the last few years (moving from 17.5%, to 15%, back to 17.5% and then up to 20%, all within the space of a few years like the proverbials), and, again, manual calculation is required when looking back at compliance in relation to old leases (more of that later). Furthermore the way in which VAT, and VAT rate changes interact with rent payment dates gives another headache: on 4 January 2011, the UK VAT rate increased to 20%, but it was only on the next 'usual quarter day' for the payment of rent (25 March 2011) that many tenants parted with VAT at the increased rate. The only thing worse than a conveyancing solicitor's face when you tell them that they have forgotten to apply VAT is the crestfallen look when they have tried, but forgotten to apply the correct rates at the right time.

#4) Overlap hassle

SDLT has a funny sort of relief that is commonly called overlap relief, which never works in the way that anyone expects that it will. For starters, is isn't a relief, in the sense of being claimed in the return. What overlap relief does is to take historic rents on which SDLT has already been paid, and then offset these against the rents payable under the new lease (so that only the additional rent in the 'overlap' period is taxed). Overlap relief can be a particular hassle from a calculatory perspective, because you have to reconcile two different rent streams on a daily basis - cue more tears for your typical conveyancer.

#5) The importance of compliance

The rate of SDLT on the net present value of rents is 1%: in other words, it is practically nothing compared to bigger taxes like VAT or corporation tax. But leases are an increasingly prevalent form of property ownership for business (I like to think of them as the original outsourcing) - but just because there is a relatively small amount of tax at stake does not mean that the you haven't (a) got to get it right; (b) tell HMRC about it properly and promptly; and (c) keep hold of a sufficiently detailed set of records to allow you to deal with any future compliance obligations satisfactorily.

#6) Control over cost

This is another area. SDLT is a very difficult area in which to be both correct and profitable. There are lots of historical reasons for this, but a key one is that the pricing model for SDLT compliance is still based on SDLT's predecessor, stamp duty, which involved very simple arithmetic, and a runner going down to the local stamp office. Lawyers were traditionally saddled with this duty: trips to the stamp office were almost a right of passage for trainee solicitors. But lawyers go into the law as fugitives from arithmetic, so the complexity of SDLT lease compliance left them with a dreadfully difficult task that could take hours to deliver on.

A well-crafted tax compliance engine can turn questions of the billable hour into questions of the billable minutes. Which is about all you can afford to have. I wanted to experiment with keeping time costs down in compliance - and freeing myself and others up to do more interesting stuff.

#7) The control over the calculation and compliance stack

This is the big one. By creating a calculation engine that replicates (and then improves) the calculatory functionality of the HMRC webapp, it is possible to then scale it or increase its scope - which goes to the very heart of the exercise here: to enable rapid, comprehensive audit of large portfolios of leases for occupational tenants. If the data prep, and the data entry, do not have to be done by hand, then this can present signficant savings in relation to the time it takes to deliver an audit to a client who needs comfort that their portfolio of leases has been dealt with properly.

It is not difficult to imagine that this code has been dropped into a slightly wider code-base that can take significant volumes of input, and spit out a full SDLT analysis in a lot shorter time. Which was the second project that then derived from the original exercise.

#8) The intellectual challenge

Yep, I'll be honest, I thought that it would be an interesting exercise - someone always said that it's a lot easier to to learn to program if you have an 'itch to scratch'. And this one bugged the hell out of me much more than it really should have.

#9) The right tool for the job was pointed out to me

After another bundle of hassle on a calculation, I decided to ask the brightest person I know (Safe Hammad). He pointed me to Python as a useful tool. The Internet pointed me to the phenomenal Zed Shaw. And Zed's excellent book, *Learn Python the Hard Way*, pointed me to Wes McKinney's equally fantastic work *Python for Data Analysis*. And these books gave an introduction to the world of Python and the excellent Pandas data analytics library.

Now, using these tools for non-'big data' issues does, in essence, represent the use of a sledgehammer to crack a walnut. But just because something is built for big data doesn't mean that you can't use it on little data, too.

And when the sledgehammer is so awesome, and you **really** hate that walnut, then it's hard to resist having a swing.