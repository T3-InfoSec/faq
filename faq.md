# Frequently Asked Questions --- Great Wall


[obsegg]: https://www.linkedin.com/posts/lugano-plan-b_luganoplanb-bitcoin-activity-7167881837728493568-LEZk/
[theproblem]: https://x.com/search?q=jameson\%20lopp\%20wrench\%20attack&src=typed_query&f=live
[nocurrentsolution]: https://www.youtube.com/watch?v=MsfR6ZIkzPs&t=2734s
[kba]: https://en.wikipedia.org/wiki/Knowledge-based_authentication
[kprinciple]: https://en.wikipedia.org/wiki/Kerckhoffs's_principle
[privsecplaque]: https://duckduckgo.com/?q=prosegur+verisure+\%22warning+sign\%22+facade\&iar=images\&t=brave\&iaf=type\%3Aphoto
[mhh]: https://security.stackexchange.com/questions/237498/how-does-memory-hard-hashing-passwords-protect-against-brute-force-attacks\#237511
[bipref]: https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki
[tlp]: https://en.wikipedia.org/wiki/Time-lock_puzzle
[gmaps]: https://blog.google/products/maps/15-years-of-mapping-the-world-makes-search-better/
[runningparachute]: https://duckduckgo.com/?q=running+parachute&iar=images&t=brave
[ssssbtc]: https://iancoleman.io/shamir39/
[rewindbitcoin]: https://rewindbitcoin.com/
[wearestillearly]: https://duckduckgo.com/?q=\%22we+are+still+early\%22+bitcoin&t=brave&ia=web
[tacitknowledge]: https://en.wikipedia.org/wiki/Tacit_knowledge
[gwdemo]: https://www.youtube.com/watch?v=bI8fiGmpHR0
[ceilingfrequencyscalling]: https://en.wikipedia.org/wiki/Frequency_scaling

This document aims at covering basic questions about Great Wall protocol and the startup built upon it.

## Table of Contents

