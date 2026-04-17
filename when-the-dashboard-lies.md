# When the Dashboard Lies

*How to fix systems that break down while scaling up*

When a system is visibly broken, fixing it is straightforward. The hard case is when everything looks fine.

Files were moving. Deadlines were being met. Quality scores exceeded industry benchmarks, and our executive sponsors were satisfied. By every operational metric, the enterprise localization program I'd been brought in to relaunch was performing well.

But the people closest to the work told a different story. Regional teams in Asia were dissatisfied with the output. Last-minute source changes were creating friction across product and services. Translation queries were piling up, deliveries were slipping to the wire, and most stakeholders had quietly concluded that the translators were to blame.

They weren't. The translators were a symptom. The system itself was the problem — and the same operational metrics that had reassured leadership were masking it.

## The Setup

I'd spent years as a linguist on an in-house localization team that served three languages — Chinese, Japanese, and Korean — and was never larger than twelve people. When I was tapped to manage the relaunched Enterprise Localization program, the scope was dramatically different: sixty target languages within six months, expanding to one hundred within two years, with all translation work contracted to a single external vendor.

The transition itself got off to a difficult start. The original plan had called for a gradual handoff, but an executive decision compressed it to weeks. The in-house team, colleagues I'd worked alongside for years, was dissolved with two weeks' notice and reassigned to other positions. The knowledge they carried — about our content, our customers, our quirks — didn't transfer cleanly. We had arranged a three-day onsite in Tokyo for knowledge transfer, which felt productive at the time, but a lot of that knowledge was the kind that moves slowly, through questions and small corrections over months of working together. After the abrupt transition, some of my former colleagues weren't sure whether they could still trust me. I hadn't known it was coming either, but that wasn't always believed. So the informal knowledge transfer I'd been counting on was inconsistent at best.

On top of that, the product portfolio had shifted toward everyday patients and users rather than the clinical researchers our previous products had served, raising the bar for tone, clarity, and regulatory compliance. Leadership also had high expectations for neural machine translation (NMT), seeing it as a path to both speed and cost savings.

We had what looked like a scalable model: a capable vendor, a translation-management system (TMS), translation memories, defined workflows, and a new vendor solution architect who had spent three days with me mapping out our processes and pain points. The program she designed looked resilient on paper.

## The System That Appeared to Work

When we put the new program into operation, it functioned in process terms. Files were ingested and returned correctly. Language quality scores exceeded the industry benchmark for life sciences across every language we tracked. Our monthly reporting was professional and consistent, with clean charts and clear metrics. Leadership was pleased.

But underneath the clean reports, the localization process was intensely labor-intensive. Translators were raising a high volume of queries to content creators, which delayed deliveries and frustrated everyone involved. Our APAC colleagues were consistently dissatisfied with the work product — not because it was incorrect, but because it didn't reflect the voice and register they expected, and didn't harmonize with what had been published before. Product and services teams felt overburdened by last-minute requests and constant back-and-forth. And most stakeholders, seeing that every project involved a rush of queries and a deadline scramble, blamed the vendor's translators.

The localization system was functioning, in that it was turning inputs into outputs in line with the roadmap. We weren't getting acceptable business outcomes.

## Finding the Real Problems

When I stepped back and looked at how the localization program fit into the larger product ecosystem, four root causes came into focus quickly.

The first was input quality. Translation memories and terminology databases had been poorly maintained for years. Data was fragmented — values missing, duplicated, or conflicting, with inconsistent labeling and references — which made them nearly useless both to human translators and as training inputs for NMT engines. Source files arrived through a combination of GitHub downloads and Jira attachments, with version control disappearing along the way. Context was sparse, usually limited to partial screenshots that covered only some of the strings being localized. And because the definition of done for resource files hadn't been written with localization in mind, strings that shouldn't be translated were exposed, and syntax characters appeared in text without escaping. Translators were left to make judgment calls on the fly or escalate issues as queries, both of which cost time and accuracy.

The second problem was tight coupling between fragile systems. Localization teams were accustomed to agile projects with frequent source-file revisions, but our setup made that kind of flexibility extremely costly. Source changes were often applied to projects already in process, without a clear handoff or even a comment on the Jira ticket. And because the workflow depended on manual file movement across GitHub, Jira, and the TMS, volume growth didn't just add work — it multiplied coordination overhead. Comments on individual tickets sometimes ran into the dozens. Rework was frequent, turnaround times extended, and the people doing the manual checking had no way to distinguish a genuine emergency from a routine update.

The third problem was unclear ownership of quality. Regional teams had strong preferences but no formal authority. The vendor was responsible for delivery but not empowered to resolve ambiguity on translation choices. Product teams weren't accountable for localization readiness or for the downstream impact of source changes. This meant that quality was subjective, disagreements surfaced late, and there was no durable record of decisions that had already been worked out. The same arguments recurred on project after project.

The fourth problem was that issue resolution was informal and left no trace. Translator queries were frequent but not systematically tracked. Stakeholder dissatisfaction surfaced through side conversations rather than structured channels. Decisions weren't captured for reuse. Stakeholders could see the same issues recurring, but the system had no memory, so the issues weren't categorized or addressed at the root.

