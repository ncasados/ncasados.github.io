---
title: "Looking Back on my 2024 Job"
date: "2025-03-08 08:00:00"
thumbnail: "/assets/img/thumbnail/looking-back-1.jpg"
---

Just some thoughts on the start of this year and reviewing the last year.

# The Year So Far
Well, today I am unemployed again. I've been unemployed again since January of 2025. This time I had done a lot better because I had managed to save a little bit of money and I had learned so much about being an engineer while at my last employer.

For the most part, I had always done development by myself. Which honestly, being the solo developer with no one reviewing your code really sucks. You're unable to address bad habits that other more senior developers would notice quite quickly. While I was at my last job, I found myself submitting PRs that usually went through tons of revisions before it was finally accepted and merged. Each PR required tests and my contemporaries were great at helping define tests. Overall, I think learning testing and this kind of code review was good.

I had also learned some other things about running a system well. There was telemetry built into the application that would send back to another system metrics about how the system was behaving. We could define in a module a span function that would create a span log in the system with whatever metadata we could think to put into it. I appreciated this a ton when debugging something.

I think where I struggled most while working here was understanding fine details for a PR. It feels like writing English but people having different ways of constructing those same English sentences. For example, where I might have piped a few `|> Map.get` I had learned from my then boss that I could use a `get_in` and use much less pipes.

I remember one of my last tasks was to put together something that would delete the child records of a parent record in our database. I had implemented this using a transaction which would rollback the database deletions if something went wrong. However, my boss was disappointed that I had not implemented it where it would just delete things and the transaction was not necessary. The one thing that was important was that the parent object be deleted last.

I think it was carrying out small details like this where I had struggled. The boss had thought of one thing when he defined the tickets he wanted. Sometimes they were quite short, but that's fine. I'd just ask for more detail later. But when getting the final implementation down, the way I had did things just never seemed to be quite right. I only had a few PRs where there were not much needed to be changed.

I'm not entirely sure if this is normal for the industry. I guess if it is, this makes for what I feel like is kind of a shitty industry. Inb4 people tell me to get good, I know.

As I see it though, it is hard to get good without a community and people around you who actually care about your growth. In my life, I've only known maybe 1 or 2 people who are actually concerned with seeing my growth and they aren't family. At work, coworkers are okay with you growing as long as it's within the same priorities of the business too. I think if you're growing slow, you'll get kicked to the curb.

So, since it's hard to have a community as a lone developer on their own, I've kind of been thinking about putting some serious work into building out a YouTube channel. I've been doing all kinds of different things through my life and could teach people all kinds of different things. As it would turn out too, I had put together a video a while ago teaching how to use the GitHub API with Elixir. Since 2021, it's gained 1000 views which is meager but certainly alright.

I'll bet I could put together more videos teaching topics on Elixir. I'll bet they could do decently well. I could probably spent plenty of time talking about other technology topics and have a good time of it. We'll see. The point though is that I could build some community around videos where I share the value of my knowledge with others and maybe others would share the value of their knowledge with me.

# Thoughts On The Elixir Job Market and Software Job Market
This job market sucks.

There are not many jobs in the market and I've started to conclude that in order for there to be more jobs in this space, someone must create jobs in the space. I think I should be someone who is making jobs for others to work but I have no capital and nothing that's solving a problem for anyone.

Because of how bad this market is though, it has me thinking about taking up work in other languages. However, I've had one hell of a time interviewing with my next best language, JavaScript.

It feels like the software engineering industry and IT as a whole feels like the most "Dark Souls" of all of the job fields. You need to test into every job. In software engineering the tests are much more straightforward, although one might get some assignment with vague requirements; so a hiring team can reject it later, I'm sure. But even for IT jobs, I've been asked a bizzare question about, "I'm asking you to cut a pizza, how would you cut the pizza?" and what this interviewer was looking for was if I'd be wondering if the pizza is for a party or not.

It feels like the requirements for any particular job just aren't clear and I have started to feel like this field just is not something for me. Despite all of the effort I've put in, I don't think I'm great at recalling information with the accuracy required of passing interviews and surviving in the workplace.

With how the market place has a lack of junior positions and it doesn't seem there are companies looking to hire people and help them learn and grow, I think I might just try something else. However it's leaving me feeling like if I were an online game character, I'm maxing into being a super novice.

Lately I've been wondering if I'll do okay with sales. I like talking to people and if I'm selling a product I really believe in, I think I can do well talking about it.

Well anyways, thanks for reading.
