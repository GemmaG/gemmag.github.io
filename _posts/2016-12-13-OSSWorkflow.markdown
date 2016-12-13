---
layout: post
title: OSS Repository Maintenance and Management
---

I am new to open source maintenance and management, and my position at OCaml Labs is operational rather than technical. It's important for me to grasp the general idea of a project enough to see how it fits within our larger goals, and then help it move forward without administrative blockers. Figuring out how I can fit in this highly technical environment has been interesting and challenging (that's a whole other post!), but I've recently implemented a few changes that (I hope) will start to positively impact our projects and our research.

## Motivation

Keeping track of administrative details and the ~40 projects our distributed team is working on requires a consistent approach to reduce the likelihood of tasks being dropped, stuck in a bottleneck, or lost in the noise. Our projects are highly collaborative and receive input from developers, students, researchers and support staff - we need a method of maintenance that promotes this direct interaction and goal-oriented development.

## My Workflow

I started by looking at my own daily tasklists to explore how I might manage them more efficiently, then chose one of our internal projects that might be applicable for a similar process.

I've tried many methods of to-do list management, including:

### Ye Olde Paper & Pen
I can write pages and pages of lists, but there is little organisation to it and my scrawlings are not always legible to others. I still use a scribble pad to jot down the individual tasks I need to complete that day - physically crossing off items on a list is always satisfying! - but carting around a messy, poorly organised notebook to and from meetings is not especially helpful for sharing progress and interacting with colleagues.

_**UPDATE: I have succumbed to maintaining a bullet journal! It is no longer a messy, poorly organised notebook, and is the perfect complement to my online workflow**_

### Inbox To Do List
I must confess that my inbox was managed rather appallingly until recently. Although I dealt with important or time-sensitive emails quickly I seemed unable to decide on a strategy for managing emails that were a collection of useful details, or decisions that I would need to make at some point in the future - all of the non-immediate tasks. I tried using my inbox as a todo list by using Gmail labels, but that quickly got out of hand and I ended up just avoiding looking at my email, missing the entire point! It's also very easy to unintentionally filter out important conversations, especially if every query or pending decision is part of a long, in-depth thread.

