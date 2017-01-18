---
layout: post
title: MirageOS Fortnightly IRC Call Feedback
---

As referenced in a [previous post](http://reynard.io/2016/11/01/MirageOSFeedback.html) I wanted to check in with [MirageOS](https://mirage.io/) community members to gauge current opinion about the fortnightly [IRC meetings](https://irclog.whitequark.org/mirage/2016-02-13), and to see if there were any positive changes we could make. The main focus of the questions was directed specifically at the meeting itself, and other more general MirageOS community questions that help gauge the sample and to see where respondents currently access MirageOS information.

The feedback poll was online and accessible for 6 weeks, and I received 16 distinct responses. As I chose to keep the results anonymous we cannot tell if those distinct responses represent distinct individuals, but the data provides a starting point.

## Generalisability to a larger population

It is a small sample size, so I do not wish to generalise the results to the whole MirageOS community - the sample is likely limited to core users and developers, and to those that already join or actively participate in the meetings. It is therefore important to bear this in mind when reading the following report. Feedback and suggestions relating to the fortnightly meetings are still of interest despite the small sample, as they provide specific insight from current users and apply directly to that context.

----

## TL;DR

### Overall Conclusions

* The call provides a way to check the current state of MirageOS projects and a time and place to get consensus on decisions
* Some respondents join the call but don't participate directly due to a self-identified lack of specific knowledge
* Summaries in addition to the logs would be helpful and will help create a rounded view of current projects alongside the mailing list
* Items discussed in the meeting appear to be appropriate and providing more structure would be a benefit
* The mailing list and #mirage IRC on Freenode are the most common areas the respondents access for MirageOS information

### Possible future actions based on feedback

* Continue with IRC for the fortnightly calls until a suitable open source alternative is available
* Post the [agenda](https://github.com/mirage/mirage-www/wiki/Call-Agenda) online (wiki and mirage.io?) 2/3 days prior to call
* More structured agenda - with additional background information for topics, and prioritisation of burning issues that require discussion/decision
* Follow up other discussion items regularly on the [mailing list](https://lists.xenproject.org/cgi-bin/mailman/listinfo/mirageos-devel)
* Call summaries alongside [IRC logs](http://canopy.mirage.io/irclogs)
* Publicise calls to the wider community
* Add more details of topics of discussion for participants to read before the call - linked from agenda perhaps?
* Provide documentation and tutorials for newcomers
* Set up a calendar invite for each call to encourage attendance
* Provide details of how to contribute to the call and to MirageOS itself - ensure [current information](https://mirage.io/wiki/contributing) is up to date

----

## Results

The results have been loosely categorised where possible (this refers to similar wording or similar concepts) - while this is not wholly systematic and relies on the conclusions I have drawn, it is useful data when considered along with the sample size and background of the respondents (see Q1 of the general Mirage questions below). Please do study the data and come to your own conclusions - then let me know!

Thanks to everyone who participated - your feedback is extremely valuable! Please continue to tell us your thoughts and suggestions by emailing the MirageOS [mailing list](https://lists.xenproject.org/cgi-bin/mailman/listinfo/mirageos-devel) or feel free to [contact me](http://reynard.io/about/) directly.

## MirageOS Call Questions

16 respondents for most questions, stated next to the answers.

### 1: Do you join the fortnightly calls?

* Yes: 8/16
* No: 8/16

### 2: If you answered no, please explain why.

* N/A (these people do attend): 6/16
* Conflict (timezone/work/family): 6/16
* Unsure of schedule: 2/16
* Dislike IRC: 1/16
* Prefer async communication: 1/16

**NOTE: 2 of the respondents who previously said they attended also provided reasons for not joining.**

**Conclusions**

Of those not who do not join the call, just over half (6/10) stated that the main reason was due to a timing conflict of some kind, including other work, family and timezone.

**Actions**

Personal preferences, timezones and conflict constraints are out of our control, but ensuring that the call is scheduled at a regular time each fortnight and scheduling details are available in obvious, public places may encourage further participation.

### 3: Do you feel able to participate in the call?

* Yes: 10/16
* No: 6/16

### 4: If not, why not?

* N/A: 12/16
* Lack of knowledge: 3/16
* Distraction/concurrent discussions: 1/16

**NOTE: There may have been some confusion here - I should have made this clearer that it should be those who usually attend the call feel they can participate, not those who would not usually attend. Perhaps the following wording would have been better: "When you join the call do you feel able to contribute your ideas or questions?**

**Conclusions**

Of those respondents that provided an answer, the majority said they did not feel able to participate due to a lack of MirageOS or OCaml-specific knowledge. It is difficult to determine if this is wholly negative - perhaps people feel less involved due to a lack of knowledge, or perhaps they prefer to listen to others who do know more.

**Actions**

This point warrants further discussion, but one area of focus could be to ensure documentation, tutorials are up to date and prominently displayed on [mirage.io](https://mirage.io/), along with more details of current MirageOS users and projects for members of the community to explore between calls.

### 5: What is the main value of the call for you?

* N/A: 2/16
* Get up to date: 8/16
* Synchronous decisions: 6/16

**Conclusions**

Of those that didn't answer 'N/A', the majority (8/16) of respondents value the call as a way to check the current state of MirageOS projects (although one did say that high-level issues should receive more focus), with the remainder stating that having a significant number of core developers and users in one (virtual) room for synchronous agreement on issues was valuable.

**Actions**

Respondents says continue! The calls provide a sync point for decision making and allow community members to keep up to date with activity. Ensuring that the agenda includes items requiring discussion and decision would be appropriate based on this feedback.

### 6: Do you feel that the call addresses appropriate items of discussion?

* N/A: 3/16
* Yes: 11/16
* Unstructured: 2/16

**NOTE: Of those who answered yes, there were some caveats: Sometimes the content is highly technical and difficult to follow, especially for newcomers; the content is generated by those intending to attend and casting a wider net for discussion might be beneficial.**

**Conclusions**

The majority of those who answered feel that the items discussed are appropriate, bearing in mind the above notes. It looks like we are discussing the right things, and providing more structure would be a benefit.

**Actions**

Rather than making the discussion less technical, we could provide more background to proposed agenda items before the call for people to refer to. Regularly looping back and highlighting where specific projects, features and issues sit in the MirageOS ecosystem would be relatively easy to do, and might target this concern. Based on the answers from Question 5 above, deciding which burning issues should be addressed in the call and which items are for wider/more general discussion (such as roadmap items, feature wish-lists etc) on the [mailing list](https://lists.xenproject.org/cgi-bin/mailman/listinfo/mirageos-devel) or via [Issues](https://github.com/mirage/mirage/issues) would be a benefit.

This links to repository management and organisation - specifically providing information on how to contribute, and a process by which topics are discussed, decided upon and re-visited if necessary. My [post](http://reynard.io/2016/12/13/OSSWorkflow.html) about using GitHub features and tools for repository management outlines our experimentation with providing public roadmaps, monitoring ongoing project progress and encouraging wider discussion through community empowerment.

### 7: Currently we use IRC to conduct the call/chat. Do you use IRC for other channels/chats?

* Yes: 12/16
* No: 4/16

The majority of respondents use IRC for other purposes.

### 8: What would be your preferred platform for Mirage call?

* N/A: 1/16
* IRC: 11/16
* Slack/Discord: 2/16
* Video: 1/16
* No preference: 1/16

**Conclusion**

The majority of our sample have a preference for using IRC for the MirageOS meetings for reasons such as low overhead, easy to stick to an agenda, easy to join mid-way through, and can follow up with logs/minutes (if available). [Slack](https://slack.com/) or [Discord](https://discordapp.com/), mainly due to a nicer UI, with one stating a strong preference for an OSS version. One person prefers video calls, but acknowledges that most video call software has problems.

It is worth noting that [ReasonML](https://github.com/reasonml) from Facebook have an active public channel on [Discord](https://discordapp.com/channels/235176658175262720/235176658175262720) - it would be interesting to find out what their team have found most valuable from using it as a Platform.

**Actions**

Responses suggest we should stick with IRC for now - if an OSS version of a platform such as Slack appears, then there will be the option to switch (if it is reliable).

### 10: If you could make one improvement to the call what would it be?

The main suggestions for improvements in descending order were:

* N/A: 2/16
* Put the agenda up sooner: 3/16
* Provide a summary of the call along with the IRC logs: 2/16
* Advertise to and encourage a wider group of people to join the call: 2/14
* No improvements, it's great as it is!: 2/14
* Provide a calendar invite: 1/16
* More structure (no further details provided): 1/16
* Use the mailing list for support and questions, not the call: 1/16
* Improve the flow of conversation: 1/16
* Change the time and day: 1/16

### 11: Do you read the IRC call logs?

* Yes: 10/16
* No: 4/16
* Didn't know they existed: 2/16

### 12: Do the IRC logs provide a good overview of current MirageOS projects?

* N/A: 5/16
* Yes: 6/16
* Yes but additional summary needed: 3/16
* No: 2/16

**Conclusions**

Of those who read the logs (didn't answer N/A), the majority agree that they provide a good overview of the current projects. A summary in addition to the logs would be helpful - the logs are not particularly easy to skim or quickly read. One person did suggest that if you weren't on the mailing list or were new to the community the logs don't provide a good sense of the project as a whole.

**Actions**

Making the location and existence of the logs more obvious and figuring out a way to add a call summary to accompany the logs would be beneficial.

### 13: Anything to add?

We had 6 further responses, with 5 people saying that the community is great and they value being part of it and to keep up the good work, and 1 person saying simply "IRC is great!".

----

## General MirageOS Questions

These questions and responses have less to do with direct actions, but provide insight into our community and its members.

### 1: To what extent do you use MirageOS?

Respondents self-identified as the following:

* Experienced MirageOS developers: 6/16
* Interested parties: 6/16
* MirageOS users: 2/16
* None of the above: 1/16
* Developer of other unikernels: 1/16

### 2: When did you first hear about MirageOS?

* At inception!: 5/14
* MirageOS release: 2/14
* The OCaml community: 2/14
* Talks/presentations on MirageOS: 1/14
* The OSS community: 1/14
* Unikernel news: 1/14
* Reddit: 1/14
* A friend: 1/14

### 3: Where do you find answers to your MirageOS questions?

The majority of responses included a combination of the following, so I've created a tally instead.

* Mailing list: 7
* IRC: 6
* Slack: 3
* Personal enquiries: 3
* GitHub: 2
* Source code: 2
* Blogs 2
* Mirage.io 1
* Google 1

**Conclusion**

The mailing list and #mirage IRC on Freenode receive the most hits from this particular group.

### 4: Do you find the MirageOS mailing list helpful?

* Yes: 13/15
* No: 2/15

### 5: If not please elaborate why.

**NOTE: Only 3 responses to this question.**

* Traffic on the mailing list is sporadic
* Dislike of mailing lists
* No context
