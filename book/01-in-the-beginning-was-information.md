---
title: "1 · In the Beginning Was Information"
---

# 1 · In the Beginning Was Information

> *"And God said, Let there be light: and there was light."* — Genesis 1:3
>
> *"The fundamental problem of communication is that of reproducing at one point either exactly or approximately a message selected at another point."* — Claude Shannon, *A Mathematical Theory of Communication* (1948)

**In this chapter** — *Theology:* creation by speech; the Logos of John 1. *Information science:* what Shannon's theory measures, and what it deliberately leaves out. *Philosophy:* speech-act theory and the question of whether reality is, at bottom, informational.

## Creation by speech

Genesis opens not with a struggle, as the Babylonian creation epics do, but with a voice. Ten times in the first chapter the text says *"And God said"* — a count old enough that the Mishnah remarks on it: *"With ten utterances the world was created"* (Avot 5:1). Light, sky, seas, life: each arrives as the fulfillment of a sentence. The psalmist compresses the whole doctrine into one line: *"For he spake, and it was done; he commanded, and it stood fast"* (Psalm 33:9).

The philosopher J. L. Austin gave the twentieth century a name for sentences that do not describe a state of affairs but *bring one about*: **performatives**. "I now pronounce you man and wife" doesn't report a marriage; it makes one. Austin noticed that human performatives are fragile — they fail if the speaker lacks authority or the conditions aren't met. Genesis 1 presents the limiting case: a speaker whose authority is absolute, whose performatives cannot misfire. *"My word... shall not return unto me void, but it shall accomplish that which I please"* (Isaiah 55:11). In the grammar of Scripture, God's word is not commentary on reality. It is the cause of it.

Hebrew quietly agrees. The word **davar** means both *word* and *thing* — the same noun covers the spoken and the actual. Where English must choose between "the word of the LORD" and "the matter," Hebrew doesn't. A language in which words and things share a name is a language already committed to the idea that speech is load-bearing.

## What Shannon left out

In 1948 Claude Shannon founded information theory with a definition of startling austerity: information is the resolution of uncertainty, measured in bits. His theory tells you how much channel capacity a message needs, how much it can be compressed, how much redundancy defeats how much noise. And it does all this by ignoring something on purpose: *"These semantic aspects of communication,"* Shannon wrote, *"are irrelevant to the engineering problem."* To the theory, a psalm and an equally long string of static may carry the same number of bits.

His collaborator Warren Weaver immediately mapped what had been set aside, distinguishing three levels of the communication problem: **A**, the technical (were the symbols transmitted accurately?); **B**, the semantic (did they convey the intended meaning?); and **C**, the effectiveness level (did the meaning produce the intended effect?). Engineering solved level A with mathematics. Levels B and C remain open — and they are precisely where theology and philosophy live. Scripture is explicit about operating on all three: it is concerned that the words be preserved exactly ([Chapter 5](05-the-canon-an-error-corrected-channel.md)), that they be understood (*"have ye understood all these things?"*, Matthew 13:51), and that they accomplish their effect (Isaiah 55:11 again — a level-C claim if there ever was one).

This is the founding asymmetry of our whole subject: **information theory measures surprise; it cannot measure significance.** Any account of meaning has to be imported from outside the mathematics. The question is from where.

## It from bit — or it from Word?

The physicist John Archibald Wheeler proposed that the deepest layer of physics might be informational — *"it from bit"*: every particle, every field, deriving its existence from yes/no questions and the answers they elicit. Philosopher Luciano Floridi has built an entire philosophy of information on related intuitions. The proposal is seductive to the theologically minded, and the temptation should be named: it is *not* what John 1 says.

