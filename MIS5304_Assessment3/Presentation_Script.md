# MIS5304 Assessment 3: Presentation Script

**Target time:** about 9 min 30 s (around 1,200 words at a relaxed pace)
**Audience:** non-technical executives, so keep it simple and talk about risk, cost and who's responsible.

---

## Slide 1: Title (about 30 s)

Good morning, everyone.

In 2022 and 2023, three big Australian companies, Optus, Medibank and Latitude Financial, were hacked. Millions of people had their personal details stolen.

Here's the surprising part. In at least one of these cases, the security tools actually raised the alarm. The problem was what happened *after* the alarm.

So today I'll cover three things: what went wrong, which investigation tools really help, and four things I think boards should do next.

---

## Slide 2: Why this matters now (about 45 s)

First, why should we care right now?

Because the problem is getting bigger. Last year, the Australian Signals Directorate, or ASD, dealt with more than 1,200 cyber incidents. That's up 11%. And ASD warned organisations about attacks 83% more often than the year before.

Now look at the three breaches. Optus affected about 9.5 million people. Medibank, about 9.7 million. Latitude, around 14 million records.

Optus and Medibank have both been taken to court by the privacy regulator. Latitude says the breach cost it about 76 million dollars.

So this isn't just an IT problem. It's a money problem, a legal problem, and a trust problem.

---

## Slide 3: Three breaches, three different failures (about 1 min)

Each breach went wrong in a different way.

At **Optus**, the regulator says a coding mistake left an old system open to the internet. It was fixed on the main website, but not on this side system. So the door was left open for years.

At **Medibank**, a contractor's password was stolen. The attacker used it to log in remotely, and there was no second check, like a code sent to your phone. That second check is called multi-factor authentication, or MFA.

At **Latitude**, the attackers got in through a supplier's login. And Latitude was still holding customer records going back to 2005.

One quick note: these are the facts as regulators and official sources report them. Some are still before the courts, so I call them "alleged". I also don't claim any company used a particular tool unless a source says so.

---

## Slide 4: Medibank, the alarm rang (about 1 min 5 s)

This is the most important slide.

Let's follow the Medibank attack step by step. In early August, malware stole a contractor's login. A few days later, the attacker tested it. Around the 23rd of August, they logged in, with no MFA to stop them.

Now look at the red box. On the 24th and 25th of August, Medibank's security software spotted something wrong and sent alerts. But those alerts went to an email inbox, and nobody acted on them.

Over the next seven weeks, the attacker took about 520 gigabytes of data. The incident was only properly looked at on the 11th of October.

So the lesson is this: the tool did its job, but nobody owned the alarm. And research shows security teams get so many false alarms that real ones get missed. That's a risk we can plan for.

---

## Slide 5: Comparing the tools (about 1 min 15 s)

So which tools help? Here are the four main types, in plain terms.

**SIEM** is like a central control room. It collects logs from across the business and spots patterns. It sees the most, but it's expensive and needs skilled people to tune it.

**EDR** watches every laptop and server, and it can cut off an infected device fast. But it can't see what it isn't installed on, like a contractor's home computer or an exposed website system.

**Forensics tools** help us work out exactly what happened and what was taken. That's vital for telling customers and regulators. But the skills are rare, so most companies keep an outside firm on call.

**Threat intelligence** tells us who is targeting our industry and how. It's useful, but only once the basics are working.

The colours show green for good, amber for okay, and red for a weak spot.

My takeaway: SIEM plus EDR is the core. Bring in forensics when needed, and add threat intelligence last.

---

## Slide 6: The framework (about 1 min)

Next, I lined these tools up against the NIST Cybersecurity Framework. It's a common checklist that many Australian organisations use. It has six areas, from Govern through to Recover.

The tools cover the middle well: spotting attacks and responding to them.

But look at the first column, Govern. It's empty. No tool covers it.