One additional constraint deserves mention. Leadership had prioritized NMT adoption, and the vendor was eager to pilot it. But when we ran the tests, the results were clear: our existing databases were too small and too compromised to produce edit distances that would make NMT-assisted translation faster or cheaper than manual translation. We were being asked to adopt a technology that our own data wasn't ready to support. I documented this carefully and recommended deferring NMT until our translation memories and terminology databases reached a usable standard — a tradeoff between short-term expectations and long-term performance that we ultimately persuaded our executive sponsors to accept, because we had the metrics to back it up.

## Fixing the System

What we needed wasn't more people or effort. It was better-designed systems — ones that surfaced problems early, distributed authority clearly, and retained the decisions they produced.

We started with inputs, because everything downstream depended on them. I worked with the vendor's language quality lead to clean and realign the translation memories and terminology databases, establishing rules for ongoing maintenance so improvements would persist rather than degrade. I introduced localization-readiness criteria for different content types, covering file structure, formatting, and context requirements. We pushed for access to Figma designs instead of screenshots, which gave translators genuine visibility into how strings would appear at runtime. Over time, these changes reduced ambiguity at the point of translation: ad hoc calls about localization issues fell by 50%, and bugs reported by international customers fell by 40%.

We then codified handoff procedures at each phase of the workflow. Jira wasn't a great communication tool, but it had the advantage of keeping localization work visible within the main product development stream. We introduced templates for ticket description fields and naming conventions for file attachments, which reduced the version-control errors that had been quietly multiplying.

On quality ownership, we established what we called a voice-of-customer model: each regional office designated a localization liaison for each language, and those stakeholders worked directly with the vendor's language leads. Their decisions were captured in the terminology database and style guide, creating a consistent standard and reducing the recurring debates over translation choices that had previously slowed delivery.

We also built more structured mechanisms for tracking issues and decisions. The vendor was developing a query-management system, and we offered to pilot it. It allowed us to track translation questions and their resolutions, reuse those decisions on future work, and generate metrics that let us categorize query types and identify upstream fixes. This was the piece that addressed the system's lack of memory most directly.

As volume continued to grow, it became clear that UI localization specifically required dedicated tooling. Because I had maintained analytics from the start of the program, I had the data to make the case. We implemented the Lingoport suite, which provided linting for source files, agile project tracking, and automation of certain quality-assurance steps. This reduced the reliance on manual file handling and caught issues earlier in the process, before they propagated downstream. On-time deliveries across product lines rose to 98%, while queries and rework fell by 30%.

## The Harder Work: Getting People On Board

None of the process changes would have taken hold without sustained effort on relationships and communication — and this is where I'd push back against any framing of change management as a separate workstream. It wasn't. It was woven into everything.

On the formal side, I delivered an internal webinar on localization readiness, covering process flows, intake criteria, quality standards, and real examples of failures and what they had cost. I followed that with shorter presentations embedded in existing team meetings for portfolio leaders and product teams, so the information reached people in their own context rather than asking them to come to mine.

On the informal side, I started reaching out to stakeholders more regularly with unsolicited small updates. A message saying "the PM has confirmed the translators haven't raised any questions on this one yet" took thirty seconds to send and did two things at once: it gave the stakeholder genuine reassurance, and it kept me close to what was actually happening in each project. One implementation consultant responded to one of these messages by mentioning that she'd heard a customer was going to request a custom training course. By the time we formally received the assignment months later, I'd already briefed the language leads on the content domain.

I was also realistic about what I couldn't change. The company had a siloed culture — I'd been told on my first day that cross-functional alignment would require constant effort, and that had proven accurate. I was good at finding shared values on individual projects, but I knew that organizational mindset around global readiness wouldn't shift quickly. Some manual handoffs remained because we couldn't restructure engineering workflows fully. Design access improved but was never complete. These were real constraints, and acknowledging them explicitly — rather than pretending the program was frictionless — was part of what made the relationships with executive sponsors durable.

## Results

Within one year, the impact was measurable. UI source word count increased by a factor of four, while localization costs increased by only fifty percent — reflecting genuine efficiency gains rather than cost-cutting. The system was handling significantly higher volume without proportional increases in effort or error.

Turnaround times became more predictable. Friction among product teams, regional stakeholders, and the vendor decreased. Issues that had previously recurred were less likely to repeat, because decisions were now captured and integrated into process rather than residing in individual memory.

## The Lesson

Adding capacity doesn't fix a system that isn't designed to surface its own problems. Vendors can absorb volume, but they can't compensate for unclear authority, fragmented inputs, or workflows that punish transparency. What those things require is a system designed to keep teams aligned, bring issues forward before they propagate, and retain the decisions it produces.

When scaling breaks down, the first place to look for failure points is at the interfaces: between teams, between systems, and between processes. That's where assumptions go unexamined, handoffs lose information, and accountability quietly disappears. Fix the interfaces, and the rest often follows.
