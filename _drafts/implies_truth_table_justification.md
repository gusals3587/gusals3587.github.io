---
layout: post
title: "Utilitarian justification for the truth table of 'implies' operator"
category: blog
tags: math logic
---

# ditched for now
I need an example pair of mathematical statements p and q that's
1. p needs to be invalid on some "exotic" choice of axiom (eg non-euclidean geometry vs euclidean geometry)
2. q can be right even in the choices of axiom that makes p invalid
3. the really hard part; p and q has to be elemantary (undergraduate or lower)

there doesn't seem to be that much overlap when even the notion of axiom is not really high school level anyway.

<hr>

The truth table of p $\to$ q is as follows.

|p|q (presuming p)[^1]|p $\to$ q|
|:-:|:-:|:-:|
|T|T|T|
|T|F|F|
|F|T|T|
|F|F|T|

Now, it's usually the part where p is "False" that trips people up. Because, why would you even think about the implication of an assumption if that assumption is false to begin with? Well, to find the reason the truth table is defined as the way it is, let's think about the "utility" of the word implies

#### What should imply($\to$) do?

implies, expressed in logic as $\to$, is used in logic generally for [modus ponens](https://en.wikipedia.org/wiki/Modus_ponens). That is, in an axiomatic system, if you assume p, p$\to$q then by modus ponens you should be able to deduce q.

p  
p $\to$ q
<hr>
q

So, it makes sense that the part of truth table where p is true is defined the way it is, because if you thought p is true, then p $\to$ q is true, the only row left on the truth table is when q is true, so q has to be true!

Now comes the difficult part, how should you think about the implies operator when the assumption is false?

Well, it should atleast do one thing, it shouldn't tell us anything about the validity of q

#### How to think about implication when assumption is false

I'll use two examples, since those usually help when explaining, one is "philosophical"[^2] and one is mathematical.

Example 1.  
p: it rains  
q: I wear boots

they both need to be elemantary and easy to demonstrated to be associated
p also needs to true or false depending on what axioms you have
q needs to be a theorem which is *can be* true even if p is removed
Example 2.  
p: (euclidean distance function) the distance between two points on a two dimensional euclidean plane is $\sqrt{(x_2-x_1)^2 + (y_2 - y_1)^2}$
q: (Pythagoras theorem) the square of the length of the hypotenuse in a right triangle is the sum of the squares of the other two lengths  

For example 1, let's just wave our hands and say p $\to$ q is true, even though anybody can raise a counterpoint in 2 seconds[^3].  
For example 2, I'll just leave that as an exercise to the reader.

Now, there's one feature of p $\to$ q that we should keep in mind, it's that the validity of p $\to$ q doesn't mean anything about the validity of p.
That should make sense, just because if I know if it rains, I wear boots, doesn't mean that it's raining right now.
Likewise, just because I know the Pythagoras theorem, doesn't mean that it's always gonna be true. Maybe I'm working with some weird metric. Keep this in mind.

Anyway, in both of these examples, p $\to$ q is true, it's just that in my system for deduction, I may not assume neither p or q. It may even be the case that I, in my train of thoughts, decided that p is false in whatever context I was thinking in. (maybe I was solving a math problem, or pondering about what to wear outside)
So, if p is false what should I be able to do?

Well, even if p $\to$ q itself is true, since p is false, p $\to$ q should not tell us **anything** about the validity of q!
In example 1, it means that even though it's not raining, I still may or may not boots (I never it had to be *rainboots*, so maybe I want to wear some leather boots)
In example 2, it may mean that $ a = 2n, a \neq 4n $ or not! The validity of q is still an open question!
What does this mean in the truth table? Well, it means that in the part where p is false, p $\to$ q would always have to be true *or* false. If it's always false when p is false, that means axiom p $\to$ q and ~p is 'incompatible'[^4] since there is no case in the truth table where both of them (p is false and p $\to$ q is true) can happen at the same time. If it's always true... when then we're done, aren't we?

So we narrowed down the possibility, when p is false, either p $\to$ q is always true or p $\to$ q is always false

#### Final nail

Here comes the final part. Remember that p $\to$ q shouldn't tell us anything about the validity of q? What would happen if p $\to$ q is false when p is false?

|p|q (presuming p)|p $\to$ q|
|:-:|:-:|:-:|
|T|T|T|
|T|F|F|
|F|T|F|
|F|F|F|

When you presume p $\to$ q, you can find out that p is true!
This is the final nail in the coffin. Because p $\to$ q has to  
1. not tell us anything about the validity of q when p is false  
2. not tell us anything about the validity of p by itself  
3. (implicit) *do* tell us about the validity of q if p is true

The only possible truth table was the one introduced at the beginning above.

#### Reductio ad absurdum

One consequence of accepting the truth table is that reductio ad absurdum can also be justified.

$$(~p\to p) \to p$$

With [the law of excluded middle](https://en.wikipedia.org/wiki/Law_of_excluded_middle), the only way $~p\to p$ is true is if ~p is false and p is true. So $~p \to p$ can be *shown* to be true, **without** presuming about the truth value of p or ~p. Then p has to be true[asterisk 6]

|p|q (presuming p)[^1]|p $\to$ q|
|:-:|:-:|:-:|
|~~T~~|~~T~~|~~T~~|
|T|F|F|
|F|T|T|
|~~F~~|~~F~~|~~T~~|

##### More resources

for more interested, you can check out [Now retired Prof. Ikenaga course notes on math proof that was about truth tables](https://sites.millersville.edu/bikenaga/math-proof/math-proof-notes.html)  


<hr>

[^1]: One thing that I always see is that you implicitly assume p when you want to find the truth value of q in that truth table, not making that explicit implies operator look like it's the same thing as AND or OR. And although it's technically a binary operator just like those two, it's different in that it has to make an assumption about the relationship between p and q when determining their truth values, whereas AND and OR doesn't really require them.

[^2]: the reason I call it "philosophical" is these are usually the kind of example you would see in philosophy, the problem I always have with these is that they require so many "messy" human context and implicit assumptions. In other words, these examples would not be suitable to a turing machine. And sure, these symbols and rules were initially created for humans, not machines, but human culture always felt so malleable and open for misinterpretation, that I think it's always healthy to include a mathematical example that feels a lot more concrete and well-defined.

[^3]: Especially since I don't actually own a pair of boots

[^4]: If you immediately became uncomfortable, keep reading, I'll deal with it later

I was tempted to use a more 'famous' one, like the Riemann hypothesis and it's many implications or the Taniyama–Shimura conjecture and the Fermat's last theorem, but I decided a pair of theorem that's a bit more elemantary, less flashy, and still easy to recognize the relationship of would make a better example for demonstration.

[asterisk 6]: Some may think that you can prove ~p by proving $~p \to p$ is false, unfortunately, because of [principle of explosion](https://en.wikipedia.org/wiki/Principle_of_explosion) basing any statement from a **false** statement is meaningless. Since you can prove any statement by that method anyway.
