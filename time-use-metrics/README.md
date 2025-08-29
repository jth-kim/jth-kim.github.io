# Personal Time-Use Metrics for Informed Decision Making
<br>

> **Any measure used for control is unreliable.** — Goodhart's Law

Having learned that what gets measured gets improved, my younger self enthusiastically embarked on a journey of self-knowledge: time tracking to understand how my days actually looked, and to grapple firsthand with the uncomfortable revelation of just how little deep work a person naturally does without externally enforced consequences. Over five years of experimentation I learned that the road to inappropriate optimisation was paved with the combination of measurement with targets. I learned of the ease with which a metric can become a leveraged dopamine hack (Goodhart's Law) if one fails to prevent structural noise from being smuggled, often unconsciously, into the signal which must remain pure if it is to serve as a reliable compass. Such corruption, of course, can only lead to collapse of the paradigm, and I witnessed many collapses of my little towers of Babel.

After another five years of consistent tracking (and fallen Babels), I'd attained productivity-satori: I came to know that DGP samsara is to metric nirvana as yin is to yang. I also came to know discipline - both in regard to technical capacity and the equally necessary spiritual vigilance, giving me the courage to again attempt a metric based decision making tool. This time, I built the tower such that my metrics will either be ignored (un-gamed) or remain honest (un-gamed). It won't reach into the heavens, but I think it will stand the test of time. 

I present to you my Time Oracle ☯️


<figure>
  <img width="300" height="300" alt="closeup" src="https://github.com/user-attachments/assets/82d6dbb5-3ad6-42e4-865d-788e5ef46a3d" />
</figure>

Its an iOS widget that draws data from Toggl:

<figure>
  <img width="4470" height="2366" alt="widget-screenshot" src="https://github.com/user-attachments/assets/36448b5b-450a-492d-beeb-eead762ab3c5" />
  <figcaption>Subset of the data. You can see a holiday, an intense period, and evolving priorities throughout.</figcaption>
</figure>


## Objective
Developed a system to process Toggl time tracking data into un-gameable metrics to inform in-the-moment decision-making, visualized on an iPhone widget. Make thresholds dynamically adjusting to change baselines to reflect transitory epochs of varying intensity.

## Method
- Tracked time use in Toggl (habit etched into spine from years of time tracking / automated with Siri shortcuts)
- Fetched Toggl time entries via API.
- Merged datasets, produced tag suggestions, heat scores (historical / today), and dynamic references.
- Implemented dynamic thresholds: Heat indicator adapts baseline based on prior performance.
- Integrated with Supabase for nice storage and daily updating.
- Feed to Scriptable (JavaScript app) for widget rendering on iOS.


## Plots and Widget

<figure>
  <img width="800" height="317" alt="download" src="https://github.com/user-attachments/assets/fe65d86a-8cc2-4b0d-8022-0e67a9c08ca9" /><br>
  <figcaption>Same totals data as above, but plotting each weekday separately.</figcaption>
</figure>

## Visualization
<table style="width:100%; border-collapse: collapse;">
  <tr>
    <td style="text-align:center; padding:10px;">
      <img width="409" height="879" alt="fri" src="https://github.com/user-attachments/assets/e4c039bf-a86e-47dc-b179-9d06d84cd209" /><br>
      <figcaption style="text-align:center;">Friday data</figcaption>
    </td>
    <td style="text-align:center; padding:10px;">
      <img width="409" height="879" alt="sat" src="https://github.com/user-attachments/assets/db1fdcb7-8d91-41d7-a1fb-0349a4c365e6" /><br>
      <figcaption style="text-align:center;">Saturday data - day off as you can see</figcaption>
    </td>
  </tr>
</table>



## Widget Anatomy


<img width="300" height="300" alt="closeup" src="https://github.com/user-attachments/assets/82d6dbb5-3ad6-42e4-865d-788e5ef46a3d" />

Taking a closer look at the Saturday screenshot, from top to bottom: 
- First line: Tag suggestions, essentially recommendations for what to work on today. Each tag is associated with a verb. "Coding" in this case, recommended for 201 minutes. The little circle fills up thorugh the day as I work on it. It dynamically suggests 1 or 2 based on recent working patterns. Saturday is typically a day off, so it suggests only 1 tag.
- Second line: Heat indicator, read right to left it displays 13 prior days + today for the indicator values. The values of the indicator are translated into braille characters with color to indicate heat. More dots = more heat. The furthest left character represents today's value, and it updates through the day as I accumulate time tracked. Yes, how astute your observation is; the past series values adjust with today's values, idk, I tried it both ways and prefer it as is. Maybe because fatigue / momentum aren't a flow but a stock? so it 'feels' more accurate? Maybe that's bad practice...
- Third line: The heat indicator of line 2 is relative, and so doens't suggest anything about absolute quantities of time, so this line gives some orientation. The base value is the quantity of time tracking required to leave the dynamic thresholds unchanged. Upper and lower plus-minus correspond to the threshold where the braille colour from green to red or blue.
- Fourth and fifth line: Same as the prior two lines, but for the week-on-week data. I tried using the braille here, but it looked weird, So I switched to column bar characters.

## Findings
Here's what I found after 6+ months of use:
- Having outputs directly presented on iPhone home screen means I'm up to date with how my day compares to prior days, prior weekdays (n previous Mondays) and the average day compared to some window-length of prior days.
- Identified patterns that led to short-term exhaustion and sustainable intensity levels, which also inform tag suggestion mechanism updates.
- The recommended durations attached to suggested tags are almost always ignored.
- Daily "heat intensity" plot is the most influential tool, motivating action when things get too cool, and rest when things get too heated.
- Weekday totals are insightful too, providing a sort of narrative hue to each weekday.
- Week-on-week heat intensity is surprisingly uninformative.
- Dynamic thresholds are encouraging during high-intensity periods and easy to ignore when overworked.
- Constructed distributions of productive hours per day, revealing productivity patterns day-to-day and week-on-week.

## Tools

Python (pandas, matplotlib, scipy, statsmodels, requests, supabase)\
Scriptable (iPhone JavaScript app)\
Supabase (data storage/updates)\
Toggl (time tracking)\
The Tyranny of Metrics by Jerry Z Muller (satori catalyst)
