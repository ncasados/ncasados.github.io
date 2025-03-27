---
title: "The End of March, Looking Forward to April"
date: "2025-03-26 18:00:00"
thumbnail: "/assets/img/thumbnail/how_does_video.png"
---

In my last post, I talked about maybe trying out tutorial video production—and honestly, I’m having a nice time with it. Like anything new, though, there have been plenty of challenges.

## What's Been Happening

It’s the end of March, and while I didn’t land that sales job, I *did* pick up a temporary gig canvassing for a local political activism group. I’m actually looking forward to it—it pays well, and I think it'll be a good experience overall. Definitely going to need some sunscreen and decent clothes, though. Talking to strangers and getting signatures is the game plan, with a target of 60 signatures and a 65% validity rate. From what I hear, success just depends on being in the right places and talking to as many people as possible.

I joked with my barber recently about it—how I’ve definitely told signature collectors to “buzz off” before, and now I’m the one who might get told to buzz off. Karma, huh? We laughed about it, but it’s a good reminder to stay humble and give it my best.

## Video Production Adventures

On top of canvassing, I’ve started spinning up the ol’ video production machine again. You’d think I’d be more seasoned by now, given how often I’ve kept my setup ready “just in case.” But getting back into it reminded me just how tricky the whole pipeline can be—especially on Linux.

I’m using OBS (pretty much the go-to for screen recording), but on Linux it didn’t come bundled with some of the plugins I needed. And while Kdenlive is available for editing, it’s not very GPU-friendly or particularly robust. DaVinci Resolve, on the other hand, is a powerhouse—but getting it to run on Linux is a whole journey on its own.

## OBS, Plugins, and File Types

One lesson learned: *Advanced Scene Switcher*. It’s an OBS plugin that automatically switches scenes based on the window you're focused on. Super useful when you’re bouncing between your code editor and browser mid-recording. I didn’t have it for my [Quantum Russian Roulette GenServer video](https://www.youtube.com/watch?v=l7yB-n_TE2w) and without it, it made editing harder than it needed to be.

Installing it wasn’t super straightforward—there aren’t great Linux-specific guides for OBS plugins. But the short version: find your OBS plugins folder, drag the `.so` file in, and boom.

Now, let’s talk file types—because DaVinci Resolve is *very* particular. The file extension (like `.mp4` or `.mov`) is just a container; the real concern is the codec. Resolve on Linux doesn’t play well with h264/h265. Instead, I had to use `ffmpeg` to re-encode files into something Resolve would accept—specifically, `.mov` files using MPEG-4 part 2 video and PCM 24-bit audio. A weird combo, but it worked.

## Installing DaVinci Resolve on Linux

Okay. This one was wild.

First off, I’m on Ubuntu—which is oddly *not* officially supported by DaVinci Resolve. They support RedHat and RockyLinux instead. So right out of the gate, it was a challenge.

I’m also using an AMD GPU, and Resolve heavily favors Nvidia. I had to dig through logs and tinker with environment variables before I finally figured out the magic incantation:  
`RUSTICL_ENABLE=1 /opt/resolve/bin/resolve`

That `RUSTICL_ENABLE` variable got Resolve to use a better OpenCL implementation (apparently it works better than AMD’s native one on Linux). No guide mentioned this—I just pieced it together through experimentation and log-surfing.

Once I *did* get it running, editing worked decently. But rendering? Ugh. It barely used the GPU. Rendering at 14 FPS on Linux vs. up to 240 FPS on Windows. My solution: do everything in Linux—record, edit, prep—then boot into Windows just to render. Frustrating, but it works.

## Making the Video Happen

This was the hardest part. All the tech challenges led up to finally producing the [GenServer video](https://www.youtube.com/watch?v=l7yB-n_TE2w). And when I realized I was at risk of never finishing it, I told myself: “It’s better to submit any homework than none at all.”

Was it perfect? No. Could I have polished it more? Probably. But when a video’s an hour long, reviewing it gets time-consuming, and you can only speed it up so much before the speech becomes unintelligible.

There were also editing quirks—like DaVinci's "ripple editing," which sometimes caused weird duplicates or jump cuts. Plus, scripting and recording code explanations live? That’s hard. No wonder so many people split tutorials into parts. I eventually shifted to chunking: code a part, record a part, repeat.

That approach really helped. Having a working project already made it easier to stay on track during the tutorial. It also gave me more chances to internalize what I was teaching—kind of like learning through repetition. I now firmly believe: pause the recorder when you’re unsure, figure things out, then come back when you’re ready.

## Looking Ahead to April

In April, my goals are pretty simple:

1. Make it through the canvassing gig—hopefully in one piece.
2. Keep iterating on this video production pipeline.
3. Build consistency and quality over time.

Big takeaways from March:

- Setting up a Linux-to-Windows workflow is tricky, but doable.
- Talking through code is a skill. The more I practice, the better I get at communicating what I’m doing.
- Ship something. Done is better than perfect—especially early on.

And honestly? I’m excited. People have told me they see value in these tutorials, and I believe that too. I’d hate to let all this knowledge go to waste. Sure, I might explore other paths—but I need to share what I’ve learned before I move on.

Also, a highlight from today:  
I had an interview with **Kuali**! It went really well, and there was a live coding section I actually felt confident in. I credit that to the practice I’ve gotten recording videos and explaining code aloud. Fingers crossed I move to the next round—but if not, I’m still in a good spot. I took the canvassing job because I *wanted* to, not because I had to.

If things don’t pan out, I’m open to exploring trades like HVAC. Sales sounded interesting, but I’m not sure it’s for me. Canvassing is a great, low-stakes way to test the waters.

The weather’s been beautiful—green grass, blue skies, warm sun. Feels like the start of something. And speaking of starts—I owe a big shoutout to Jason Brown from the UK. He helped me polish my resume, and I’m certain his advice helped land me the Kuali interview. Jason knows the Elixir hiring space cold. If this leads to a job, he’s getting a big thank-you.

I know I might be punching above my weight right now. But hey—no risk, no reward. You miss 100% of the shots you don’t take. Let’s see what April brings.