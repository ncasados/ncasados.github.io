---
title: "Some Thoughts on Building Bet Buddies Part 1"
date: "2024-03-19 11:00:00"
thumbnail: "/assets/img/thumbnail/playing-cards.jpg"
---

I'm definitely not doing anything ground breaking, but I wanted to talk a little about some of what I have learned from working on making a Texas Hold'em Poker application in Elixir.

# GenServers, Registries, and DynamicSupervisors Are Lovely
---
Elixir is a very cool language because it's grandpappy Erlang is cool. It's cool because you have processes as a primitive within the language and these processes are decoupled from one another. So if one process encounters a bug and dies, it doesn't take down the entire application with it. One common use of this in Elixir land is setting up a GenServer, registering it to a Registry, and having a DynamicSupervisor supervise the GenServer.

<img src="/assets/img/building-a-poker-app-part1/genservers_registry_and_dynamic_supervisors.png"/>

Starting with this kind of knowledge base and having seen other examples of how this can be used with a game, I figured I would start building out a Texas Hold'em poker application. As it would turn out too, there aren't a lot of great multiplayer poker applications and I'm out here building probably the worst one. However, it's mine and I love it.

So what does this GenServer do? Well, you can put the state of the poker game as the state of the GenServer. So this GenServer process is holding onto some data structure representing what's going on in the game and I can show what this looks like.

```
defmodule Poker.GameState do
  use Ecto.Schema
  alias Poker.Card
  alias Poker.Player

  embedded_schema do
    field :game_id, :string
    field :game_started_at, :utc_datetime
    field :password, :string
    field :game_stage, :string
    embeds_many :dealer_hand, Poker.Card
    embeds_many :dealer_deck, Poker.Card
    field :pot, :integer
    field :side_pot, :integer
    embeds_many :players, Poker.Player
    field :turn_number, :integer
    field :minimum_bet, :integer, default: 0
    field :most_recent_max_bet, :integer, default: 0
    field :big_blind, :integer, default: 800
    field :small_blind, :integer, default: 400
  end
  ...
end
```

Now this structure will likely change from what I'm showing in this article, but essentially this is what is being tracked for a poker game. What is particularly nice is that we can give unique poker games unique game ids. These get registered to the Registry and supervised by the DynamicSupervisor. In this way with Elixir, we can have a hypothetical millions of poker games going on each decoupled from each other so if there were some issue in one poker game, it wouldn't affect anyone else's poker games. It's really the multiple poker games going on that's nice though.

None of that would be possible without the fact that GenServers, Registries, and DynamicSupervisors exist and I find myself while building out the program and debugging just going and creating a new poker game and running through it. Make some changes, make a new game, validate changes--wash, rinse, repeat.

Now continuing with the GenServer, because it's a server, we can send it messages like, "Hey man, in the 'Eevee' game, player 1 had just bet 400."

Then the GenServer can handle the processing for making 400 leave player 1's wallet, go into the pot, and move onto the next player. Really cool stuff!

# Some of the Challenges
---
Now probably the biggest challenge that I found myself encountering while building out this thing was figuring out how to handle sidepots, and managing whose turn it is. 

What has been great about living in 2024 is now we have YouTube and AI chatbots and I found myself watching YouTube videos on how to handle side-pots and asking chatbots how to handle side pots and between the two, one can begin to close knowledge gaps.

So just to share about these knowledge gaps, let's talk about side-pots.

Side-pots are created when there are 3 or more players betting but one player has decided to all-in but they had less money than everyone else. Suppose that we have three players: Alice, Bob, and Charlie. Suppose that Alice bets 1000, Bob calls for 1000, and Charlie only has 50. Charlie, desperate to win or lose, bets it all. This means that for Alice and Bob, their 1000 bet will have 50s added to the main-pot and the overflow 950 will go into a side-pot. Although Alice, Bob, and Charlie are all competing for the main-pot, only Alice and Bob can win the side-pot. It took me a while to learn this.

Next, we have managing whose turn it is. Naively, I had thought, "Let me just assign a turn number to everyone. Alice is first, Bob is second, Charlie is third. Then when they make a move, we'll increment between 0, 1, and 2 respectively."

Although this manages to get a game where you can loop through players, poker is tricky. When someone folds, they aren't part of the turns happening the rest of the hand. If someone bets, then everyone else has to call up to the same amount. If everyone called, then the first person to have moved has a chance to check. With all of this complexity to moving around players, I ended up learning to set up a "Player Queue" where this queue will remove players who had just made some kind of move, however if someone bets, then everyone gets added back into the queue except for the better unless someone bets even more.

So with the next updates of my poker app at this time, I'm working on implementing this stuff. Recently I had just started to write up getting the dealer to put cards on the table and needing to edit some of that front-end UI displaying that.

Thanks for reading!