1. [General Questions](#general-questions)
2. [Technical Questions](#technical-quesitons)
3. [Business Model](#business-model)

## General Questions

### What problem does your startup solve?
Great Wall, the protocol, app and startup solve the [terrifyingly rising problem of **wrench attakcs** on custody of crypto assets][theproblem].

### How is your approach different from competitors?
Great Wall is, the first to combine 4 crucial information security properties, namely:
  1. **Devicelessness / Stateless / [Kowledge-Based Authentication][kba]:** aka **KBA**. This refers to the attainment of secret at hand, in our case, the private keys of a wallet, is not depending on any physical object except user's own brain, in contrast to PBA (**P**ossession-**B**ased **A**uthentication). Namely, by having access to a piece of information (the 'knowledge', in knowledge-based authentication) that is possible to memorize, user can access their wallet in any device. There is no particular external device, metal plaque, object, physical address that, user depends on, therefore becoming an additional point of failure;
  2. **Individual, non-Shared Custody**: This is the foundational premise of Bitcoin. Compromising on that premise negates the core valeu proposal of Bitcoin / crypto. As our sayings go 'not your keys, not your coins', and 'be your own bank' means you don't rely on anybody else or any company for the custody of your assets.
  3. **Non-Obscurity**: This is a direct consequence of one of the most widely accepted paradigms in cryptology and protocol design, the [Kerckhoffs's principle][kprinciple]. The principle states: 'Knowledge inevitably diffuses, so a security system cannot rely on adversaries' ignorance on how it works, but on the secrecy of each instance.' Put simply: 'A good security system is not one based on a secret trick (that one just *wishes on their lucky star* adversaries never get to learn), but on the secrecy of each user's keys'.
  4. **Coercion Resistance**: It's the main point: to render attempts of using violence or threats thereof on custodians to compel them to give up their stashes (or any private information whatsoever). Not only that, system has to be such that an attacker cannot even threaten the integrity of the user's stash to try to obtain something else.

### Why are this specific combination of 4 properties so important?
 The importance of that specific combination of properties becomes clear once we analyse the shortcomings of systems lacking or compromising each one individually, as described below:
 1. **Individual, Non-Obscure, Coercion Resistant, but not KBA**: This setup describes solutions that are intensive in physical elements, such as [sharding your key][ssssbtc] and distributing shards accross multiple addresses as well as the elements for physical security of each such address, like physical vaults, surveilance, home defense, alarm, geographic separation, etc. The shortcoming of that approach is the **astronomically high costs} of setup, maintenance and update. Put simply: 'Bitcoin is reduced to a glorified gold'.
 2. **KBA, Non-Obscure, Coercion Resistant, but not Individual**: This setup describes solutions in which owner depends on services of shared or delegated custody. As explained above, that completely negates the foundational premise of Bitcoin. Companies offering said services, are themselves liable to state regulations, judicial subpoenas, and are themselves, additional points of failure. Put simply: 'Bitcoin is reduced to a glorified fiat currency';
 3. **KBA, Individual, Coercion Resistant, but based on Obscurity**: This setup consist of relying on a critical secret trick that only works in so far adversary is ignorant about it. Many [modern 'solutions'][rewindbitcoin] unknowingly have that shortcoming, which fundamentally violates the most widely accepted paradim in protocol design: [Kerckhoffs' principle][kprinciple] --- more about that in questions about obscurity. Put simply, it is wishing on your lucky start that the bad guys willing to plan and execute an elaborate and risky endeavor as a kidnapping will just never hear about how your James Bond play works. Don't bet yours Sats (or your life) on that!
 4. **KBA, Individual, Non-Obscure, but Coercion Vulnerable**: This is, basically, vanilla self-custody. Having your keys, but not doing anything in particular to defend them against wrench attacks. "[We are still early][wearestillearly]", the saying goes. For purposes of going by as a needle in a haystack to avoid being attacked, not so much anymore, and, as crypto continues to grow in adoption and value, it will only get worse! So don't wait until problem reaches you (it's a *when*, not an *if*) to solve it!

Combining the aforementioned 4 properties literally means that "1) it's all in your head; 2) in nobody else's; 3) attackers are aware of that; and 4) they are unable to coerce you into giving up said knowledge." By logic, this can only be possible if said knowledge is [tacit][tacitknowledge]. Hence the jargon **T**acit **K**nowledge-**B**ased **A**uthentication **TKBA** to the innovation.

### What exactly does client pay for?
Client does **not** pay for custody in any definition. In one sentence: if clients does setup today and company disapears tomorrow, clients still has as much access to their stash as right after setup. The catch is that running the entire process offline, though possible, is typically very inconvenient. For a small price, user can render their UX much more **convenient**. Let's see how that works in the sessions below.

## Technical Questions

### How does the solution work?
Likewise BIP39, it's just a key derivation scheme that can run 100\% offline in any device. The simple way to describe the Great Wall protocol is to say:
 1. You input an initial seed equivalent in strength to 6 BIP39 words into an hours-(, days-, or even weeks-) long hash;
 2. This hous-(, days-, or even weeks-) long hash yields a seed to your 'private game', which admits a near-infinity of possible 'gameplays';
 3. Bits of your 'private gameplay' of your 'private game' are added to entropy of master secret;

The catch is that the knowledge of 'gameplay' is easy to memorize but impossible to put into words. Because of that, you, alive and well, are strictly necessary throughout the entire process, which can be set up to take hours, days, or even weeks. As a result, stealing your stash becomes at least as difficult as conducting a kidnapping that takes as long.


### What does such *TKBA game* consist of?
**[Zooming in a fractal into a specific object][gwdemo]**. Desired characteristics met by that are:

 1. **Deterministic:** a fixed math formula with a given input will always yield the same fractal no matter the platform;
 2. **Quantifiable:** a simple straightforward calculation ensures the given objects have exact the cryptographic strength needed;
 3. **Familiarity and Ease:** everybody is familiar to the UX of zooming in Google from planetary scale into specific addresses. With [~200 M distinct locations in Google maps][gmaps], selecting one single location is roughly equivalent to 27 bits, which is north of 2 BIP29 words (11 bits each). That puts memorizing the equivalent strength to a conventional 12-words seedphrase at equivalent to locating 6 addresses --- **easy**;
 4. **Tacitness:** Unlike the UX of zooming in to location on planet earth, zooming in into a location in a private fractal, involves using reference points that are all:
  - private --- hence not previously known by the adversary;
  - unlabeled --- the only way to user can (attempt to) refer to them is by (attempting to) describing them;
  - unfamiliar --- yielded purely by math formulas with secret parameters, private reference points' shapes are unlike anything adversaries had seen before
  - similar to one another --- reference points differ from one another with very subtle nuances of position, shape, angle and coloring, which makes them **impossible to describe apart with words**;
 5. **Culturally Neutral:** Also worh mentioning process is not linguistic, or linked to something that might be vary in cultural acceptability accross time and geography. It's purely mathematical, so no cultural barriers to adoption;

Efficacy of method has been anecdotally validated with flying colors.

### How can user decide the duration of their time barrier? Wouldn't an adversary equiped with a setup 1000-X more powerful than your be able to perform your derivation in 1000-th of the time?
Three important concepts are the basis for it:
 1. **sequences of tasks that cannot be computed in parallel:** Many types of sequential computation have the characteristic adding more machines, don't speed up the process. It's similar to how having 1000 marathonists don't allow you to run a marathon in $1/1000$ of the time, only in the speed of the fastest runner.
 2. **frequency scaling barrier:** continuing the analogy between compuation performance of a sequential task and running a race, the 'speed of a runner' is equivalent to the *frequency} of a CPU. For highly technical reasons, since mid 2000's we have reached a [ceiling on frequency scaling][ceilingfrequencyscalling]. Said ceiling is very directly consequence of physics --- the speed of light, limiting how fast a signal can travel, or size of atoms limiting how small a transistor can be, hence,cannot be expected to change.
 3. **memory intensivity:** continuing the analogy even further, there are known techniques to minimize the material advantage a top performing CPU has over an ordinary one, or in the analogy pro runner has over a casual walker. To have the sequential task at hand be intensive in memory access, would be equivalent to equip both pro runner and casual walker alike with a [running parachute][runningparachute]: the top performer would still outperform the casual one, but way less efficiently.

The combination of those three paradigms are widely used in modern technology. They are at the core of design of **offline** key derivation functions like that employed in [BIP39][bipref], [memory-intensive hashes][mhh], and [time-lock puzzles][tlp]. In a nutshell: a memory-intensive sequence with enough iterations will impose a time as long as desired to **any** adversary, at the cost of an UX **only marginally (a few times)** as long.

### Wouldn't it be simpler to have the time barrier consist of blockhain block counting?
In that case, there would be a necessary piece of information published on the blockchain, therefore invalidating the premise of individual non-shared custody. The entire process has to be possible to do offline.

### There are current [solutions also based on imposing a time-barrier][rewindbitcoin]. Why are they inadequate?
The catch is 'What exactly happens / becomes possible to be done after the time barrier?'. If the answer is: 'transaction from a protected address can be redirected to emergency address before $n$ blocks enlapse', this means the system only works in so far adversary does not know how it works, namely it's an obscure system. The problem with obscurity is that not only, knowledge diffusion undermines a security system, but also it makes it backfire. In that example, an educated attacker has incentive to assassinate wrench attack victim to prevent them from performing transaction redirection. Reliance on obscurity, therefore, introduced the incentive for an educated attacker to intensify / aggravate / worsen their attack --- and obviously, there are no reliable ways to prevent wrench attackers form educating themelves ([Kerckhoffs' principle][kprinciple]).

