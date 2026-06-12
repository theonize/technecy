---
title: "5 · The Canon: An Error-Corrected Channel"
---

# 5 · The Canon: An Error-Corrected Channel

> *"The grass withereth, the flower fadeth: but the word of our God shall stand for ever."* — Isaiah 40:8
>
> Shannon's noisy-channel coding theorem (1948), paraphrased: *over any noisy channel, messages can be transmitted with arbitrarily few errors — provided you add enough of the right kind of redundancy.*

**In this chapter** — *Theology:* the preservation of Scripture. *Information science:* noise, redundancy, checksums, and error correction. *Philosophy:* what it means to say a text transmitted by fallible hands is "the same" text.

## The noisy channel

For roughly three thousand years, the biblical text traveled by the noisiest channel imaginable: tired human hands copying by lamplight. The failure modes are so regular that textual critics have a taxonomy of them — an error catalog any QA engineer would recognize:

- **Haplography** — writing once what appeared twice (a dropped duplicate).
- **Dittography** — writing twice what appeared once (an inserted duplicate).
- **Homoioteleuton** — the eye skips from one line-ending to an identical one, deleting everything between (the copy-paste skip).
- **Metathesis** — transposed letters; plus mishearing (in dictation), misdivision of words, and the marginal note that migrates into the text.

Jesus' remark that *"one jot or one tittle shall in no wise pass from the law"* (Matthew 5:18) names the smallest glyphs in the Hebrew writing system — the yod and the tiny stroke distinguishing similar letters. It is a claim of bit-level fidelity made about a hand-copied text. On its face, over such a channel, that is an outrageous engineering requirement. This chapter is about the machinery that met it.

## Scribes as error-correction engineers

The **Masoretes** (roughly AD 500–1000), heirs of older scribal practice, built what can only be called an integrity-verification system around the Hebrew text:

