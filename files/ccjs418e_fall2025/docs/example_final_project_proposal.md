# Example Final Project Proposal

## Part 1: The Proposal

**Student Name:** [Example Student]
**Date:** November 2, 2024
**Course:** CCJS 418E - Coding for Criminology

---

# Do NYC Noise Complaints Spike During Major Sporting Events?
## An Analysis of 311 Call Patterns Around Madison Square Garden and Yankee Stadium

### 1. Research Question

**Main Question:** Do noise complaints to NYC's 311 system increase during major sporting events at Madison Square Garden and Yankee Stadium?

This question matters because understanding complaint patterns around major events can help city agencies allocate resources more effectively. If noise complaints consistently spike during games, the NYPD and 311 system could prepare by increasing staff during those times. Additionally, understanding these patterns could inform event planning and community relations for venues in residential areas. This analysis could benefit 311 operators who handle these calls, NYPD officers who respond to noise complaints, event venue managers who want to maintain good community relations, and residents who live near these major stadiums.

**Supporting Sub-Questions:**
1. What is the baseline rate of noise complaints on non-event days in Manhattan and the Bronx?
2. Do complaints spike more for certain types of events (basketball vs baseball vs hockey)?
3. Which boroughs show the biggest increase in noise complaints during game days?

### 2. Dataset Description

**Source:** NYC 311 Service Requests Database (2023)
**Access:** NYC Open Data Portal - https://data.cityofnewyork.gov/311-service-requests

**Time Period:** January 1, 2023 - December 31, 2023 (full calendar year)

**Dataset Size:** Approximately 50,000 records (filtered to noise complaints only)