In our case, answer is: 'The time barrier is a necessary condition for loading the interface for user deploying their otherwise tacit knowledge.'. This rather technical statement translates more simply to: 'Time barrier becomes itself, duration in which user alive and well, is strictly necessary to access its stash'. That fact makes wrench attack more difficult to carry out.

### How can user buy improvement in convenience without compromising security properties or true self-custody? If I pay for somebody else to derive my keys, then I no longer have individual custody of them, right?
User doesn't pay to derive the seed to the private game. Instead, he pays to derive a one-time usage key to decrypt locally stored game seed. The outsourced material is insufficient to deriving the private game.

As a consequence of that design, anonymity of user becomes critically important: if wrench attacker Wednesday discovers when client Charlie pays for and receives result of key derivation, she, therefore knows his window of vulnerability to wrench attack. Wanting to maximize his anonimity, Charlie will want to join the largest possible pool of other users, (similarly to first-mover consolidation of a social network).

### Wouldn't a frustrated / distrusting / uneducated wrench-attacker, then brutalize their victims? How to solve that?
Likewise [private security companies warning signs][privsecplaque], users will want to acquire, use and wear branded merchandise to dissuade attackers or would-be attackers. Likewise warning signs, branded merch will educate attackers (and would-be attackers) that victim (and would-be victims) really are well protected. 

