---
layout: post
title: Summer 2019 @ Facebook
permalink: /summer_2019_facebook/
---

I've never written a blog post before but I'm writing this for two reasons:
1. To provide an account of my experiences for anyone interested in similar opportunities
2. To record this while I still remember it and have something to look back on a year from now when I have no memory of any of it

This summer I worked at Facebook Seattle as a Production Engineering Intern. I was a member of the Traffic team, which is responsible for handling and routing all the requests to Facebook servers and managing the networking infrastructure (which is *massive* - more on that later). Every time you open your app, tap that meme, tag your friend - all of that flows through us.

## Seattle

I picked Seattle as the location for my internship. If I'm being honest, there were times I regretted this - I felt like there were things I was missing out on because I wasn't getting the "HQ experience". However, when I look back on it, I think Facebook's Seattle office (the biggest office after their headquarters in Menlo Park) was a much, much better environment for me to work in and learn from. The number of people was significantly fewer than the relatively crowded MPK office and as a result I grew closer to a fewer number of people, instead of being utterly lost.

As a city, Seattle has the best of both worlds:
- A rising tech city, Seattle houses Amazon and neighbors Bellevue/Redmond which are all Microsoft land. Facebook, Apple, and Google are locked in a construction race, each one trying to spring up new offices quicker than the other.
- It is surrounded by some of the most picturesque nature in the country. There are snow capped mountains, lakes and glaciers, all less than a couple hours away. During the summer, the government runs a special bus route to reach the plethora of hiking spots in and around the area. I hiked up some of the steepest hills and around a (fortunately inactive) volcano. I saw waterfalls, lakes, a variety of trees and threw a very icy snowball - a very different experience from looking at various species of dead grass stretching for miles in every direction (*cough* Mission Peak).

{% include image.html url="/images/personal/office_view.png" description="View of Lake Union from the office" %}
&nbsp;

{% include image.html url="/images/personal/rainier.jpg" description="Mount Rainier" %}
&nbsp;

Plus, Washington no state income tax, so keeping more of my money is another plus. Unfortunately, Seattle has very few good bubble tea places.

## General thoughts and random facts