### [Kanban](http://kanbanblog.com/explained/)
Hello [Trello](https://trello.com/)! I found this idea worked for the most part, but I couldn't get everyone to join Trello and interact with my board, which meant overall it was not useful and got abandoned. I liked the idea of having a process that individual tasks pass through - the standard set-up is "Todo", "Doing", "Done", or similar variations - and clicking and dragging cards between columns is helpful. Perhaps I could apply this principle elsewhere?

### [GitHub](https://github.com/)
The majority of developers on our team use GitHub to release code and maintain our open source repositories, so this seemed like a useful place to start. I wanted to try implementing a management workflow within an existing structure to increase the likelihood of long term adoption and success. Initially I looked at the myriad of project management extensions and apps that have been developed as plugins for GitHub, but I was keen to avoid the Trello problem we faced when using another external application. Fortunately GitHub released their Projects feature around this time, and this together with using Labels and Milestones addresses most of my needs directly.

### GitHub Issues, Labels, Milestones and Projects

[Issues](https://guides.github.com/features/issues/) are essentially tasks, and can be organised as bugs or todo items depending on the type of project. All members with access to a repository will be able to view, create and comment on Issues. Colour-coded [Labels and Milestones](https://guides.github.com/features/issues/#filtering) allow you to further manage your Issues, and assign them to specific individuals and timeframes.

GitHub Projects aim to apply the Trello/Kanban management style to repositories, and I experimented by using them in conjunction with my Issues. Any Issues that are created in a repository are available to use directly within a Project. You can add them to one or more active projects, and progress them through your workflow as you see fit.

_**It is worth noting that in this administrative repository all of the Issues are created as todo items, which is slightly different to a standard repository featuring code - here Issues are added to highlight a problem or bug, and don't necessarily represent a todo list as such.**_

The approach I currently use is also slightly different to the usual Kanban method in that my columns represent tasks I need to complete "Today", "Tomorrow" "This Week", in the "Future" as well as a "Completed" column on the far side.

This process allows me to prioritise my todo items and for anyone on my immediate core team (those who have access to the repository) to see exactly what I am working on at the moment, the state it is currently in, and what is next on my agenda/workflow. I move issues/cards between the columns and update comments on them to provide incremental updates on the topic itself. I have given permission for my immediate team to also add issues to the workflow management process on the basis that they use it in a similar way - essentially it is a shared todo list that is updated on the fly.

**Example process:**  

**1:** I create an Issue for "Create a list of internship projects for 2017". Everyone who has access to the repository will be able to see that is a current Issue

**2:** Under Projects, I click through to the Project entitled "Gemma's Workflow" and click "+ Add Cards" on the top right. A drop down menu of all Issues appear, and I can drag the one I need into the column that is most appropriate, for example "This Week"

**3:** Everyone can see from this overview that I would like to address this task at some point within the next week  

**4:** I add a description with some details of what we need to do, and @ someone on my team who I want to check it over next

**5:** They can see the Issue, add a comment, move the Issue around within the Project workflow, or close it if complete

Everyone can see the current status of the todo task, and it is easily passed between team members whose input is required. The vast majority of my team is on GitHub regularly, so items are addressed in a timely and effective manner - if one person is blocked, it can quickly and easily be redirected.

The combination of Issues, Labels and Milestones together with the prioritisation in the Projects workflow has so far been very useful for my workflow, but I was interested to see how we might apply it to our code-based open source projects.

## Applying this workflow to the Merlin repository

[Merlin](https://the-lambda-church.github.io/merlin/) is an editor service that provides modern IDE features for OCaml. It is maintained by [Frederic Bour](https://github.com/let-def) and [various contributors](https://github.com/the-lambda-church/merlin/blob/master/README.md) and relies on community support.

The workflow application to Merlin is still a work in progress, but Fred and I collectively are looking at the most applicable labels, and looked at how we might use the Projects method in this case.

New project features tend to go through the following process:

* Idea/discussion
* Build
* Test
* Documentation
* Release
* Manual testing/feedback

The Merlin Issue tracker was initially arranged in the basic format that GitHub suggests: Labels such as "Bug" and "Feature request" were present, but as time progressed, some issues were pushed to the bottom and left unresolved.
We decided to represent the above stages of development as Labels, and now ensure that each issue goes through this process to avoid losing track. Thanks to the [Docker for Mac and Windows](https://github.com/docker/for-mac/labels) repository for inspiration!

[Area/Emacs](https://github.com/the-lambda-church/merlin/labels/Area%2FEmacs): Related to Emacs
[Area/Vim](https://github.com/the-lambda-church/merlin/labels/Area%2FVim): Related to Vim
[Kind/Bug](https://github.com/the-lambda-church/merlin/labels/Kind%2FBug): This issue describes a problem
[Kind/Docs](https://github.com/the-lambda-church/merlin/labels/Kind%2FDocs): This issue describes a documentation change
[Kind/Feature-Request](https://github.com/the-lambda-church/merlin/labels/Kind%2FFeature-request): Solving this issue requires implementing a new feature
[Kind/To-discuss](https://github.com/the-lambda-church/merlin/labels/Kind%2FTo-discuss): Discussion needed to converge on a solution; often aesthetic. See mailing list for discussion
[Status/0-More-info-needed](https://github.com/the-lambda-church/merlin/labels/Status%2F0-More-info-needed): More information is needed before this issue can be triaged
[Status/0-Triage](https://github.com/the-lambda-church/merlin/labels/Status%2F0-Triage): This issue needs triaging
[Status/1-Acknowledged](https://github.com/the-lambda-church/merlin/labels/Status%2F1-Acknowledged): This issue has been triaged and is being investigated
[Status/2-Regression](https://github.com/the-lambda-church/merlin/labels/Status%2F2-Regression): Known workaround to be applied and tested
[Status/3-Fixed-need-test](https://github.com/the-lambda-church/merlin/labels/Status%2F3-Fixed-need-test): This issue has been fixed and needs checking
[Status/4-Fixed](https://github.com/the-lambda-church/merlin/labels/Status%2F4-Fixed): This issue has been fixed!
[Status/5-Awaiting-feedback](https://github.com/the-lambda-church/merlin/labels/Status%2F5-Awaiting-feedback): This issue requires feedback on a previous fix

We are using the [Project](https://github.com/the-lambda-church/merlin/projects/1) area as a scratchpad to note future work and 3 month roadmaps, by having a column assigned to each upcoming month in the quarter. It's easier to update than a normal list in the repo Wiki and you can quickly edit and move cards between columns. Currently there is a disparity between the roadmap and the actual issues - it will take some time working with it to see what works best.

Checking in with the Issue tracker regularly is key, and we have updated the [README](https://github.com/the-lambda-church/merlin/blob/master/README.md) to reflect the new management process to provide clarity, and to encourage others to contribute in specific ways to help the project. These changes align the desire to efficiently manage our shared repositories with the aim of encouraging and acknowledging contributions to the projects. We will further test and refine this process with other repositories that we manage and projects to see what works.

## Conclusion

After some research with different approaches we are experimenting with using a combination of GitHub Issues, Labels, Milestones and Projects to manage our open source project workflow management.

### Benefits
* Collaborative: Use the @ function to directly involve others in the conversation. This is good for specific queries or for when you need to ping that person to engage with the task - they will receive a notification and can respond appropriately.
* Potentially reduces the number of meetings you will need to have: We have been able to reduce the number of admin sync meetings we need to have as incremental updates on the Issues and the overview from the Projects area provides a good snapshot of what is happening currently and what is planned next. We have yet to see if it will do the same for other repositories...
* Works well with a distributed team: It is utilising a tool already in use in the daily life of our team, and is an effective alternative when you can't have a physical meeting or call.

### Some problems

* Difficult to link the larger roadmap plans with individual issues/todo items: Still difficult to assess progress based on goals.
* If you don't have one large mono-repository, you cannot have Labels and Projects linked across repositories: You have to set up a workflow management system on a per-repository basis which does little to improve the organisational overview of ALL projects.
* Assigning Issues to more than one individual at any one time simply creates noise and reduces clarity: Stick with one assignee at a time.