Influenced by the myth of Satoshi Nakamoto, our community got overly attached to the idea of security through obscurity. We, however, are way passed the point in which Bitcoiners can simply go by needles in a haystack, and as adoption and value of Bitcoin continue to grow, effectiveness of obscurity will only rapidly drop to zero. We offer the solution: **security through anti-obscurity}.

### It seems like there is an obvious single point of failure in user forgetting either inputs to their setup. How to fix it?
Let's break down this objection into 3 responses:

 1. **There is plenty brain power in a typical user:** Those who were born before in the 90's or earlier will remember: knowing a handful of telephone numbers by heart was commonplace. Moreover: we also do remember a few of them even today, dacades after this brain skill fell in disuse. As few as 5 of them convey as much entropy as a 12 word BIP39 seedphrase.
 2. **Integrated Memory Coach** similar to those in [Anki][https://apps.ankiweb.net/] and [Duolingo][http://duolingo.com/] makes sure user both doesn't forget critical knowledge and doesn't overdo memory exercise, causing usage fatigue. The process of regularly replaying private game to keep memory of private gameplay fresh is great news because it translates to **recurrent payment**, and **habit building**.
 3. **Inheritance:** a stash relevant enough to be defended against wrench attack, is also relevant enough to have its automatic transmission to heirs secured by a protocol setup. Details of that fall beyond the scope of this document, but it suffices to say that it can be implemented as an additional feature seamlessly synergized with the main one of coercion resistance. Moreover, the habit-building effect of integrated memory coach will propagate from heir to testator to heir in a given family.

### Is the expected UX, by itself, not too tiresome?
We are talking about a half minute game-like UX, automatically notified and replayed on average once a week. Different, but definitely not much to ask considering the benefits.

### What is so bad about obscurity, really? How to avoid it? Can you provide examples?
Obscurity is the characteristic of a system relying on / necessitating the ignorance of its adversaries about it, in order to function. By logic and common sense, one cannot seriously **publish** a new system and expect bad guys will never learn about it.

Reliance on obscurity, is however even worse than just the mere false sense of security. Below are a few examples in which obscurity actually backfires:

 1. **plausible denial:** Legit user, say, Daniel denies to wrench attacker, say, Wednesday having what she seeks, or claims having much less --- which is called to use a *decoy wallet*.
 
 If Wednesday is aware of how plausible denial techniques and decoy wallets work she may keep brutalizing Daniel not only until but also beyond the point of he giving up everything he has, motivated by belief he is in denial. In other words, obscurity gives incentive to indefinite brutality.
 
 On the other hand, an adversary to our anti-obscure system is made readily aware that harming victim leads to no material gain at all.
 
 2. **cancellable transaction:** Legit user, say, Albert, keeps stash in an programmable UTXO that: A) ordinarily takes a large quantity of blocks to be emptied; and B) a transaction moving Bitcoin away from it can, before maturity block is reached, be redirected to obscure address or aborted.
 
 As explained above, an educated wrench attacker would have the material incentive to assassinate Albert as to prevent him from aborting theft transation.
 
 Once more, the adversary to our anti-obscure system needs their victim alive and well during the entire process which, if longer than they are able to abduct victim for, will be pointless anyway, so all incentives are in the direction of desisting the attack.