I'm putting this section up here in case you don't have the patience to read the whole thing (I don't blame you). These are a few interesting things that I found, presented in an organized list, because lists are better than paragraphs.
1. People are super super friendly. You can walk up to or message anyone in the whole company, and they would be more than happy to help you with whatever bug you have, teaching you what they know. The amount of learning you can do just by talking to people is huge (one of my regrets - not talking to enough people)
2. People know their stuff, and they know it well. We went out to a team dinner once, and a guy on my team started talking about the answer to the classic question "What happens when you type www.facebook.com (replace with any other website) into the browser and hit enter?" (the topic of conversation was interviews).
<br/><br/>
We had to forcefully change the topic of conversation 45 minutes in, by which time he had only reached the initial DNS lookup request produced by the browswer.

3. They have a very open culture - everyone has access to the entire codebase (excluding user data of course), which I found immensely useful. I was allowed to view and modify the code used by every Facebook service - WhatsApp, Messenger, even Oculus. I find this culture really useful and important for a company which focuses on moving fast and growing; too many useful changes would otherwise be bogged down in bureaucracy and the like.
4. Mark Zuckerberg has far less code committed to the codebase than the average employee (including me), and even he got roasted like crazy on PRs, so I guess there's hope after all
5. The machine I worked on had 64 cores and more than 100 gigs of RAM. w o w

## Facebook - a technical perspective

Wow.

People toss around the term "big" and "huge" when referring to "tech companies" like Facebook, Google, etc. But only after I joined and got a chance to explore some of the codebase did I really understand what that means. The scale at which Facebook operates is enormous - they maintain around 4 million servers, and by the end of 2020 are aiming to more than double that number. The challenges of operating at this scale are unlike anything someone would normally encounter during any development on their own; there are multiple layers of automation and tooling for every service, and the disaster recovery abilities of teams are constantly tested through efforts such as [Project Storm](https://www.forbes.com/sites/roberthof/2016/09/11/interview-how-facebooks-project-storm-heads-off-data-center-disasters/#570af4c14875), an effort wherein an entire data center is randomly shut down, redirecting all traffic to the other centers and thereby stress testing the servers.

The team I was on, Traffic, handled a peak egress of around 90 terabits. Tera with a T. To put that into perspective, that's around 28,000 HD movies being handled per second. 5 years of non-stop Chris Tucker and Jackie Chan action ([Rush Hour](https://www.imdb.com/title/tt0120812/) is objectively one of the best movies ever). Keep in mind that this is every second, so it would only take about 10 seconds to hit about 1 petabit of egress. Every second, the entire fleet of computers across the world has to handle all these requests without fail, automatically directing traffic to healthy servers with capacity. If a single link in the chain fails, the bottleneck produced would be monumental without safety mechanisms in place.

I was specifically on the Proxygen team, Facebook's L7 load balancer - a part of this project is OSS and can be found [here](https://github.com/facebook/proxygen). My project involved producing tooling to build Proxygen binaries asynchronously and in parallel, and allow automatic regression detection in case things go south. In other words, if there were errors in the binaries, my tool would automatically find where exactly the issue was introduced, allowing quick debugging when time is of the essence. The entire thing was 100% Python, with a touch of Hack, SQL, and Bash.

## Production Engineering

Fancy, right? Sure sounds a lot cooler than sOfTwaRe EngINeeRiNg.

To be honest, there is only a subtle difference. I applied for PE because I imagined it to be more systems and low level oriented work, which is my focus. To an extent, this was true, but do not associate PE with rearranging x86-64 instructions and manually flipping 1s and 0s to produce performance gains. In some teams, this may be true, but your work is largely team based.

So what exactly is the difference then? The best way I can think of describing it is: SWEs are responsible for writing the code that runs on machines. PEs are responsible for the glue that binds various services and machines together, for scaling these machines, and for ensuring the robustness of the infrastructure in general. PEs at Facebook follow an on call schedule - if something related to their team goes down, the fact that it's 4am or a Sunday night doesn't matter. The moment the on call is paged, they have to work as quickly as possible to bring the service back up and running. Every second the site is down, the company loses millions of dollars in ad revenue, so bringing it back up is of utmost importance.

My personal experience was that PEs were more knowledgeable of exactly how things work - they feel uneasy accepting black box functions or services that "just work", and need to know exactly what is going on at every stage. Useful skills for a PE include a good understanding of Linux/UNIX, Bash scripting, and developed debugging skills. Definitely the debugging skills.

## Facebook - a social perspective

Now for the fun stuff. Facebook really does their best to spoil an intern. This is a non exhaustive list of all the benefits we received and events hosted for us:
- Breakfast lunch and dinner from multiple cuisine options
- Q&A sessions with Mark Zuckerberg and Sheryl Sandberg
- A cruise to a private island rented out for us, where there were events like kayaking, paddleboarding, etc
- Weekly game night with snacks, board games, and a Nintendo Switch
- A Build-A-Boat event where we were challenged to create a boat out of cardboard and wooden sticks. Our team's sank after a grand total of 4 seconds in the water
- Beach day at a beach nearby (I didn't attend, not a huge fan of beaches)
- Movie nights and other spontaneous social events scattered throughout the summer
- Lots of swag (11 shirts/jackets at last count)

{% include image.html url="/images/personal/cruise.jpg" description="A boat cruise with a view of the Space Needle" %}
&nbsp;

## Conclusion

Will I return? Maybe. I can't think of anything I didn't like about my experience, but I would stop short of calling it a "life changing" one, or one of the "most amazing" experiences I've had. I liked my work, I liked the company, and I loved the treatment we received. Summer is a time of exploration though, so I'd like to try something different next year.