---
layout: post
title:  "Driving Large Projects"
date:   2015-09-06 14:42:19
categories: leadership
---

I've been a software engineer at [Box][box] for a little over 4 years.  Since even before
I joined, there's been a holy grail project that engineers have always talked about, but
we've never been able to execute against: building our website on top of our API in order
to start breaking apart our massive (now ~1.5 million line) PHP monolith.  About 3 months
ago, we decided to tackle this project in earnest, with about 40 people working over the
next year to split the monolith.  As the driver of this project, I've been thrust outside
my comfort zone (writing code), and have been forced to learn a lot of what appear to be
in retrospect obvious lessons.  I wanted to write these lessons down because I see myself
and others (both within and outside of [Box][box]) making the same mistakes over and over.

##People can do more as a group than alone

The first thing that struck me about driving such a large project was that it was nothing
at all like I expected.  I thought I would show up, start giving orders, and everything
would fall into place.  Nothing could be further from the truth, and it all comes down to
one undeniable fact:

Everyone has their own goals, and no one cares what you want

This is completely obvious when you write it down, but I see engineers - including myself -
get this wrong over and over.  In my mind, breaking the monolith apart was so clearly the
most important thing to be doing, and I simply couldn't fathom why this wasn't obvious to
everyone else.  Were they dumb?  Were they just being difficult?  Were they actively trying
to drive me insane?  Of course the answer is no, but the temptation is so strong to pretend
like its yes, that I'll give the real answer once more:

Everyone has their own goals, and no one cares what you want

This seems bleak, but its really quite powerful.  What this means is that when someone says
they don't want to work on what you want them to work on, what they're really saying is that
they don't see how working towards your goals helps them achieve their goals.  Your job is
to understand their goals, and be able to evaluate if those goals can be made to align
with your own.

Luckily, this is easier that is sounds, because in most cases people can accomplish more
as group than alone.  (add some example)

##By empowering people within the team

The other thing that struck me is how few decisions I actually make.  I had the impression
that as the driver, people would come to me with questions of deep importance, and I would
pontificate on how to make the world in the image of my vision.  But that was wrong too:
people don't want to build my vision - they want to build their own.  And rationally, that's
ok.  But it was really hard for me to accept that, because one of the hardest things for 
engineers to do is step back from the details.

Focusing on the details is absolutely killer when leading a large project.  Its bad from 
a time perspective: there
aren't enough hours in the day to make every decision or answer every question on such a
big project.  Its bad from an expertise perspective: you can't possibly be better at
everthing than the fifty other people on the project.  But far more important than either
of those: no one wants to work on a project where they are constantly micromanaged.

Time and time again I have seen other engineers - and had to stop myself from - trying to
dictate minutiae on a project that really doesn't matter.  I've seen a critical ten person
project grind to a halt because the tech lead and a developer couldn't agree on what
type of config file to use (yaml of course).  I've seen a developer leave a team because
his class and variable names were constantly nitpicked by the tech lead.  In cases like 
those, it doesn't matter who is technically correct, the tech lead is wrong because the
project is worse off than if he or she had stepped back and allowed more freedom.

This tendency is incredibly strong, and the only way I have found to fight it is with a
little bit of rigid process.  I force myself to write down three fundamental, make or
break decisions of the project, make sure all the track leads know those points, and tell
everyone very clearly that for any other question or decision, I will make my preference
and reasoning known, but the power to make that choice lies in developers working on it.

Choosing these three critical principles is where you wield the most influence as a leader.
They must be strong enough that if they are met, the project will be a success; they must
be reasonable enough that people can agree to them without much argument or discussion; and
they must be clear enough that anyone working on the project can know if they are in line
with them or not.  For the splitting the monolith project, they were:

- We must be able to deploy code for the web applications independently from the business logic
- All access to the business logic must be through APIs, and we must be able to bless a release
  of the business logic using only automated testing
- We must be able to at least write down an execution and resourcing plan that has the project
  complete in a year.  Schedules slip in real life, but there should not be glaring holes that
  we can point to and say "no way is this going to work"
  
And that is the extent of my input to the process.  I can offer guidance or thoughts, but
ultimately, I do not own the vision of how we accomplish those things.  In fact, I should
actively push other people to develop their own visions for how we accomplish those things
because that helps ensure that their goals and own my are aligned.
  
##And engaging with people outside the team