### Can the system be used for other currencies?
Protocol is merely a key derivation scheme. Resulting secret can be converted into any secret user wants to protect against wrench attack. That includes key to any wallet, any digital secret, or singature scheme, password manager, or even physical vaults.

## Business Model

### What exactly is the business model?

Company is a marketplace between anonymous clients of key derivation and providers of key derivation. Clients want to stay anonymous in order not to reveal their window of vulnerability (namely, the span of time in which their time-locked virtual vault is open or close to be opened).
Another venue is to sell branded merchandise. Likewise [warning signs of private security companies][privsecplaque], branded merchandise will educated attackers and would-be attackers that their victims (and would-be victims) really are well protected, and that attempts on wrench attacking them are futile.

### Is there any first-mover advantage or lock-in mechanism?
Absolutely! Users want to maximize their anonymity. The more anonymous they are, on buying their key derivation, the less likely it is they are wrench-attacked right upon receiving their keys (which would anull their time barrier). By adhering to first mover, new users make sure they blend in the largest possible pool of other users, therefore maximizing their anonymity. This is similar to having the tendency to choose the largest social network.

### How this UX improvement purchase happen?
Best way to implement it, in terms of maximizing security properties is:
Lightning Network wallet connects through Tor with company's Linghtning Network node, submits derivation request through Lighning Network connection 

Less sophisticated and more conventional subscription, connection and payments methods may be made available to less advanced users for usability / securty tradeoff, without negating the premise that derivation request and payment still being anonymous. Example: user may sign up with email and conventionally pay with credit card and trust the company not to leak their secrecy.

### How will clients feel about that?
Extremely positively: unlike fremium games that charge for adfree experience, the gain in UX quality through is **not** product of an artificially imposed arbitrary inconvenience, that user is bored / annoyed into paying to get rid of. Necessity to recurrently perform a hardware-intensive hours-, days-, or even weeks-long computation arises as a direct logical consequence of TKBA. It is, by design, totally possible to do that all by oneself. But, for a small price (operational cost plus markup), one can make the experience not be burdensome by outsourcing it to agents with more economy of scale. Also, it's critically important that such outsourcing happens anonymously. Thus, a first-mover consolidating anonymous marketplace for that service becomes a natural solution. Decision to adhere to that marketplace as client, therefore, feels fair and natural.


### What are the customer acquisition strategies?
The main one is **affiliate marketing**. Approach has several precedents in many similar products and services in the same community.


### Are payments recurrent?
Yes. User needs to regularly replay their 'private game' to keep memory of their 'private gameplay' fresh. That is ensure by the aforementioned integrated memory coach, which translates to user regularly paying for derivation of one-time usage keys.


### Are there ways to minimize user churn?
Yes. Ease to use, gamefication of UX, habit consolidation of recurrent playing of 'private game', given by necessity to consolidate memory, and ensured by integrated memory assistant. On top of that, there is the fact of the importance itself of the service: security against physical violence and theft of large amounts --- a good benchmark for user churn would be that of conventional private security companies. Finally, habit creation from heirs and testators in a given family tend to propagate by example and peer presure. Example: children reinforce mom and dad usage of the system so to protect their inheritance against wrench attacks.


### Where can I learn precise details of valuation, and budget projection for the first years?
In our [executive summary][https://tr.ee/gwxs].
