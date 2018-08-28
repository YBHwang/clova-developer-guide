You must change the code so that the Sample Dice extension can handle the slot.
In this section, we will reuse the repository from the [first tutorial](/CEK/Tutorials/Build_Simple_Extension.md) in order to see which parts were changed by referring to the source codes implemented before.
Go to the local repository and check out the `tutorial3` branch as shown below:

{% raw %}
```bash
cd /path/to/your_sample_dice_directory
git fetch
git checkout tutorial3
```
{% endraw %}

The Sample Dice extension handles the slot in `intentRequest()` of the `clova/index.js` file.

{% raw %}
```javascript
intentRequest(cekResponse) {
  const intent = this.request.intent.name
  const slots = this.request.intent.slots

  switch (intent) {
    case "ThrowDiceIntent":
      let diceCount = 1
      if (!!slots) {
        const diceCountSlot = slots.diceCount
        if (slots.length != 0 && diceCountSlot) {
          diceCount = parseInt(diceCountSlot.value)
        }

        if (isNaN(diceCount)) {
          diceCount = 1
        }
      }
      ...
  }
  ...
}
```
{% endraw %}

As shown by the codes above, the extension extracts slot information (`this.request.intent.slots`) from the request message sent by Clova. If the "diceCount" slot (`slots.diceCount`) registered in the interaction model exists, the extension reads the slot value as an integer. This value is the number of dice to roll. The extension determines the value as 1 by default unless the slot does not exist or the value is not an integer.

Run the new code on the extension server.