**Key Variables (Exact Column Names):**
- `created_date` - Date and time when complaint was filed (format: YYYY-MM-DD)
- `complaint_type` - General category of complaint (we'll filter to "Noise - Residential" and "Noise - Street/Sidewalk")
- `descriptor` - Specific type of noise (e.g., "Loud Music/Party", "Loud Talking", "Banging/Pounding")
- `borough` - Which NYC borough the complaint came from (Manhattan, Bronx, Brooklyn, Queens, Staten Island)
- `created_hour` - Hour of day when complaint was filed (0-23)
- `incident_address` - General location of complaint
- `resolution_time_hours` - How long it took to resolve the complaint
- `agency_name` - Which agency handled the complaint (usually NYPD)

**Data Access:** I have downloaded the dataset and verified it contains all necessary columns. The CSV file is approximately 15 MB and loads successfully into pandas.

### 3. Analysis Plan

#### A. Which Specific Columns Will I Use?

- **created_date** - To identify which complaints happened on game days vs non-game days
- **complaint_type** - To filter the dataset to only noise complaints
- **descriptor** - To break down what types of noise complaints happen (music vs talking vs other)
- **borough** - To compare Manhattan (Madison Square Garden area) vs Bronx (Yankee Stadium area) vs other boroughs
- **created_hour** - To see what time of day noise complaints happen, especially after games end

#### B. What Exactly Will I Calculate?

**Counts (How many?):**
- Total number of noise complaints on game days in 2023
- Total number of noise complaints on non-game days in 2023
- Number of noise complaints by borough on game days
- Number of noise complaints by hour of day on game days vs non-game days
- Number of complaints by type (Loud Music vs Loud Talking, etc.)

**Averages (What's typical?):**
- Average number of noise complaints per game day
- Average number of noise complaints per non-game day
- Average noise complaints per day in Manhattan vs Bronx vs other boroughs

**Percentages (What proportion?):**
- Percent increase in noise complaints on game days: ((game day average - non-game day average) / non-game day average) × 100
- Percent of total noise complaints that come from Manhattan vs Bronx
- Percent of complaints that happen in evening hours (6pm-midnight) on game days

#### C. What Groups Will I Compare?

1. **Game days vs Non-game days** - Do days with Knicks, Rangers, or Yankees games show more noise complaints?
2. **Manhattan vs Bronx vs Other Boroughs** - Do the boroughs with major stadiums show bigger spikes?
3. **Weekday games vs Weekend games** - Is the increase bigger when games happen on weekends?
4. **Evening hours (6pm-midnight) vs Late night (midnight-6am)** - When during the day do noise complaints peak on game days?
5. **Basketball games vs Baseball games** - Do different sports show different patterns?

#### D. Step-by-Step Plan

**Step 1:** Load the NYC 311 data into pandas

**Step 2:** Filter to just 2023 data (created_date between Jan 1, 2023 and Dec 31, 2023)

**Step 3:** Filter to just noise complaints (complaint_type contains "Noise")

**Step 4:** Create a list of all game dates for 2023:
- Knicks games at MSG (41 home games): dates from NBA schedule
- Rangers games at MSG (41 home games): dates from NHL schedule
- Yankees games (81 home games): dates from MLB schedule
- Mark these dates in my dataset as "game_day" = True or False

**Step 5:** Count total noise complaints on game days vs non-game days
- Group by game_day column and count complaints

**Step 6:** Calculate average complaints per day for each group
- Game days: total game day complaints ÷ 163 game days
- Non-game days: total non-game day complaints ÷ 202 non-game days

**Step 7:** Calculate percent increase on game days
- Formula: (game day average - non-game day average) / non-game day average × 100

**Step 8:** Group by borough and count complaints on game days
- Compare Manhattan and Bronx to other boroughs

**Step 9:** Look at complaint timing - group by created_hour on game days vs non-game days
- See if there's a spike in late evening/night hours on game days

**Step 10:** Compare different event types by filtering to specific game date lists
- Knicks game days vs Yankees game days - do they show different patterns?

### 4. Expected Outcomes

**What I Expect to Find:**

I expect to find that noise complaints increase on game days compared to non-game days, but not by a huge amount. My hypothesis is that game days will show a 20-40% increase in average daily noise complaints compared to non-game days. I think Manhattan will show a bigger spike than the Bronx because Madison Square Garden is in a denser, more residential area (Midtown), while Yankee Stadium is in a less dense neighborhood.

I hypothesize that weekend games will show a bigger increase than weekday games because people stay out later and celebrate more on weekends. I also expect that the noise complaints will peak between 10pm-2am on game days, which would be 2-4 hours after most games end, as people leave the venues and go to nearby bars or head home.

It would surprise me if the Bronx showed NO increase during Yankees games, because that would suggest the stadium has zero impact on the neighborhood. It would also surprise me if the increase was over 100%, because that would suggest game days are completely different from normal days.

**How I Might Show My Findings:**

1. **A line graph** showing average noise complaints by hour of day, with two lines: one for game days and one for non-game days. This would clearly show if there's a spike in late evening hours on game days.

2. **A bar chart** comparing average daily noise complaints across the five boroughs, with separate bars for game days and non-game days. This would show which boroughs are most affected.

3. **A table** showing:
   - Total complaints on game days vs non-game days
   - Average per day for each group
   - Percent increase
   - Number of game days vs non-game days analyzed

4. **A second bar chart** comparing different event types (Knicks vs Rangers vs Yankees games) to see if certain sports generate more complaints.

### 5. AI Tool Usage

I used Claude (TerpAI) in several specific ways to develop this proposal:

**Understanding the Dataset:**
I asked Claude: "What kinds of columns would typically be in a NYC 311 dataset?" This helped me understand what information would realistically be available and what analyses would be possible. Claude explained the difference between complaint_type (broad category) and descriptor (specific type), which helped me structure my analysis plan.

**Refining My Research Question:**
My initial idea was very broad: "analyze noise complaints in NYC." I asked Claude to help me narrow it down by asking: "I have 311 data with dates, complaint types, and locations. What's a specific research question I could answer about noise and events?" This led me to focus specifically on sporting events rather than all events, which is much more manageable.

**Checking My Math:**
I asked Claude to verify my calculation approach: "If the Knicks play 41 home games, Rangers play 41 home games, and Yankees play 81 home games, that's 163 total game days. But some dates might overlap - could the Knicks and Rangers both play on the same day?" Claude confirmed that yes, overlaps are possible, so I should count unique game dates, not sum the games. This saved me from making an error in my analysis.

**Understanding Event Impact:**
I asked Claude: "What factors besides the game itself might cause noise complaints on game days?" This helped me think about bars near the venues, people traveling to/from games, and celebration noise - all of which helped me develop my hypothesis about the 2-4 hour delay in peak complaints after games end.

**Validating My Approach:**
I described my step-by-step plan and asked Claude: "Can I do all of this with basic pandas operations like filtering, groupby, and calculating averages?" Claude confirmed that yes, this is all achievable with the skills from class, and suggested I could use boolean indexing to create the game_day column.

Throughout this process, I used AI as a thinking partner to refine my ideas and check my logic, but all the decisions about what to analyze and why it matters came from my own thinking about the problem.

---

## Part 2: What Makes This Proposal Strong

### Why This Example Works

**Focused Research Question:**
- Specific: Not "noise in NYC" but "noise during sporting events"
- Testable: Can clearly be answered with available data
- Interesting: Connects city life, sports culture, and quality of life
- Practical implications: Results could inform city planning

**Realistic Dataset:**
- All column names are typical of real 311 data
- Size is manageable (50K rows is realistic after filtering)
- All required information is present
- Student demonstrates they've thought about data access

**Appropriate Scope:**
- Uses only operations from lectures 4-6: filtering, groupby, basic calculations
- Avoids advanced techniques: no mapping, no geographic calculations, no complex time series
- Calculations are simple but meaningful: counts, averages, percentages
- Comparison groups are straightforward: game days vs non-game days, borough vs borough

**Detailed Analysis Plan:**
- Lists EXACT column names (not vague descriptions)
- Specifies EXACT calculations with formulas
- Provides 10 concrete steps from start to finish
- Each step is achievable with class skills
- Shows understanding of data preparation → analysis → interpretation flow

**Realistic Expectations:**
- Hypotheses are reasonable (20-40% increase, not 500%)
- Acknowledges what would be surprising
- Multiple sub-questions allow for exploration
- Considers alternative explanations (bars, travel, celebrations)

**Thoughtful AI Usage:**
- Shows specific questions asked, not just "I used ChatGPT"
- Demonstrates AI as thinking partner, not ghostwriter
- Used AI to understand data, check logic, refine questions
- Shows iteration: started broad ("noise in NYC") → narrowed to specific question
- Honest about what AI contributed vs student's own thinking

### Common Mistakes Avoided

**❌ Too Vague:** "I will analyze patterns in noise data"
**✅ This Example:** Specifies exactly what patterns (game day vs non-game day) and how to measure them

**❌ Missing Data:** "I hope to find data about..."
**✅ This Example:** Confirms dataset downloaded, lists actual column names

**❌ Unclear Scope:** "I will use advanced analytics"
**✅ This Example:** Sticks to counts, averages, percentages - all from class

**❌ No Real Plan:** "I will explore and see what I find"
**✅ This Example:** 10 specific steps with exact operations

**❌ Weak AI Section:** "I used ChatGPT to help"
**✅ This Example:** Five specific examples of how AI was used, what was asked, what was learned

### Key Lessons for Students

1. **Start Broad, Then Narrow:** Notice how "noise complaints" became "noise during sporting events at specific venues"

2. **Be Concrete:** Every section uses exact column names, specific numbers, precise calculations

3. **Show Your Work:** The step-by-step plan proves you know how to do this, not just what you want to find

4. **Right-Size Your Ambition:** This project is doable in a semester with class skills, but still interesting

5. **Use AI Wisely:** Document how AI helped you think, not how AI did your thinking
