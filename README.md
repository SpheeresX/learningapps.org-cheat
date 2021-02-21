# learningapps.org-cheat
Cheats for learningapps.org (group assignment)

## What it does
This script will show you the correct answers (groups) for all questions (cards). It does not automatically assign them.

## Usage
**Note: this script only works for apps that use the "Group assignment" template.**

1. Open the DevTools and go to the Console tab
2. Change the JavaScript context from `top` to `frame (watch)`
3. Paste the following code:

```javascript
allCards.forEach((card) => {
  var answer = card.cluster.xmlValue.replace('text|', '').replace('||0', '');
  var question = card.innerHTML.replace('<span unselectable="on" class="resizeText">', '').replace('</span>', '').substring(0, 33) + '...';

  console.log(`Q: ${question} / A: ${answer}`);
});
```
