# Kyrian Guide
## Boon of the Ascended Primer
In order to understand a lot of the text later, there’s a requirement to understand how Boon of the Ascended (Boon) works. Boons design is quite opaque and it can be hard to understand quickly with only a 10 second duration every 3 minutes. This prelude will describe the general functionality of the spell so you have context for the upcoming information.

### Boon Mechanics
Boon is a 1.5 second cast that will grant you a 10 second buff that transforms some of your spells into significantly more powerful versions. On top of this, these improved spells are instant with a 1 second global cooldown, and you can move with 50% increased movement speed during the effect.

#### Empowered Spells
* Ascended Blast, a very hard hitting spell that replaces your Smite cast but has a 3 second cooldown, reduced by haste. This also heals a nearby player for the damage it deals, like a secondary Atonement effect.
* Ascended Nova, a moderately powerful spell that functions similarly to Holy Nova and replaces your Boon of the Ascension button during the buff.

Each spell will build stacks of the Boon of the Ascended buff, up to a maximum of 100 stacks, and each stack will be consumed to buff an Ascended Eruption at the end of your 10 seconds of ascension. Ascended Blast will always grant 5 stacks, meaning 25 is the minimum for a single target. Ascended Nova will grant you stacks based on the number of enemy targets hit, which opens up some shenanigans we’ll go into later. 

Each stack consumed by Ascended Eruption will grant an extra 3% (4% with the Courageous Ascension conduit) damage and healing to this effect, meaning at 100 stacks it will deal 840-1050% spellpower damage before any modifiers. (That’s a lot).

#### Basic Rotation
The basic Boon rotation is straightforward, the combination of Ascended Blasts 3 second cooldown with the 1 second global cooldown on both Boon spells makes for a very simple rotation of,
> Ascended Blast -> Ascended Nova -> Ascended Nova  

Know that more advanced sequences exist that substitute Ascended Novas for more important casts, we’ll look at those more in-depth later.

#### Discipline Specific Mechanics
If you are a seasoned Discipline player, you will already know that AoE spells only proc Atonement from the first target hit. This introduces a very -awkward- cool Discipline specific constraint on the BotA spells. **As Nova/Eruption scale with the SQRT method, each enemy you hit will increase the overall damage done by the spell but decrease the Atonement healing from it.**

This introduces some conflicting goals:
* I want to hit as many enemies as possible with Ascended Nova in order to build stacks to buff my Ascended Eruption.
* I want to hit a single enemy with my Ascended Eruption in order to do the maximum amount of Atonement healing possible.

##### Stacking Shenanigans
The good news here is that while the rate of decay for Eruption is quite significant until around 3-4 targets, there is an offset in the form of building extra buff stacks via your Ascended Nova hitting more targets. 

So we’re left with some weirdness. On one hand, if you cannot hit a singular enemy with your Eruption that isn’t great. On the other, if you can AoE and hit a single enemy afterwards, your Eruption _might_ just be the single most broken thing Discipline is capable of in a raid currently.

#### Latency and Ascended Blast
Currently if you queue a Smite/Ascended Blast during the initial cast of Boon of the Ascended, you will encounter a 1500ms global instead of 1000ms. This is significant as it shaves off 5% of your total time in the buff, this could mean losing stacks which may upset your ability to get CDR reliably, or even result in a significant damage loss.

Luckily, there’s a way around it that incurs a much smaller time penalty, but isn’t perfect. By directly using the “Ascended Blast” spell name, the game client will not be allowed to dispatch the spell until the Boon buff is registered on us. The game servers then process the cast as an Ascended Blast as you would expect.

##### Spirit Shell + Ascended Blast
```
#showtooltip Spirit Shell
/cast Spirit Shell
/cast Ascended Blast
```

Spam this macro while casting Boon of the Ascended to cast Spirit Shell and Ascended Blast at the same time. After using this macro you can continue to use your original Smite bind.

##### Ascended Blast
```
#showtooltip Ascended Blast
/cast Ascended Blast
```

When playing with Evangelism, the first macro isn’t appropriate, as Evangelism is on the global cooldown. Once your initial Ascended Blast has finished, you can continue to use your regular Smite bind.

## Legendaries, Conduits, and Soulbinds
### Legendary Acquisition
#### Clarity of Mind
> Due to the introduction of Domination sockets on certain gear slots, players will have to recraft the Clarity of Mind legendary as a ring.   