*"In the beginning was the Word, and the Word was with God, and the Word was God."* John writes **Logos** — a term with a deep Greek résumé (Heraclitus's ordering principle, the Stoics' rational structure of the cosmos, Philo's intermediary) — and then does something no Greek philosopher did: he gives it a face and a mother. The claim of John 1 is not that the universe is made of information. It is that the universe is made *by a communicator* — that personhood, not pattern, is at the bottom of things. Bits are the residue of acts of saying; in the beginning was not the bit but the Speaker. The difference matters, and [Chapter 10](10-the-word-made-flesh.md) hangs everything on it.

<details markdown="1">
<summary><strong>Closer Look — Leibniz: binary arithmetic as a picture of creation</strong></summary>

Centuries before computing, Gottfried Wilhelm Leibniz — co-inventor of calculus and inventor of binary arithmetic — saw theology in his 1s and 0s. In 1697 he proposed a commemorative medallion celebrating binary, with a motto to the effect that *one suffices to derive all things from nothing* ("omnibus ex nihilo ducendis sufficit unum"). For Leibniz the binary system imaged creation *ex nihilo*: every number generated from unity (God) and nothing. The conceit is charming and should be held loosely — but it is a reminder that the founders of the information age were asking theological questions from the start, not smuggling them in later.

</details>

<details markdown="1">
<summary><strong>Closer Look — Psalm 19: a broadcast without words</strong></summary>

*"The heavens declare the glory of God... There is no speech nor language, where their voice is not heard. Their line is gone out through all the earth"* (Psalm 19:1–4). The psalm describes what theologians call *general revelation* in frankly transmissional terms: a signal continuously broadcast, omnidirectional, crossing every language barrier because it uses none. Paul cites this very feature as the reason no one can claim they never received the message (Romans 1:19–20; he quotes Psalm 19 in Romans 10:18). Then the psalm pivots at verse 7 to *special* revelation — *"the law of the LORD is perfect"* — moving from broadcast to addressed message. Two channels, one Sender.

</details>

## Workbench: the Entropy Lab

Shannon entropy measures the average surprise per symbol in a message. Try it (this tool runs on the published site):

<div style="border:1px solid #555; padding:1em; border-radius:6px;">
<p><strong>Entropy Lab.</strong> Paste any text — a verse, a headline, keyboard-mashing — and measure its character-level Shannon entropy.</p>
<textarea id="entropy-input" rows="3" style="width:100%;">And God said, Let there be light: and there was light.</textarea>
<p><button onclick="technecyEntropy()">Measure</button></p>
<p id="entropy-output"></p>
</div>
<script>
function technecyEntropy() {
  var s = document.getElementById('entropy-input').value;
  if (!s.length) { return; }
  var freq = {};
  for (var i = 0; i < s.length; i++) { freq[s[i]] = (freq[s[i]] || 0) + 1; }
  var H = 0;
  for (var c in freq) { var p = freq[c] / s.length; H -= p * Math.log(p) / Math.log(2); }
  document.getElementById('entropy-output').textContent =
    s.length + ' characters, ' + Object.keys(freq).length + ' distinct symbols, ' +
    H.toFixed(3) + ' bits/character, ≈ ' + Math.ceil(H * s.length) + ' bits total.';
}
</script>

Now the experiment that matters: compare a verse, a sentence of your own, and random mashing of similar length. The mashing will usually score the *highest* entropy. Sit with that. By Shannon's measure, noise is maximally informative — because his measure tracks unpredictability, not meaning. Whatever meaning is, it is not entropy.

**Selah.**

- When you speak, your words rearrange air. When God speaks in Genesis 1, what exactly is being rearranged?
- Austin's performatives fail when the speaker lacks standing. What human utterances have you seen *make* reality rather than describe it — promises, verdicts, blessings? What gave them their force?

<details markdown="1">
<summary><strong>Checkpoint</strong> — three questions (click to reveal answers)</summary>

1. *What did Shannon explicitly exclude from information theory?* — Meaning (the "semantic aspects of communication"). His theory measures uncertainty-resolution, not significance.
2. *What double meaning does Hebrew* davar *carry?* — Both "word" and "thing/matter" — speech and reality under one noun.
3. *How does John 1 differ from Wheeler's "it from bit"?* — Wheeler grounds reality in information; John grounds it in a personal communicator. Pattern vs. Person.

</details>

## Threads

- The word that *creates* here becomes the word that must be *preserved* — [Chapter 5: The Canon](05-the-canon-an-error-corrected-channel.md).
- The Logos introduced here takes on flesh in [Chapter 10: The Word Made Flesh](10-the-word-made-flesh.md).
- What meaning *is*, if not entropy, is pursued through signs in [Chapter 2: The Image and the Icon](02-the-image-and-the-icon.md).

---

[← Preface](00-preface.md) · [Contents](../README.md) · [Next: 2 · The Image and the Icon →](02-the-image-and-the-icon.md)
