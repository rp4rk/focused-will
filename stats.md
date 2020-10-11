## Coefficients

Coefficients are the amount of rating it requires, baseline, to achieve 1 unit of a given statistic. For example, 33 haste in Shadowlands at level 60 results in 1% haste. Below you can see all the coefficients for statistics that are relevant for healers,

| Statistic       | Coefficient |
| --------------- | ----------- |
| Haste           | 33          |
| Mastery         | 35          |
| Critical Strike | 35          |
| Versatility     | 40          |
| Leech           | 21          |
| Avoidance       | 14          |

## How Haste Works

Haste is a fairly straightforward statistic in 2020, you may have heard the term "haste breakpoint" before in the past, but those are mostly gone for now. There are still some places where breakpoints exist however, especially within the Discipline spec, so it can be helpful to keep this information at hand to calculate specific behaviors.

### Shadowfiend/Mindbender

> Note that for all haste math, the base value of haste is considered 100% or 1 - this is why 30% haste can be expressed as the number 1.3

Shadowfiend and Mindbender both have a baseline swing speed of 1.5 seconds, and as they restore mana **per swing** it means that there are moments you can use them with increased haste to gain more damage, healing, and mana. So in order to calculate, consider the following as behavior for Shadowfiend with no haste (i.e. naked). Shadowfiend will hit 11 times in 15 seconds, with a swing timer of 1.5 seconds. This leads us to the following formula,

`hitCount = floor( 1 + 15 / swingTimer )`

So let's modify this to get how many swings are available to us at say, 39.5% haste,

`hitCount = floor( 1 + 15 / (1.5 / 1.395) )`

The result of the formula after flooring is 14, however if we consider not flooring the value to the nearest integer, we get 14.95, meaning that if we were to get enough haste to push us over that number we get a whole extra hit. Hence Shadowfiend has what we call a breakpoint. If we were wanting to calculate the value at which a specific number of hits is achieved, we can calculate that using:

```
15 = 1 + 15 / ( 1.5 / x)
15 = 10x + 1
10x = 14
x = 1.4
```

Meaning that we achieve 15 hits at 40% haste.

### Evangelism

Evangelism also has haste breakpoints, in the form of when you can achieve a specific number of casts inside the 6 extra Atonement seconds provided by the effect. It is slightly more complex due to the nature of Evangelism having a Global Cooldown, however simplified by most of Discipline's cast times being 1.5 seconds baseline either via the Global Cooldown or regular requirements.

`casts = floor( (6 - (1.5 / haste)) / (1.5 / haste) )`

So for example at 39.5% haste again,

`casts = floor( (6 - (1.5 / 1.395)) / (1.5 / 1.395) ) = 4`

Let's solve for when we can get 5 of our regular casts into Evangelism,

```
5 = (6 - (1.5 / x)) / (1.5 / x)

7.5/x = 6 - 1.5 / x
6 = 7.5/x + 1.5/x
6x = 9
x = 1.5
```

### Rapture

Rapture is another effect that has breakpoints, the math here is similar to the Shadowfiend and Mindbender calculations, but to demonstrate the value of certain conduits for ramping let's take a look. Here's a familiar formula for the baseline version of Rapture,

`casts = 1 + 8 / (1.5 / haste)`

Let's say we were to want to find out when we can combine our Rapture with two Power Word: Radiance in order to coat a 20 man mythic raid, we would plug in:

```
10 = 1 + 8 / (1.5 / x)
15/x = 9
x = 15/9
x = 5/3 // (1.66666666667)
```