Players will still want to have Clarity of Mind as it affords us the only way of extending Atonement durations into a range that lets us invest enough damage into them, particularly with Spirit Shell. We’ll talk later about how Clarity of Mind can tie into stronger Boon windows, and the primary sequence variant we use with it.

#### Spheres’ Harmony
> Spheres’ Harmony is exceptionally good in M+  - so you’ll probably at least want it to continue farming M+ each week for your valor upgrades.  

This legendary enables us to reduce the cooldown of Boon of the Ascended by up to a minute. The full value of this effect can be realised quite easily in single target situations, as most players will get 5 Ascended Blasts quite easily.

There is an alternative ramp sequence enabled by this legendary if you can take full advantage of it, note the inclusion of a Mindbender as on most fights you play Spheres’, you enable a ramp cadence that is divisible by a minute.

### Conduits
Courageous Ascension and Exaltation are lock in conduits, Courageous Ascension represents upwards of 100k absorb inside of your ramps, along with a fair chunk of damage. Exaltation allows the Eruption from your Boon to hit reliably during your Spirit Shell, which allows more of the damage from Courageous Ascension to be effective. Exaltation also lets you follow your ramp up with a Power Word: Solace to get some easy output.

The third slot is more of a toss up, you can choose from Shining Radiance or Rabid Shadows. Rabid Shadows will make your ramp better and provide better mana economy, whilst Shining Radiance represents more total output typically.

#### TL:DR 
Courageous Ascension = Exaltation > Rabid Shadows ~= Shining Radiance

### Sockets vs. Conduit Upgrading
Conduit upgrades represent a larger portion of output per point of currency than socketing your gear does in the next tier. This also pushes you out of the shared loot pools for conduits and allows DPS to get their upgrades earlier, resulting in a net benefit to your raid.

