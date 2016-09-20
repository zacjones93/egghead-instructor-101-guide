## Creating Courses

Courses are what people truly love to watch. Humans desire information in chunks. They want to learn a topic in depth, but at a pace that works for them.

For egghead, courses are the natural extension of the individual lesson. A course is a composed set of bite-sized lessons. The course itself should be bite-sized, covering a single topic in depth through a sequence of individual lessons.

## Lesson Autonomy

Within a course, **each individual lesson should be as autonomous as possible**, covering its own individual topic as independently from the other lessons in the course.

:zap:** each lesson in a course should stand on its own as much as possible**

Tightly coupling lessons to a linear sequence is something we want to avoid with egghead.io courses. A student should be able to drop into any lesson in a course and learn a concept.

> I have to provide context! The example is built step by step. The student will be confused.

This is a fair statement, but we are going to consider an alternative approach. Instead of speaking to the user about the context we will **provide context around the video within it's HTML page the user is watching it on**.

A course will include:

* a list of all the other lessons in the course

* a robust summary that can include links to pre-requisites and otehr resources

* course notes in the form of a gitbook the community can build together

* an "enhanced transcript" that assembles all of the transcripts for a course into a usable document that allows the user to read the entire course as a book
* the code is provided with each lesson representing its current state and has a readme describing how to execute the code if it isn't in a Plunker
* individual lesson summaries with links, etc...

If you consider this context that the user is supplied, it makes the automous course within a lesson much easier to realize. We don't have to provide audio describing the context. Avoid saying "in the previous lesson" or "in a future lesson" - just get right into the concept of the lesson you are currently teaching! It makes a much nicer course that is more concise and allows for modular learning with minimal confusion.

## Course Styles

egghead.io courses have several styles. The most important aspects of a course are focus and high quality examples. If you have those two things, the style doesn't matter. It definitely helps to have a plan though, and the following are excellent places to start.

* **Documentation**: This is straight forward presentation of the documentation for a library, framework, or tool. Dan Abramov's [popular course on Redux is a good example of this](https://egghead.io/courses/getting-started-with-redux). This doesn't mean you should simply read the docs to the student. Instead take the docs and present them with high quality examples.

* **Project Based**: Another favorite is a project based approach. In this case we start with a project that the student will build from start to finish. John Lindquist has [done this with his Time Machine example app](https://egghead.io/courses/building-a-time-machine-with-angular-2-and-rxjs) using Angualr 2 and ngrx\/store.

* **Cookbook**: You can also present a series of problems and solutions in the "cookbook" style. A typical recipe will include some common \(or maybe not so common\) problem, and then provide an example solution for the problem using the tool the cookbook is discussing. Trevor D. Miller's [React Testing Cookbook](https://egghead.io/courses/react-testing-cookbook) is a solid example of this approach.

* **???**: You're smart and creative, and definitely not limited to any of the above. If you've got an idea, let's hear it!



## The Course Proposal

For every egghead course we request \(and require\) a written proposal before the course starts production. We ask for proposals for several reasons. To make sure a course is solid, and delivers a ton of value to your students making the proposal lets us think more deeply about the content and structure of the course. This approach allows us to define the intent of the course, as well as craft [great titles](/02-creating-lessons/ideas.md) for the course and its lessons.

[Here is an example of a course proposal](https://docs.google.com/document/d/1goXtI_zmSfXTgaimrxIss356DoedPRt5MMAySs1f-bE/edit), and here's [a blank template](https://docs.google.com/document/d/1x5_UehD9mM2jeCtlqEZFy3epDLLmbgBBGCow5fDRNCc/edit#) for you to use.

**We strongly prefer to use Google Docs for proposals to facilitate collaboration! **The document should be shared with your mentor and other reviewers for feedback.

The proposal consists of 4 parts:

* User Story
* Goals
* Summary
* List of Lessons

We'll take a look at each of these parts in more detail.

### The User Story

At the top of the course proposal is a "user story". This is similar to the agile software practice of writing a story to describe **who**, **what**, and **why** we are creating this thing.

> As a _developer_, I want to build applications with React and Redux so that I can create applications that aren't littered with state.

### Goals

The second section of the course proposal consists of a list of goals for the course. What are we trying to teach? Why are we teaching it? What knowledge should the student walk away with?

### Summary

The course summary is a paragraph or two that describes the course, goals, technology, etc. This will generally be preseneted with the course on the website, so it should keep that in mind.

### Lesson List

Finally, we have the actual list of lessons that will be in the course. The list consists of **lesson titles and summaries** for each individual lesson. The title should follow [the "how do I..." format](/how-do-i), and the summary should summarize the goals and technology that the student will learn about in the lesson.

## The Examples

Often a course has an example that is used as a connecting thread through each lesson. Course examples should be built as soon as possible and shared for discussion. Depending on the style of the course, different example formats are more appropriate for different styles. When possible, we want to use a tool like Plunker for creating and delivering our examples. It is awesome to get the user into the code as soon as possible.

For each lesson in a course, the example will be provided in the **finished state of the lesson**.

Often it just isn't feasible for the example to be delivered in a Plunk. In those cases, we will generally prefer to use a Github repository to store the example code. Github repo examples will provide a **branch for each lesson**, where the branch is the completed state of the given lesson. If your course is the "cookbook" style and uses Github, you can just have folders in a single repo for each example.

## Recording the Course

With the prep you've done above, a lot of the hard work is done for creating a course. You can iterate on paper and build a solid curriculmn that will be useful for thousands of developers for years to come. Once your proposal has been reviewed and approved, you can start recording the lessons and uploading them as you finished.

If you haven't, we recommend you read [the section on creating lessons](/02-creating-lessons/create-lessons.md) to get more details on recording screencasts. A course is a series of lessons, recorded one by one. It's like stacking bricks.

## Maintaining the Course

"JavaScript Fatigue"

You've probably heard of this. Well, it affects egghead.io courses. Video is a tough format, and because libraries move at a brisk pace and forward progress is always happening, we are presented with some specific challenges in terms of keeping courses up to date and usable.

We make a very strong effort to keep your course as viable as possible for as long as possible.

There is a team working every day to review egghead.io courses and make sure that the code and examples are current and still work. The review team reviews the lessons on egghead.io, and makes sure that they still function with the latest versions of the tools described in the lessons. They update the code and attach version labels to help students understand the differences between the lesson video and the code.

This approach is very effective! There are times, however, where courses need to be updated. The review team will monitor and inform you of this when it occurs. We also tend to see a lot of questions and support requests around courses that have become out of date. In some circumstances, courses that aren't updated get retired.

It's in your best interest to keep your course updated when needed! It's a pain, but if you do the math, it is completely worth it.