67% haste is quite a lot, and likely not achievable without Bloodlust or Heroism. So we can say that 'perfect' ramping is almost impossible with Rapture, however if we factor in the existence of a conduit such as [Exaltation](https://shadowlands.wowhead.com/spell=337790/exaltation), we can factor in the increase to duration,

```
10 = 1 + 10 / (1.5 / x)
15/x = 11
x = 15/11
x = 1.364
```

From adding an additional two seconds, we've almost halved the haste requirement, allowing us to say a 'perfect' ramp is potentially achievable with the right trinket.

#### Haste Conclusion

Some of these considerations are why it's common for Discipline Priests to say that Haste stacking is good because it affords you two key benefits:

- More Atonements (i.e. in the case of Rapture, or other ramps)
- More casts within Atonements (e.g. in the case of Evangelism)

If I have 50% Haste and that results in 50% more Atonement and 50% more damaging casts within that Atonement window, I've effectively gained 125% benefit instead of a plain 50%. A similar type of scaling can be seen with Restoration Druid HoTs, whereby they can cast more HoTs and each HoT will do more healing due to the haste as well.

## How Mastery Works

As Mastery is specific to each Specialization in the game, there has to be a specific tuning nob for each one in order to ensure that everyone gets a fair value from it. Take a look at the following Mastery effects:

- [Harmony](https://shadowlands.wowhead.com/spell=77495/mastery-harmony)
- [Grace](https://shadowlands.wowhead.com/spell=271534/mastery-grace)

The Restoration Druid Mastery, Harmony is tuned to 4% yet the Discipline Priest Mastery is tuned to 11.2%. This is because the Restoration Druid Mastery is a much more powerful effect, meaning that less of a percentage bonus results in roughly the same benefit as Grace does at 11.2%.

Each Specialization in the game has what are called Mastery 'points', points are an abstraction derived from rating, and each specialisation in the game has 8 points baseline. The implication here is that a single point value is the `base value / 8`, for example with Grace it would be `11.2 / 8 = 1.4`. This leaves us with the following;

`35 Mastery rating = 1 Mastery point = 1.4% Grace bonus`

## Diminishing Returns

In Shadowlands, secondary statistic ratings will start having diminishing returns at specific thresholds. It's incredibly likely that we will not be reaching the threshold of 30% with regular gear, but there is potential that certain trinkets or fight mechanics will push you into that range. You will need to keep this in mind, otherwise you could be getting substantially less value from your secondaries than you may be thinking.

### Current Thresholds

| Rating Penalty | Floor | Ceiling |
| -------------- | ----- | ------- |
| 0%             | 0%    | 30%     |
| 10%            | 30%   | 39%     |
| 20%            | 39%   | 47%     |
| 30%            | 47%   | 54%     |
| 40%            | 54%   | 66%     |
| 50%            | 66%   | 126%    |
| 100%           | 126%  | ∞       |

> Note: For mastery, replace the floor and ceiling (%) with (points), see [How Mastery Works](#how-mastery-works) for more detail.

### Heroism?

[Heroism](https://www.wowhead.com/spell=32182/heroism) and other effects that increase how much of a secondary you have, such as the Kyrian Soulbind passive [Pointed Courage](https://shadowlands.wowhead.com/spell=329778/pointed-courage) will ignore these diminshing returns. The difference here is that these effects increase the amount of the **secondary statistic** you have as opposed to granting you a certain amount of **rating**.

#### Example

![Secondary Statistic Process Diagram](img/stat-process.svg)

Consider this process diagram, using haste as an example because it's fairly simple, consider these values:

| Statistic   | Coefficient | Base Value     | Rating           | Bonus                                                                     | Final     |
| ----------- | ----------- | -------------- | ---------------- | ------------------------------------------------------------------------- | --------- |
| Crit        | 35          | 175 (5%)       | 3500 (76%)       | [+5%](https://shadowlands.wowhead.com/spell=329778/pointed-courage)       | 81%       |
| Haste       | 33          | 0 (100%)       | 1650 (47%)       | [30%](https://www.wowhead.com/spell=32182/heroism)                        | 191.1%    |
| Mastery     | 35          | 280 (8 points) | 3150 (71 points) | [+12% (+8 points)](https://shadowlands.wowhead.com/spell=152262/seraphim) | 87 points |
| Versatility | 40          | 0 (0%)         | 500 (12.5%)      | [+5%](https://shadowlands.wowhead.com/spell=328257/let-go-of-the-past)    | 17.5%     |

> Note, for rating calculations we are using the table in [Current Thresholds](#current-thresholds)