### Stat Weights
You want to maintain a good ratio of stats with a bias towards haste and mastery rating, I would HIGHLY recommend plugging your stat differentials into the [ramp calculator](https://ramp.focusedwill.com) to see how it will change your ramps. It’s important to note that DRs start to come into play this patch and balancing your secondaries is more important than prioritising two of them with no second thought.

With less output coming from shielding in 9.1, you may want to pick up leech with a stronger emphasis in order to survive progress better. 

Int -> Haste -> Mastery -> Crit -> Versatility 

#### Boon and Haste
As mentioned earlier, Boon spells have a 1 second GCD - the minimum GCD allowed by the game is 0.75 seconds. The end result here is that once you have 33% haste to cap that GCD to 0.75, your haste rating only applies to up to 3 casts inside of your Boon (Up to 2 Radiances, 1 Schism).

> 33% is a an arbitrary haste breakpoint, haste does not lose value here in traditional terms but will introduce oddities to your sequencing due to GCD capping.   

### Soulbinds
#### Mikanikos AKA Micky AKA Bron 
[Build link](https://ptr.wowhead.com/soulbind-calc/kyrian/forgelite-prime-mikanikos/priest/ApZlvgIFJysGJSdiBhMFKC4GFSd-BiUpogYiFSb-BiUnMwY)
Micky enables a build with a huge amount of potential. Similarly to the Spheres’ Harmony legendary he enables up to another minute of cooldown reduction based on the targets in the arena. This means you can have Boon of the Ascended on a minute cooldown, meaning any M+ gamer can be a rock hard Booner for the entire patch!

Beyond his CDR, Mikanikos has a few other notable traits,
* [Forgelite Filter](https://ptr.wowhead.com/spell=331609/forgelite-filter) - Automatic 20% healing and dispel when you fall under 35% health, massive for progress and M+ alike.
* [Hammer of Genesis](https://ptr.wowhead.com/spell=333935/hammer-of-genesis) - A huge amount of haste for M+ gaming, we place the Exaltation conduit on the same row to opt out of having one of the worst conduits in the game for Rapture gameplay.
* [Soulglow Spectrometer](https://ptr.wowhead.com/spell=352186/soulglow-spectrometer) - Notable because it doesn’t work for Discipline, always opts to buff the damage component of your output which is obviously insignificant.
* [Reactive Retrofitting](https://ptr.wowhead.com/spell=352187/reactive-retrofitting) - The better choice over Soulglow Spectrometer,  could approach Prydaz value on fights with diverse damage income. 

#### Pelagos
[Build Link](https://ptr.wowhead.com/soulbind-calc/kyrian/pelagos/priest/ApZulgEVJysGEwUoLgYVJ34GJSmiBiIVJv4GNSdUBg)
Pelagos is fairly competitive, but mainly for Combat Meditation - the mastery during Boon of the Ascended is incredibly powerful for your output. There’s also the final tier trait, which could randomly buff your output by 12% during your output window or not. Not worth relying on, but could be considerable on fights with a 2 minute damage pattern.

Pelagos also has the following to take note of,
* [Better Together](https://ptr.wowhead.com/spell=351146/better-together) - Buffs you and a friend by 40 mastery, which isn’t good but at least consistent.

That’s about it, Pelagos isn’t a super interesting soulbind - you will probably want to drop a decent amount of mastery for critical strike if you are using this soulbind a lot.

#### Kleia
Kleia is not very good, but there is some potential with her new conduits with regards to strategical use of Phial of Serenity and [Hope Springs Eternal](https://ptr.wowhead.com/spell=351489/hope-springs-eternal).

## Ramp Sequencing
Sequencing for ramps is significantly more complex than in 9.0, and with the influx of new legendaries, soulbinds, ramp timings, cooldowns, etc. - mathing out the perfect combination for each type of ramp was going to take an extreme amount of time. The response to this has been to create a quick n’ dirty ramp simulator, so know that going forward everything suggested has been derived from this and it has some pros and cons.

This also lets us start performing a comparison between ramp magnitude for the 9.0 and 9.1 iterations of Discipline, allowing for better understanding of relative strength which can inform strategy going forward. After all if a specific sequencing is producing similar ramp numbers, while leaving more Power Word: Radiance charges on the table, we can safely assume that it is likely to be viable.

### Ramp Simulation
Visit the [Ramp Simulator.](https://ptr.wowhead.com/spell=351489/hope-springs-eternal)

> Warning: this section is dedicated to explaining the internals of the tool used to calculate the results being suggested. If you’re not interested, skip ahead to the next section.  

#### State
The general idea behind simulating ramps is quite simple, every ramp can be treated as a sequence or list of spells that changes the state of the game. A typical ramp will do the following to the game state:

* Create absorbs on players
* Heal players
* Damage enemies
* Create buffs and debuffs
* Spawn pet entities to attack for you
* Advance time in the simulation

Each one of these factors can be stored in something known as “state” which is essentially a container for the current _state_ of the game. 

#### Sequencing
Consider the following spell sequence,

> Power Word: Shield -> Schism -> Smite  

By correctly modelling the effects of these spells on a given simulation state, we can determine the correct amount of absorbs, damage, and healing etc. that will happen as a result of executing this sequence. What’s more, is that each spell will have access to the version of the simulation state that is a result of the previous spell. For those of you interested, here’s a small snippet of the code that powers

#### Example Definitions
Below is an example definition for the Mindgames spell,
```typescript
export const Mindgames: Spell = {
  category: SpellCategory.Venthyr,
  id: 323673,
  icon: "ability_revendreth_priest",
  name: "Mindgames",
  damage: (state) => {
    const mgAmp = hasAura(state, "Shattered Perceptions") ? 1.208 : 1;

    return 253.8 * mgAmp;
  },
  castTime: 1500,
  effect: [advanceTime, damage, atonement],
};
```

As we can see it facilitates the mechanics of the spell by having a damage property that can evaluate the state of the simulation to see if there is a Shattered Perceptions aura. It will also advance time, apply damage, then atonement in that order.  This allows us to be super flexible with certain implementations, for example contrast it to Power Word: Solace.

```typescript
export const PowerWordSolace: Spell = {
  category: SpellCategory.Cooldown,
  id: 129250,
  icon: "ability_priest_flashoflight",
  name: "Power Word: Solace",
  damage: 75.2,
  effect: [damage, atonement, advanceTime],
};
```

As we can see, it’s a much simpler spell, but we can model the fact that it is an instant spell by progressing time _after_ the damage and atonement healing happens. 

#### DoTs and Event Interpolation
As we can’t feed DoT ticks in as events in a list, they’re subject to haste procs and so on - so ordering could possibly change, we forward project time at the start of each ability to see what ticks could possibly happen in that time. We then apply those immediately to the sim state and move on. Both pets and debuffs such as Shadow Word: Pain are implemented like this.

This is not entirely accurate in certain situations, e.g. haste fluctuations may introduce aberrations in how we project things on a cast-to-cast basis, but those do not currently exist so this is mostly an 80% correct solution done in 20% of the time.

#### Misc. Tidbits
* Not open source at the moment, code is a mess, feel free to mess around in developer tooling or request access though
* Critical strikes are modelled as their mathematical equivalent, i.e. 20% crit is a 20% damage buff.

### Ramp Sequences
Import these sequences to the [Ramp Simulator](https://ramp.focusedwill.com) to see an in depth breakdown of their output and how they will look with your character.

#### Pelagos - Clarity of Mind
As Pelagos provides no CDR by default, we rotate our Boon and Shadowfiend to ensure each Spirit Shell has a CD going into it. This build is weaker whenever delaying Shadowfiend to your second ramp results in one less use over the duration of the fight.

##### Primary - Boon
```
{"spellNames":["Purge the Wicked","Purge the Wicked","Shadow Mend","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Radiance","Boon of the Ascended","Spirit Shell","Ascended Blast","Power Word: Radiance","Ascended Blast","Schism","Ascended Nova","Ascended Blast","Ascended Nova","Ascended Nova","Ascended Blast","Ascended Nova","Ascended Nova","Ascended Blast","Power Word: Solace"]}
```

##### Secondary - Shadowfiend
```
{"spellNames":["Purge the Wicked","Purge the Wicked","Shadow Mend","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Shadowfiend","Power Word: Radiance","Power Word: Radiance","Spirit Shell","Schism","Penance","Power Word: Solace","Mind Blast","Smite","Smite","Smite","Smite","Smite","Smite"]}
```

#### Pelagos - Spheres’ Harmony
With Sphere’s Harmony your goal is to have primary ramps that are comparable to your CoM ramps, this build sacrifices some peak ramp strength in order to ramp to a two minute timer with mitigated losses.

> Note this build has a secondary ramp that does not utilise your Spirit Shell cooldown, it is unlikely to perform better than the standard Clarity of Mind build unless you are using it to meet a specific timer.  

##### Primary - Boon + Mindbender
_Disable the Clarity of Mind legendary effect._
```
{"spellNames":["Purge the Wicked","Purge the Wicked","Shadow Mend","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Mindbender","Boon of the Ascended","Spirit Shell","Ascended Blast","Power Word: Radiance","Ascended Blast","Power Word: Radiance","Ascended Blast","Schism","Ascended Nova","Ascended Blast","Ascended Nova","Ascended Nova","Ascended Blast","Ascended Nova","Purge the Wicked"]}
``` 

##### Secondary - Mindbender
_Disable the Clarity of Mind legendary effect._
```
{"spellNames":["Purge the Wicked","Purge the Wicked","Shadow Mend","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Mindbender","Power Word: Radiance","Power Word: Radiance","Schism","Mind Blast","Penance","Smite","Smite","Smite","Smite","Smite"]}
```

#### Mikanikos - Clarity of Mind
Similarly to the Pelagos Spheres’ Harmony build, the idea behind this is to utilise the Effusive Anima Accelerator effect to reduce the CD of Boon to two minutes and ramp on that interval.

These ramps are essentially the same as the Spheres’ Harmony iterations, but will only be available later in the tier and are more sensitive to the number of targets you hit.

> Note this build has a secondary ramp that does not utilise your Spirit Shell cooldown, it is unlikely to perform better than the standard Clarity of Mind build unless you are using it to meet a specific timer.  
 
##### Primary - Boon + Mindbender
```
{"spellNames":["Purge the Wicked","Purge the Wicked","Shadow Mend","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Mindbender","Boon of the Ascended","Spirit Shell","Ascended Blast","Power Word: Radiance","Ascended Blast","Power Word: Radiance","Ascended Blast","Schism","Ascended Nova","Ascended Blast","Ascended Nova","Ascended Nova","Ascended Blast","Ascended Nova","Purge the Wicked"]}
```

##### Secondary - Mindbender
```
{"spellNames":["Purge the Wicked","Purge the Wicked","Shadow Mend","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Mindbender","Power Word: Radiance","Power Word: Radiance","Schism","Penance","Mind Blast","Smite","Smite","Smite","Smite","Smite","Smite","Smite"]}
```

#### Mikanikos - Spheres’ Harmony - 1.5 Minute Iteration
There could be a few fights where hitting 3 enemy targets with Effusive Anima Accelerator is reliable enough to bring you through the fight with a 1.5 minute Boon cooldown. This opens up Boon for every Spirit Shell on cooldown, which can be very strong.

##### Primary - Boon + Shadowfiend
_Disable the Clarity of Mind effect._
```
{"spellNames":["Purge the Wicked","Purge the Wicked","Shadow Mend","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Shadowfiend","Power Word: Shield","Power Word: Shield","Boon of the Ascended","Spirit Shell","Ascended Blast","Power Word: Radiance","Ascended Blast","Power Word: Radiance","Ascended Blast","Schism","Ascended Nova","Ascended Blast","Ascended Nova","Ascended Nova","Ascended Blast","Ascended Nova","Power Word: Solace"]}
```

##### Secondary - Boon
```
{"spellNames":["Purge the Wicked","Purge the Wicked","Shadow Mend","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Boon of the Ascended","Spirit Shell","Ascended Blast","Power Word: Radiance","Ascended Blast","Power Word: Radiance","Ascended Blast","Schism","Ascended Nova","Ascended Blast","Ascended Nova","Ascended Nova","Ascended Blast","Ascended Nova","Power Word: Solace"]}
```

#### Mikanikos - Spheres’ Harmony - 1 Minute Iteration
There are going to be very few fights where this is a good idea, but it’s here for the sake of demonstrating the high level of variety 9.1 opens up for Discipline ramping. The use case for this is a fight where you can ramp every minute by using the Spheres’ Harmony and Effusive Anima Accelerator traits. 

##### Primary - Boon + Mindbender
```
{"spellNames":["Purge the Wicked","Purge the Wicked","Shadow Mend","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Mindbender","Power Word: Radiance","Boon of the Ascended","Spirit Shell","Ascended Blast","Power Word: Radiance","Ascended Blast","Schism","Ascended Nova","Ascended Blast","Ascended Nova","Ascended Nova","Ascended Blast","Ascended Nova","Ascended Nova","Ascended Blast"]}
```

##### Secondary - Boon + Mindbender (lol)
```
{"spellNames":["Purge the Wicked","Purge the Wicked","Shadow Mend","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Power Word: Shield","Mindbender","Boon of the Ascended","Ascended Blast","Power Word: Radiance","Ascended Blast","Power Word: Radiance","Ascended Blast","Schism","Ascended Nova","Ascended Blast","Ascended Nova","Ascended Nova","Ascended Blast"]}
```

## Summary
Kyrian Discipline is looking to be a good way for the spec to adjust to the incoming Spirit Shell nerfs, even the weakest Boon sequencing is at least 25% stronger than the strongest iteration of the Venthyr ramp, which is no longer sustainable in the upcoming patch.

Boon introduces a lot of activity into the ramp, and the spell certainly has problems, but after playing it for a while on live it’s certainly better than 9.0 disc in terms of gameplay. While anaemic healing outside of ramps is still a concern going into the future, the variety of ramping and introduction of actual gear choices such as Spheres’ represents a significant improvement for the state of Discipline overall.

### Feedback, Thoughts, Concerns, etc.
These are things I see as major concerns for Discipline going forward, it’s no secret that Discipline has suffered a decline in terms of maintenance and design over the years since Legion. These are what I see as ways to tighten the spec up a little,

* DoTs do not last long enough baseline to extend into a ramp if applied at the start of said ramp, compare this to Effloresence.
* Mindbender should represent a reasonable exchange of mana to output via cooldown synergy, it does not do this at the current level of tuning.
* Introduce talents that allow Discipline to execute fights like Sun King, and work around frustrating immunity mechanics. Sun King was embarrassing*. 
* Discipline has a glut of medium term cooldowns that aren’t very impactful, Penance tuning is a shame.
* Consider an 18 second cooldown for Power Word: Radiance if Evangelism and Spirit Shell are both going to be 1.5 minutes. 
* Spirit Shell needs to go, this button should be relegated to Mists of Pandaria private servers for the rest of time.

Personal stretch goal,
* Return interactions between trinkets and Atonement, the Sentinel Owl and Sentinel Beacon were extremely fun, and allowed for toying with certain damage profiles for healing various damage types.

\* _When I say this is embarrassing, I mean having an entire fight where a healer cannot be taken is a bad joke. This expansion is so incredibly hostile towards playing off-specs, and this fight set precedent for constant maintenance of Holy for the next two years._ 🖕

### Thanks
* Smallpriest, for providing a huge amount of support with checking results and fixing bugs.
* WarcraftPriests, for their mastery of Cunningham’s Law.
* General Hospital, for providing refuge to the citizens of Focused Will at time of dire need.