Govern means deciding who owns the alerts, how much risk we're willing to take, and paying for basics like MFA. Software can't do that. That's the board's job.

The latest NIST guidance from 2025 says the same thing: responding to incidents should be part of everyday risk management, not just an emergency plan in a drawer.

---

## Slide 7: What would have changed the outcome? (about 1 min)

On the left are the facts. On the right is my own view of what could have helped.

For **Optus**: keep a full list of every system facing the internet, and test it regularly. That would probably have found the weak spot. Watching for unusual amounts of data leaving would have helped too.

For **Medibank**: turn on MFA, and make sure someone owns every alert, day and night. That would likely have stopped the attack, or caught it much earlier.

For **Latitude**: keep a close eye on supplier accounts for odd behaviour, and delete old data you no longer need. You can't lose data you don't have.

And here's the pattern. None of these was really about a missing tool. They were about seeing what you have, protecting logins, and owning the response.

---

## Slide 8: What's changing (about 1 min)

Looking ahead, four things are changing.

First, **AI**. Attackers use it to make scams more convincing. We can use it to sort through alerts faster, but we need to be able to explain its decisions, especially if they end up in court.

Second, **logins are the new front door**. Medibank and Latitude were both about stolen logins. So investigations now depend on login and cloud records, which are often only kept for a short time.

Third, **the rules are getting tougher**. Since May 2025, businesses with more than 3 million dollars in turnover must report a ransomware payment within 72 hours. And since June 2025, people can sue for a serious invasion of privacy.

Fourth, **there aren't enough skilled people**. Most companies can't watch their systems 24/7 on their own, so many will use a managed security service.

---

## Slide 9: Four actions (about 1 min 20 s)

So, what should we actually do? Four actions, in order.

**Number one**, and the cheapest: make someone responsible for every alert, around the clock, and turn on MFA for all remote access, including contractors. This fixes the Medibank problem. It's low to medium cost and can be done in three months.

**Number two**: connect SIEM and EDR, so login, cloud, website and device activity are all watched in one place. This tackles the Optus and Latitude problems. It's a bigger investment, over three to nine months.

**Number three**: be ready to investigate. Have a forensics firm on call, keep records long enough to work out what was taken, and practise your response plan.

**Number four**: only then add threat intelligence.

Each action has a clear owner and timeframe. And if the board wants dollar figures, a method called FAIR can turn these risks into money terms.

---

## Slide 10: Close (about 40 s)

To finish, here are three simple questions any executive can ask on Monday.

One: who owns our security alerts at 2 am on a Sunday?

Two: does every remote login need MFA, including contractors and suppliers?

Three: if we were hacked today, could we tell the regulator within days what was taken?

The bottom line: the right tools matter, but people, logins and being prepared matter more.

Thank you. I'm happy to take any questions.

---

## Delivery tips

- Slow down on the key lines: the hook on slide 1, the red box on slide 4, and the three questions on slide 10.
- Point at the slide as you talk: the red box (slide 4), the empty Govern column (slide 6), the action table (slide 9).
- Don't read word for word. Learn the first line of each slide, then talk naturally.
- Time two full practice runs. If you're running over, shorten slide 5 or slide 8 first.

## Likely questions, with short answers

**"Why not just buy one all-in-one tool, like XDR?"**
No single tool covers everything, especially governance. And at Medibank the tool worked; the problem was nobody acting on its alerts.

**"How do you know Medibank's security software worked?"**
The privacy regulator's court filing says the software raised alerts on the 24th and 25th of August, but they weren't acted on. It's an allegation, but it comes from the official filing.

**"What would your recommendations cost?"**
I gave relative levels, not quotes. Action one is the cheapest. To get real dollar figures, I'd use FAIR, a method for putting a money value on cyber risk.

**"Which recommendation matters most?"**
Number one: owning every alert and turning on MFA. It's cheap, fast, and directly fixes what went wrong at Medibank.
