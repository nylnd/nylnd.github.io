---
published: true
title: Pandas: let's get fiscal
layout: post
---
*this is the text from a blog originally written in 2014*

Pydata Berlin 2014 has come and gone.  And I gave my talk about what Pandas can do for tax.  If you want to be spared the [full 35-min video](https://t.co/0EfgHY6Hh8), then here is the potted version.

The key points in relation to this are that:

* there is increasing imperative for tax practitioners to commoditise their products;
* to do so will inevitably lead them to rub up against particular difficulties and limitations with spreadsheets, both as tools in and of themselves, and more particularly how they can interface well with other software (in particular databases); but
* Pandas can liberate them from these problems; and
* their pre-existing skillsets make them extremely able to pick up Pandas and do cool stuff with it.

##IMPERATIVE
The courts - and the courts of popular opinion - have stopped what the tax industry might have called its salad days.  Aggressive planning is frowned upon socially and legally.  The pressure is to be 'compliant' - to implement acceptable tax structuring well, and to have total transparency and accountability in how this is then reported to the tax authorities.

##COMMODITISATION
My experience from talking to people at Pydata is that they come to Pandas via statistical software and languages.  My own experience was (and that of others in my field will be) informed by a very different frame of reference - spreadsheets.

The spreadsheet is the tool of choice for tax professionals. [Some excellent research by PwC](http://www.pwc.com/en_US/us/industrial-products/publications/assets/pwc-mapi-tax-technology-survey.pdf) suggests that they are not going to give up using them, but equally that they are desperate for something better.  Can they have their cake and eat it?

There are three particular issues that spreadsheets have that might compel them to use something conceptually similar, but practically better. 

* Firstly, they're not great when it comes to handling time and dates - which is an extremely important ability to have when you work in tax.  Getting them to work in that way that you need is difficult and requires either a lot of manual data entry, plugins, or a working knowledge of Visual Basic.  

* Secondly, spreadsheets don't lend themselves to easy-in, easy-out manipulation of data.  Of course, Pandas can act very well as an intermediary - but since it can replicate the key functionality of the spreadsheet - why bother with the unnecessary intervening step?

* Thirdly, spreadsheets are used for immutable data storage, when they represent nothing of the sort.

##PANDAS & PYTHON

Pandas excels (if you'll pardon the pun) at handling time and dates, and series of data that ascribe values to time and dates.  This is in part because they operate 'off the grid'.  That's to say, they aren't bound in the same way by principles of cell-by-cell analysis.  You can rescale things very effectively.  The ability to refer only to key dates for each set of numbers (e.g. when the numbers being taxed change, when the applicable tax rates change, and when the applicable relief rates change), and leave the software to fill in the gaps without breaking a sweat, then dealing with tax numbers becomes a **lot** easier.

And because of Pandas' excellent interoperability with file formats, and Python's universality, it's far easier to enjoy the benefits of a whole host of other software in the ecosystem.

Just as I feel tax practitioners would be foolish to continue to ignore Pandas, it would be equally foolish for current Pandas users to be dismissive of just what an impact this functionality has for people in tax, simply because it appears so effortless and is taken for granted these days (which I feel would do a grave disserice ot the *phenomenal* work of Wes McKinney and the Pandas team).  As I said in my talk, something might be capable of large-scale application, but this doesn't mean that it cannot work wonders on small-scale application in the right context.

##TRANSFERABLE SKILLS AND GATEWAYS

I am very firmly of the view that learning Python - and learning to use Pandas - is well within the grasp of any competent tax adviser - particularly those with legal training.  The reasons are (based on my own experience) as follows.

###Transferable skills  
Drafting and coding are surprisingly similar skills - each attempts to condense a series of rules and behaviours into a mutually-exclusive, collectively-exhaustive set of conditions and actions.  Code declares variables; contracts define terms.  Code imports libraries that cover a point; contracts co-opt statute.  Code's mantra of DRY ("don't repeat yourself") - meet law's precedents.  Git diffs, blacklines.  Pair programming, four-eye review.  Test-driven development is basically worst-case drafting in hipster clothing.  

I would go so far as to say that coding and drafting are actually mutually-reinforcing skills.  Learning to code has improved my drafting, and I'm sure that drafting helped me to get my head around coding more quickly.   I'd probably go further and say that there's a lot that programming and legal practice could learn from each other.  No lawyer would use the term 'imposter syndrome' - but any of them would recognise it instantly.  (Each profession, sadly, has a lot to learn about diversity).

###Useful metaphors  
As code is similar to law, so one important aspect of the Pandas repertoire (DataFrames) is similar to spreadsheets.  That gives a handy frame of reference for explaining people what they can do.  Of course, Pandas is about a great deal more than these - but it's not a bad way to start getting your head around the power of that Pandas can deliver.  Having shown friends what Pandas can do, they tend to refer to DataFrames as "elastic spreadsheets", "smart spreadsheets" or (my particular favourite), "spreadsheets off the grid". 

The linkage to Excel is supported by the fantastic [xlwings](http://xlwings.org/) by Felix Zumstein, which provides a bridge between Excel and Pandas.

###Safe experimentation
In my experience, the excellent Anaconda scientific Python distribution allows the installation of pretty much all you need on conventional computer desktop environments.  For an extra layer of comfort for those who are still worried that their computer might explode if they mess around with things outside the world of Microsoft, a Raspberry Pi can be picked up for next to nothing.  And it will run enough Python and Pandas to learn from.

Another option is to use [pythonanywhere](https://www.pythonanywhere.com/), well, anywhere - certainly this gives a nice environment to explore Pandas.

###Excellent resources 
Subject to the very BBC-like proviso that 'other books are available', I struggle to see how anyone could top Zed Shaw's [*Learn Python the Hard Way*](http://learnpythonthehardway.org/) for a primer for a non-programmer on the world of programming.  Wes McKinney's [*Python for Data Analysis*](http://shop.oreilly.com/product/0636920023784.do) is then beautifully self-explanatory (which I fear it might not *quite* be for someone with zero-programming experience, compared to - say - an R refugee).  I cannot recommend either book highly enough for someone looking to explore this field - although in contrast to the code bootcamps I would strongly advise against cherry-picking chapters you like or think are relevant in either book.  There may one day be a market for a companion piece that pitches this stuff directly to tax people.  But maybe not *yet*.


My talk finished with a demonstration of ORVILLE - that much at least is for another post - but you can catch a brief glimpse towards the end of [the video of my talk](https://t.co/0EfgHY6Hh8).