The final thing that surprised me a great dea was just how difficult it is to engage
constructively with people outside the team.  I have seen numerous projects - some first
hand - get bogged down for two reasons: people being critical of the project for not meeting
goals that were never set and people offering advice but being unwilling to help implement
it (this is probably just two symptoms of the same thing).

The first problem is incredibly common with large projects: people will generally assume
the goals of large projects are what they think they should be, rather than what they
actually are.  For example, in this project, we received constant feedback that we weren't
making enough project on breaking our business logic layer into services.  That was always
incredibly frustrating for me because in my mind, that was never our goal, and I felt like
it was bad for morale, distracting from the team, and basically a way for people to score
easy points against us.

But then I realized something: the reason people made up their own goals for the project
was because we had never told them in a clear and convincing way what the actual goals were.
It wasn't malice or politics, it was that people tend to assume their own thoughts are
what everyone else is thinking as well (see the [False consensus effect][falseConsensus]).
And the effect went both ways - I was assuming that because the goals were clear to me,
they must have been clear to everyone else as well.

I have seen and been a part of numerous projects that have stalled or failed because the
project driver was unable to articulate the goals in a clear or convincing way.  The only
solution I have found to this is to be as quantitative as possible.  When we first started
the splitting the monolith project, we argued endlessly about where it was best to split
things and into how many pieces and so on.  And all that arguing was basically useless,
because it was driven but our gut feeling and intuitions, which meant that even if it was
correct, we would never be able to come to consensus or convince anyone that it was right
because it would always be one person's intuition versus another.

We broke this stalemate by returning to the data: we looked at the most pressing issue we had,
which was the fact that our releases were too risky and introduced too many bugs.  We looked
through all our major customer impacting bugs over the previous year and identified what
investments would have prevented them.  We looked at our release pipeline and wrote down
what parts of it took the most time (thereby preventing more releases per day), and what
parts of the codebase needed the expensive checks and which did not.  Armed with that data,
it was completely clear how we had to break apart the codebase.  But more importantly,
we were able to set goals that were clear and quantitative, and tell a story about how
we would meet those goals that was easy for outsiders to understand and buy into.

I learned another thing about managing interactions with outsiders during this process:
how to deal with the what if? question.  Anyone who has worked on a big project has
experienced someone from another team coming by and making a vague, poorly thought out or
unactionable suggestion.  When I first started, this was my nightmare.  A single question
would take an outsider just a few minutes to ask, but could mean hours and hours of work
for me or the team.  Multiply that by the fact that there were many more outsiders asking
questions than people on the team doing work, and I basically cowered in fear anytime
someone would come over to ask about something.

My strategy to deal with these questions was terrible, but its something I see engineers
do pretty much all the time: I either explained to them that we were already doing it
or I argued with them about why it was a bad idea.  Not surprisingly, I never once saw
anyone be satisfied with either of those answers.  The first makes them feel stupid
because their great idea is already old news, and the second just makes them want to
argue more with me (and boy can engineers argue).  But slowly, over time, something hit
me: I was assuming that what people wanted was answer, but really what they wanted was
to feel heard and valued.  And what was great is that making them feel heard and valued
is actually a lot easier for me and more scalable for the project than giving them an answer.

Here is my new strategy whenever someone from outside the team comes to me with a suggestion:
First, I shut up, and I let them speak until they clearly feel like they've gotten all their
thoughts out.  Second, I repeat their suggestion back to them.  Lastly, I tell them a clear,
actionable plan of what
they need to do in order to get it adopted.  This might be do a proof of concept of their
architecture, or convince person X that this is a great idea, or write up a design doc.
What I definitely don't do is make any judgement of the idea.

Its hard for me to always follow this strategy (the urge to argue is still strong), 
but when I do, it is shockingly successful.  The
person knows they are heard - because I repeated their words right back to them - and this
makes 90% of people satisfied with the conversation.  There's no argument to be had because
I've only laid out process rather than made any judgements, and people are far more likely
to argue judgement that process.  There's no extra work for the team because all of the work
falls on the person making the suggestion.  And most importantly, the really dedicated people
will go out and do the follow up work and either convince themselves that its not a good idea,
or will have done the work to make the project even better.  Win, win!

[box]: https://www.box.com/careers/
[falseConsensus]: https://en.wikipedia.org/wiki/False-consensus_effect