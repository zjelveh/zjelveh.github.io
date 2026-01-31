# Lecture 14: Anatomy of a Comparison
## From Description to Causation

**Slides:** [10_causal_inference.pptx](/files/ccjs418e_fall2025/10_causal_inference.pptx)
**Notebook:** [10_causal_inference.ipynb](https://colab.research.google.com/github/zjelveh/zjelveh.github.io/blob/master/files/ccjs418e_fall2025/10_causal_inference.ipynb)

---

## Slide 1: Title

**Anatomy of a Comparison: From Description to Causation**

Week 14 - CCJS 418E

---

## Slide 2: Two Ways to Ask the Same Question

There are two ways to ask what looks like the same question:

**Version A:** "Are there more noise complaints on days with Yankees games?"

**Version B:** "Do Yankees games *cause* more noise complaints?"

Same data. Same comparison. Different questions.

---

## Slide 3: Why This Matters

Version A is **descriptive** - it asks what happened.

Version B is **causal** - it asks why it happened.

Policy decisions need Version B answers. If you want to know whether to add police presence on game days, you need to know if games actually cause problems - not just whether problems happen to coincide with games.

But Version B is much harder to prove.

**ASK:** Which version is YOUR final project asking?

---

## Slide 4: What Does "Cause" Mean?

"Yankees games caused more noise" means:

**If the game hadn't happened, there would have been less noise.**

It's about the "what if" — what would have happened otherwise?

**The Problem:**
- We can't observe both worlds
- We only see what actually happened (game + noise)
- We never see what *would have* happened without the game

**So what do we do?**
- We use comparisons to approximate the "what if"
- Non-game days are our best guess at "what would have happened"

---

## Slide 5: Your Projects Ask Causal Questions

Look at some of the questions from your proposals:

- "Do NFL games lead to more crime?"
- "Has tough-on-crime policy deterred violent crime?"
- "Does crime increase during holidays?"

These are all Version B questions - they're asking about causes.

But the analyses you proposed mostly answer Version A - they describe patterns without ruling out alternatives.

This week is about bridging that gap.

---

## Slide 6: The Basic Comparison

Let's start with our familiar example: noise complaints and Yankees games.

We compare game days to non-game days and find: **33% more noise complaints on game days.**

This answers Version A: Yes, there are more complaints on game days.

Does it answer Version B? Do we know the games *caused* the extra complaints?

---

## Slide 7: What Else Could Explain This?

Before I show you alternatives, think for a moment:

**ASK:** What else besides the games themselves could explain why we see more noise complaints on game days?

Take 30 seconds to think of at least one alternative explanation.

We'll cover five alternatives: day of week, season, citywide trend, location, and reporting behavior.

---

## Slide 8: Alternative 1 - Day of Week Effect

Yankees games cluster on certain days - especially weekends.

Weekends already have more noise complaints (parties, people home, bars open late).

Maybe we're picking up a **weekend effect**, not a **game effect**.

**ASK:** How would you test whether it's the weekend or the game driving the pattern?

---

## Slide 9: Alternative 2 - Seasonal Effect

Baseball season runs April through October - the warm months.

In summer: windows are open, people are outside, outdoor parties, more activity.

Maybe we're picking up a **summer effect**, not a **game effect**.

**ASK:** Is this a convincing alternative? Why or why not?

---

## Slide 10: Alternative 3 - Citywide Trend

Maybe NYC is just getting noisier over time — construction, population growth, more nightlife.

Game days might coincide with noisier periods by chance.

If the whole city is getting noisier and game days happen to fall during those noisier times, we'd see a pattern even if games have nothing to do with it.

**ASK:** How could we check if it's a general NYC trend vs. something specific to games?

---

## Slide 11: Alternative 4 - Location

Maybe areas near Yankee Stadium are just noisier places in general.

The Bronx has bars, restaurants, public transit hubs — maybe it's noisy regardless of games.

If the Bronx is inherently noisy, we'd see more complaints there on ALL days, not just game days.

**ASK:** How could we separate "the Bronx is noisy" from "games make it noisier"?

---

## Slide 12: Alternative 5 - Reporting Behavior

Here's a subtle one: maybe games don't cause more NOISE, just more COMPLAINTS.

Residents who live near the stadium might be primed to be annoyed on game days. Their tolerance is lower. They're more likely to call 311.

Same amount of noise, different likelihood of reporting.

**ASK:** Can we distinguish "more noise" from "more reporting" with 311 data?

---

## Slide 13: The Challenge

One comparison can't rule out all these alternatives.

We need **multiple comparisons**, each addressing different concerns.

Think of it like building a legal case - no single piece of evidence proves guilt, but together they build a compelling argument.

---

## Slide 14: Strategy 1 - Compare to Yourself

**Logic:** Same place, different times.

Compare the Bronx on game days to the Bronx on non-game days.

**What this rules out:** "Maybe the Bronx is just a noisy place."

If someone said "The Bronx just has more complainers" or "The Bronx has denser housing" — this comparison answers that. We're comparing the Bronx to *itself*, so those things cancel out.

**What this doesn't rule out:** Things that change over time.

- **Day of week:** Yankees games cluster on weekends. Weekends already have more noise (parties, people home). Maybe it's the *weekend*, not the *game*.

- **Season:** Baseball runs April-October. Summer means open windows, outdoor activities, block parties. Maybe it's *summer*, not the *game*.

- **Citywide trend:** Maybe NYC is just getting noisier over time, and game days happen to fall during noisier periods.

---

## Slide 15: Strategy 1 Results

When we filter to just the Bronx:

- Game days: 431 complaints/day average
- Non-game days: 310 complaints/day average
- **39% increase on game days**

This rules out: "The Bronx is just a noisy place in general."

This doesn't rule out: Day of week effects, seasonal effects, or citywide trends.

**ASK:** What else — besides the game — could still explain this 39% increase?

---

## Slide 16: Strategy 2 - Compare to Someone Else

**Logic:** Same time, different places.

On game days, compare the Bronx to Brooklyn. Does the Bronx have a higher *share* of complaints than usual?

**What this rules out:** "Maybe it's just weekends" or "Maybe it's just summer."

If game days are noisier everywhere for time-based reasons, both boroughs should increase proportionally — the shares would stay the same. If Bronx's share goes UP on game days, something specific to the Bronx is happening.

**What this doesn't rule out:** Differences between places.

- **Population:** Brooklyn has more people than the Bronx.

- **Housing:** Different neighborhoods have different building types.

- **Who complains:** Some neighborhoods call 311 more readily than others.

---

## Slide 17: Strategy 2 Results

**Share of complaints by borough:**

On non-game days:
- Bronx: 46% of complaints
- Brooklyn: 54% of complaints

On game days:
- Bronx: 48% of complaints
- Brooklyn: 52% of complaints

**Bronx's share increases by 2 percentage points on game days.**

This suggests something specific to the Bronx is happening on game days — not just a general "game days are noisier" effect.

**ASK:** What could still explain this shift besides the stadium?

---

## Slide 18: The Problem with Each Strategy

| Strategy | What it holds constant | What could still explain the pattern |
|----------|----------------------|--------------------------------------|
| Compare to yourself | Place (Bronx vs Bronx) | Time-based factors (weekends, summer, citywide trends) |
| Compare to someone else | Time (same day) | Place-based factors (population, housing, complaint culture) |

Each strategy rules out some alternatives but not others.

**The insight:** What if we combined them?

If we compare *changes* instead of *levels*, we can hold both place AND time constant.

---

## Slide 19: Strategy 3 - Difference in Differences

Here's the key insight:

Compare the **CHANGE** in the Bronx to the **CHANGE** in Brooklyn.

- If there's a citywide trend: both boroughs change equally, difference = 0
- If the stadium has an extra effect: Bronx changes MORE, difference > 0

We're taking the difference of two differences - hence "difference-in-differences."

---

## Slide 20: Diff-in-Diff Table

|           | Non-Game Day | Game Day | Change |
|-----------|--------------|----------|--------|
| Bronx     | 310          | 431      | +121 (+39%) |
| Brooklyn  | 370          | 472      | +102 (+28%) |
| **Difference** |         |          | **+19 (+11%)** |

Both boroughs increase on game days - that's the citywide effect.

But the Bronx increases **more** - that's the stadium effect.

The 11 percentage points = the localized stadium effect above and beyond citywide trends.

**ASK:** What does this 11% represent? What does it rule out?

---

## Slide 21: What Diff-in-Diff Rules Out

1. **"Maybe it's just weekends/summer"** - If game days are noisier everywhere, this affects both boroughs equally and cancels out.

2. **"Maybe the Bronx is just noisier"** - We're comparing *changes*, not levels. If the Bronx is always noisier, that doesn't matter — we're asking if it gets *extra* noisy on game days.

3. **"Maybe all of NYC gets excited for Yankees games"** - Brooklyn captures the citywide "people watching in bars" effect. We subtract it out.

The ~11% extra in the Bronx is our best estimate of the localized stadium effect — the noise specifically from being near the stadium.

---

## Slide 22: But We're Still Not Done

Diff-in-diff handles the "maybe it's the weekend" and "maybe Brooklyn is different" problems.

But what if our OUTCOME is the problem?

What if something about game days affects ALL types of 311 complaints - not just noise?

Maybe people are more likely to call 311 on game days for any reason. Maybe there's something weird in the data we don't understand.

---

## Slide 23: The Placebo Test

**Idea:** Test an outcome that SHOULDN'T be affected.

If Yankees games cause NOISE complaints... they shouldn't cause HEATING complaints.

Think about it: there's no reason a baseball game would affect whether someone's boiler breaks.

**ASK:** Why is heating a good test here? What would make a good "shouldn't be affected" outcome in general?

---

## Slide 24: Placebo Logic

**If heating complaints ALSO spike on game days:**
- Something else is going on
- Maybe people just call 311 more on game days, for any complaint?
- Maybe there's something weird in the data?
- Our comparison might be picking up the wrong thing

**If heating complaints show NO game-day effect:**
- Strengthens the noise finding
- Rules out "people just complain more on game days"
- The effect is specific to noise — which makes sense if games actually cause noise

---

## Slide 25: Placebo Results

| Metric | Noise | Heating |
|--------|-------|---------|
| Overall game-day effect | +33% | -75% |
| Bronx effect | +39% | -76% |
| Brooklyn effect | +28% | -75% |
| Diff-in-diff | +11% | -1% |

Heating complaints go DOWN on game days - because baseball season is summer, and no one needs heating!

More importantly: the diff-in-diff for heating is essentially zero. No Bronx-specific effect.

This is good news for our noise finding. If heating also spiked in the Bronx on game days, we'd be worried. But it doesn't — so the noise pattern seems real.

---

## Slide 26: What Could Still Explain This?

Even after diff-in-diff and the placebo test, we haven't *proven* causation.

Someone could still argue:

- **"Maybe Bronx residents are extra sensitive to game-day noise"** — They tolerate normal noise but complain more when it's game-related.

- **"Maybe there are other events near Yankee Stadium on game days"** — Food vendors, street performers, traffic congestion — not the game itself.

- **"Maybe it's the fans traveling through, not the game"** — Subway crowds, honking, pregame gatherings in the neighborhood.

- **"Maybe Brooklyn isn't a good comparison"** — What if Brooklyn has its own game-day dynamics we don't know about?

This is why we say "closer to Version B" — not proof, but a stronger case.

---

## Slide 27: Applying to Your Projects

Think about your final project:

**Example 1:** "Do NFL games lead to crime?"
- Placebo: Do NFL games lead to library book checkouts?

**Example 2:** "Does crime increase during holidays?"
- Placebo: Do pothole complaints increase during holidays?

**ASK:** What would be a good placebo outcome for YOUR project?

---

## Slide 28: Building a Causal Case

| Step | What You Do | What It Rules Out |
|------|-------------|-------------------|
| Basic comparison | Game vs non-game | Nothing yet — just shows a pattern |
| Compare to yourself | Same place, different times | "Maybe the Bronx is just noisy" |
| Compare to someone else | Same time, different places | "Maybe it's just weekends/summer" |
| Diff-in-diff | Compare the changes | Both place AND time explanations |
| Placebo test | Test an outcome that shouldn't be affected | "Maybe people just complain more on game days" |

---

## Slide 29: From Version A to Version B

- One comparison = Version A (descriptive — just shows a pattern)
- Multiple comparisons = Stronger (rules out more alternatives)
- Diff-in-diff = Even stronger (rules out both place and time explanations)
- Placebo = Strongest (shows the effect is specific to what you're studying)
- All together = Much closer to Version B (causal)

Still not *proof* — we'd need a randomized experiment for that.

But a much stronger case than a single comparison alone.

---

## Slide 30: For Your Final Project

Think about your own analysis:

1. What is your main comparison?
2. What are 2-3 alternative explanations someone could raise?
3. Can you compare to yourself AND someone else?
4. What would be your placebo outcome?

You don't need to implement all of these - but thinking through them will make your analysis stronger and your interpretation more careful.

---

## Slide 31: Summary

**The key insight:** The same comparison can answer a descriptive question (Version A) or begin to answer a causal question (Version B).

The difference is how carefully you've ruled out alternatives.

**For your projects:**
- Be clear about which version you're answering
- Acknowledge alternative explanations
- Consider what additional comparisons would strengthen your case

---

## Session Plan

### Session 1 (Tuesday 12/2): Concepts + Notebook Sections 1-5
- Slides 1-19 (~45 min)
- Notebook through diff-in-diff (~30 min)

### Session 2 (Thursday 12/4): Placebo + Application
- Slides 20-28 (~20 min)
- Notebook placebo section (~25 min)
- Discussion: Apply to your projects (~30 min)