- They **counted everything** — verses, words, letters of each book — and recorded the counts. A finished copy was verified against the totals: a checksum, executed by hand.
- They marked **midpoints**: the traditional middle letter of the Torah (in Leviticus 11:42), the middle words, middle verses — positional checkpoints, so an error's *location* could be bracketed, not just detected.
- They wrapped the text in the **masorah** — marginal metadata noting every unusual spelling and every rare form, so a future copyist could not "correct" an oddity that was original. (Note the sophistication: protecting the text *from* its copyists' good intentions.)
- Rules for synagogue Torah scrolls went further: prescribed materials and layout, letter-by-letter copying from an exemplar, review of a fresh copy — and defects requiring correction or the scroll's retirement. Quality control with teeth.

In 1947 the system received a spectacular field test. The Dead Sea Scrolls included a complete Isaiah scroll a thousand years older than the standard Masoretic manuscripts then known. Across that millennium of copying, the texts proved remarkably stable — overwhelmingly the differences are spelling and minor slips, with the famous handful of interesting variants. A thousand-year round trip through the noisy channel, and the message held.

## Redundancy: the other half of Shannon's recipe

Shannon's theorem says noise is beaten by *redundancy*, and the biblical channel is saturated with it:

- **Manuscript abundance.** The New Testament survives in thousands of Greek manuscripts, plus early translations (Latin, Syriac, Coptic...) and so many quotations in early Christian writers that large parts of the text could be reconstructed from quotations alone. Classical works we consider secure often rest on a few dozen copies; the NT's textual evidence is, by ancient standards, an embarrassment of riches. More copies mean more errors in absolute terms — and far more power to correct them, because independent copies rarely fail in the same place.
- **Internal redundancy.** Four Gospels encode overlapping accounts; Kings and Chronicles run parallel histories; Psalm 14 reappears as Psalm 53; prophets quote the Law; the New Testament quotes everything. Parallel passages let critics cross-check one stream against another.
- **Liturgical redundancy.** The text was not only copied but *memorized, chanted, and read aloud on schedule* — living copies in thousands of memories, a side-channel that catches a written corruption the moment it is read in public.

**Textual criticism** is the decoding step: given the surviving copies, infer the most probable original — weighing manuscripts by age and independence, preferring readings that explain the others, knowing the error taxonomy above. Its practitioners' verdict is worth hearing precisely: the vast majority of variants are trivial (spelling, word order), and no doctrine of the faith hangs on a disputed reading. That is not a claim that the channel was noiseless; it is the claim that the redundancy was sufficient — which is exactly what Shannon's theorem requires.

**Canon formation** is the *authentication* layer of the same system — not "which copies are accurate" but "which messages are from the claimed sender." The early church's working criteria — apostolic origin, universal reception across independent churches, coherence with the rule of faith — map with eerie neatness onto modern message authentication: provenance verification, multi-node attestation, consistency checking. ([Chapter 8](08-prophecy-signal-verification-trust.md) finds the same multi-factor pattern in the tests for prophets.)

## Workbench: the Scriptorium

Watch the whole argument run (this tool works on the published site):

<div style="border:1px solid #555; padding:1em; border-radius:6px;">
<p><strong>Scriptorium.</strong> Three scribes copy your verse; each one randomly corrupts about 3% of the letters. Then a textual critic reconstructs the original by majority vote, letter by letter.</p>
<textarea id="scribe-source" rows="2" style="width:100%;">The grass withereth, the flower fadeth: but the word of our God shall stand for ever.</textarea>
<p><button onclick="technecyScribe()">Copy &amp; Reconstruct</button></p>
<pre id="scribe-output" style="white-space:pre-wrap;"></pre>
</div>
<script>
function technecyScribe() {
  var src = document.getElementById('scribe-source').value;
  var alphabet = 'abcdefghijklmnopqrstuvwxyz';
  function copy(s) {
    var out = '';
    for (var i = 0; i < s.length; i++) {
      if (/[a-zA-Z]/.test(s[i]) && Math.random() < 0.03) {
        out += alphabet[Math.floor(Math.random() * 26)];
      } else { out += s[i]; }
    }
    return out;
  }
  var copies = [copy(src), copy(src), copy(src)];
  var rec = '';
  for (var i = 0; i < src.length; i++) {
    var a = copies[0][i], b = copies[1][i], c = copies[2][i];
    rec += (a === b || a === c) ? a : (b === c ? b : a);
  }
  function errs(s) { var n = 0; for (var i = 0; i < src.length; i++) { if (s[i] !== src[i]) n++; } return n; }
  document.getElementById('scribe-output').textContent =
    'Scribe A (' + errs(copies[0]) + ' errors):\n' + copies[0] + '\n\n' +
    'Scribe B (' + errs(copies[1]) + ' errors):\n' + copies[1] + '\n\n' +
    'Scribe C (' + errs(copies[2]) + ' errors):\n' + copies[2] + '\n\n' +
    'Critic’s reconstruction (' + errs(rec) + ' errors):\n' + rec;
}
</script>

Run it several times. Each scribe averages a couple of errors — and the reconstruction is usually perfect, because three independent copyists almost never blunder at the same letter. Now imagine not three copies but thousands, plus translations, plus quotations, plus memories. That is the actual situation of the biblical text.

**Selah.**

- Isaiah 40:8 stakes the word's permanence against the most perishable things in its world — grass and wildflowers. What is the modern equivalent of grass — what carriers of words around you are withering fastest?
- The Masoretes protected the text *from its copyists' good intentions*. Where have you seen a well-meaning "correction" corrupt something — a story, a quote, a doctrine?

<details markdown="1">
<summary><strong>Checkpoint</strong> (click to reveal answers)</summary>

1. *Name three scribal error types and their software analogues.* — Haplography (dropped duplicate), dittography (inserted duplicate), homoioteleuton (skip between identical line-endings — the copy-paste skip).
2. *What were the Masoretes' letter-counts functionally?* — Checksums: integrity verification against recorded totals, with midpoints as positional checkpoints.
3. *How do textual criticism and canon formation differ in information terms?* — Criticism is error correction (recovering the message); canonization is authentication (verifying the sender).

</details>

## Threads

- Why so much of the text is *poetry* — redundancy with a second job: [Chapter 6](06-figures-of-speech-divine-compression.md).
- Authenticating the *sender*, not just the message: [Chapter 8: Prophecy](08-prophecy-signal-verification-trust.md).
- Forged epistles and Paul's countermeasure — a literal signature: [Chapter 11](11-the-body-as-network.md).

---

[← 4 · Babel](04-babel-when-protocols-break.md) · [Contents](../README.md) · [Next: 6 · Figures of Speech: Divine Compression →](06-figures-of-speech-divine-compression.md)
