# learningapps.org-cheat
Cheats for learningapps.org

## How it works
This script will make it look like all answers are correct. It currently does not tell you which ones are right, but I'm planning to implement this if it's possible.

## Usage
**Note: this script only works for apps that use the "Group assignment" template.**

1. Assign the cards to any group
2. Open the DevTools and go to the Console tab
3. Change the JavaScript context from `top` to `frame (watch)`
4. Paste the following code:

```javascript
// make it look like all cards are correct
Array.from(document.getElementsByClassName('card')).forEach((c) => {
	c.classList.remove('correct', 'wrong');
	c.classList.add('correct');
});

// show the "congratulations, you found the correct solution" screen
if ($("#feedback").length === 0) {
	var f = AppClient.getParameters("feedback").value;
	$("#cardsOverlay").append(
	  '<div id="feedback" '+(f.length < 50 ? 'style="text-align:center"':'')+'>'+AppClient.linkifyText(f)+
	   '<br><br><div style="text-align:center">'+
	    '<button style="font-size:120%" onclick="$(\'#feedback\').remove()">OK</button>'+
	  '</div>');
}

// not sure if this is needed
AppClient.setSolved();
```
