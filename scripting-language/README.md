---
description: How to edit the prompts for A.I.
---

# ➗ Scripting Language

## When to Edit Prompts

Prompts should only be changed by advanced users, as it does take a lot of troubleshooting and testing to find prompts that result in the smartest behaving A.I.&#x20;

Keep in mind that most changes will result in degraded performance as we have already spent countless hours to create the default prompts.\
\
However, if you wish to create your own prompt, you can always change it to try and:

* Reduce some unwanted A.I. behavior
* Increase some desired A.I. behavior
* Reduce token costs

## Prompt Templates

You do not directly write the prompts for the A.I. because it needs to know things about the game state that change over time.\
\
Instead, you write **prompt templates** which are then turned into the prompt for the A.I.&#x20;

### Example of a bad prompt

<pre><code><strong>It is 1914 and you need to make a decision as Argentina!
</strong><strong>So far, people have done a lot of things and may be attacking you.
</strong><strong>Your population is 3,000,000
</strong><strong>What do you want to do now?
</strong></code></pre>

This is a bad prompt because its not using game state, doesn't apply to all countries, etc. It might work for the very beginning of the game,&#x20;

### Correctly using prompt templates

```
// Some code
```

When in the game, prompt templates turn into text that depends on game state and the country that needs to respond to it. For example:

```
// Some code
```

