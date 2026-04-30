[[toc]] 

# Speech for Game Developers

Think about the moments when your players aren’t in front of their screens.

They’re on the bus.  
They’re walking to class.  
They’re grabbing coffee before work.  
They’re living their lives.

And in those ordinary moments, something extraordinary can happen.

They cross paths with someone who loves the same game they do.

They don’t need to talk.  
They don’t need to exchange usernames.  
They don’t need to coordinate or plan.

They just feel it — that spark of recognition.  
That quiet smile.  
That sense of *oh, someone else out there cares about this too*.

That’s Kiubo.

Kiubo isn’t about replacing social features.  
It’s about **extending your game’s community into the real world**, gently, naturally, and respectfully.

Messaging is intentional.  
Friend codes are transactional.  
Social feeds are noisy.

Kiubo is ambient.

It’s the heartbeat of your community, pulsing softly in the background of your players’ daily lives.

With Kiubo, your game becomes something players *carry with them* — not because they’re grinding or checking notifications, but because the world itself becomes part of the experience.

Two players sitting in the same train car.  
Two fans waiting in the same line.  
Two strangers who share a world, a guild, a passion.

Kiubo turns those moments into meaning.

A small reward.  
A shared bonus.  
A collectible.  
A story they’ll tell later.

Not because they talked — but because they connected.

And that connection strengthens your community in a way no chat system or friend list ever could. It builds a sense of belonging that players feel even when they’re not actively playing.

Kiubo doesn’t ask players to do more.  
It simply lets them feel more.

More seen.  
More connected.  
More part of something bigger.

For you, as a developer, Kiubo is a new design surface — a way to create rituals, surprises, and shared experiences that happen *out there*, in the real world, where your players live.

It’s a way to keep your community alive between sessions.  
A way to reward exploration and movement.  
A way to make your game feel present, even when the app is closed.

Kiubo isn’t a feature.  
It’s a feeling.

A feeling of belonging.  
A feeling of community.  
A feeling that your game is part of the player’s life — not just their screen time.

That’s why Kiubo exists.  
Not to replace social interaction, but to **weave your game’s community into the everyday moments where connection feels the most human**.

Here are **two versions** of the Kiubo pitch you asked for — one **emotional and human**, one **technical and developer‑friendly**.  
Both are short, sharp, and designed to *land* with the people who make decisions.

---

# Shorter Pitch for Producers, Designers

**Kiubo is about keeping your community alive in the moments between play.**

Your players don’t stop being fans when they close your game.  
They carry your world with them — on the bus, in the hallway, at the café, walking to work.

Kiubo turns those everyday moments into tiny sparks of connection.

Two players sitting in the same train car.  
Two fans waiting in the same line.  
Two strangers who share the same love for your game.

Kiubo lets them feel that.

A soft vibration.  
A small reward.  
A quiet smile.  
A sense of *belonging*.

Not because they talked.  
Not because they friended each other.  
But because your game reached out and said:

**“Hey — you’re not alone. Someone else loves this too.”**

Kiubo extends your community into the real world.  
It keeps players connected to your world even when they’re not actively playing.  
It turns proximity into possibility — and everyday life into part of the experience.

It’s simple.  
It’s warm.  
It’s human.

And it gives your game a heartbeat that follows your players wherever they go.

---

# TECHNICAL PITCH (for engineers, tech leads, and producers) 
**Kiubo is the easiest way to add real‑world encounters to your game — without building any of the hard parts yourself.**

Kiubo handles the messy, platform‑specific problems so you don’t have to:

- **Cross‑platform BLE encounter detection** (iOS + Android)  
- **Background‑safe scanning** that respects OS rules  
- **Battery‑friendly duty cycling**  
- **Offline‑first encounter logging**  
- **Deferred sync with idempotent APIs**  
- **Rotating, anonymous IDs** (no PII, no compliance headaches)  
- **Unity‑native API** that feels like any other gameplay system  

Integration is as simple as:

```csharp
Kiubo.Start();
Kiubo.OnEncounter += e => GrantReward(e);
```

That’s it.

No servers required — unless you want them.  
Kiubo provides a **fully documented, backend‑agnostic API**, so studios can:

- Use Kiubo Cloud (optional)  
- Self‑host with Node, Go, Python, or anything else  
- Plug Kiubo into existing account systems  

Kiubo doesn’t force a network stack, a database, or a service contract.  
It’s a **tool**, not a dependency.

And once it’s in your game, it unlocks mechanics you simply couldn’t build before:

- Encounter streaks  
- Real‑world buffs  
- Event‑based bonuses  
- Community rituals  
- Collectibles tied to real‑world crossings  
- Convention‑exclusive encounters  
- Guild proximity rewards  
- “You met someone from your faction today” moments  

Kiubo gives your designers a **new dimension** to play with — a social layer that lives in the real world, not just on the screen.

It’s lightweight.  
It’s safe.  
It’s easy to integrate.  
And it opens up a whole new category of mechanics for your game.

# Invitation to Test Kiubo

1. **Short emotional intro pitch** (for designers, producers, creative leads)  
2. **Short technical intro pitch** (for engineers, tech leads)



## Invitation to designers, producers, creative directors

Hi! I’m building something new for Unity games, and I’d love to invite you to be part of it.

It’s called **Kiubo** — a lightweight system that turns real‑world proximity into small moments of connection inside your game. Think of it as a modern, privacy‑safe evolution of StreetPass: when two players cross paths in the real world, your game can respond with a reward, a collectible, a buff, or a moment of delight.

Kiubo isn’t about messaging or friend codes. It’s about giving your players a sense of *belonging* even when they’re not actively playing.  
That feeling of being on the bus, looking up, and realizing someone else nearby loves the same world you do.

I’m offering early access for free because I want to build this **with** developers — to learn what kinds of mechanics you’d create, what sparks your imagination, and what would make Kiubo genuinely valuable for your community.

If you’re exploring new ways to keep players connected, engaged, and emotionally invested, Kiubo might open a door you didn’t know was there.

I’d love to hear what you think.



## Invitation to engineers, tech leads, technical producers

Hi! I’m developing **Kiubo**, a Unity‑ready proximity encounter system that lets your game react when players cross paths in the real world — without requiring you to build any of the hard parts.

Kiubo handles:

- Cross‑platform BLE encounter detection (iOS + Android)  
- Background‑safe scanning that respects OS rules  
- Battery‑friendly duty cycling  
- Offline‑first encounter logging  
- Deferred sync with idempotent APIs  
- Anonymous, rotating IDs (no PII, no compliance headaches)  
- A clean Unity API that feels like any other gameplay system  

Integration is simple:

```csharp
Kiubo.Start();
Kiubo.OnEncounter += e => GrantReward(e);
```

No servers required — unless you want them.  
Kiubo includes a backend‑agnostic API so you can self‑host with any stack.

I’m offering early access for free because I want real developer feedback on what workflows feel natural, what tools you need, and what mechanics Kiubo unlocks for your game. My goal is to make Kiubo a **creative enabler**, not a dependency that adds friction.

If you’re interested in exploring new social mechanics with minimal setup, I’d love to share Kiubo with you.

## DM-Friendly 

**Option1**

Hey! I’m building a small Unity tool called Kiubo — it lets your game react when players cross paths in the real world, kind of like a modern StreetPass. It’s lightweight, privacy‑safe, and free during early access. I’m looking for a few devs who want to try it and help shape what it becomes.
If you’re curious, here’s more info: Learn more


**Option 2**

Hey! I’m working on a Unity tool called Kiubo — it turns real‑world encounters between players into in‑game moments (rewards, buffs, collectibles, etc.). Think “StreetPass energy,” but modern, simple, and privacy‑safe. I’m opening early access for free and looking for devs who want to experiment with it and influence the final design.
If that sounds interesting, here’s a quick overview: What is Kiubo?


**Option 3 (Studio-Facing)**

Hello! We’re developing Kiubo, a Unity‑ready system that lets your game respond when players cross paths in the real world — a modern, privacy‑safe evolution of StreetPass. It’s designed to strengthen community, extend engagement beyond play sessions, and unlock new social mechanics with minimal engineering effort.

We’re offering early access at no cost and inviting a small group of studios to help shape the final version. If your team is exploring new ways to differentiate your game or deepen player connection, Kiubo may be a strong fit.
More details here: Kiubo overview