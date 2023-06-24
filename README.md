## Specifications

Start by importing the required files for this step: 

```bash
bash update_step_5.sh
```
You should have 1 new file, `Step_5.test.js` in the tests directory.

### Wallet

Let's wrap things up starting with the Wallet component.

#### onGameOver

Let's add a event handler prop `onGameProp` to the Wallet. This should also have a function that will set the state of `gameStatus` to `events.gameOver`, and will be triggered when payout is completed. 

#### Top ups

In most online Blackjack games, the player gets informed when they are out of credits, and gets provided with options to top up their account. 

Although we won't provide this service in our quest, we do want to make sure the player can keep playing without refreshing the page, so implement a function to alert the player with the following message, and replenish their `walletAmount` to the original amount:

`You're broke!! - Here's more credits, don't give up! 💪`

#### Payouts

We need a `useEffect` to respond to different game outcomes, so the `walletAmount` gets updated depending on the result. 

- For the player, Blackjack pays 3 to 2
- Winning pays out 1 to 1
- A push or tie returns the original bet to the player

Implement this in the Wallet component, and consider where we need to trigger the `onGameOver` event, and the top up function!

#### Resets

We also need a `useEffect` to perform the following tasks when the `gameStatus` resets to `events.bet`:

- Set the `betAmount` back to `0`
- Set the `inputValue` back to an empty string

### Controls

In `Controls.js`, add in the prop for the event handler to reset the game, and similar to `HIT` and `STAND`, conditionally render a `New Game` button that will trigger the event handler when clicked. This button should only be rendered when `gameStatus` is `events.gameOver`.

### Resetting the Game

Lastly, in `App.js`, add in the event handler function for resetting the game. When the game resets, the following things should happen:

- All scores must be reset to 0
- All cards are removed
- The deck is reshuffled
- The `message` should be cleared and reset to `messages.bet`
- The `gameStatus` should be reset to `events.bet`

Implement the function and pass the event handler down to the Controls component!

------------
Congratulations on completing all the steps! 🎉

Run `npm start` to play some Blackjack in `localhost:3000`~

Run `npm test`when you're done and submit your solution once you pass all the tests!

### Going further

#### Split, Double and Surrender

As you might already know, the player's options during his turn aren't limited to just hitting and standing. You can also:

- **Double-**  Double the player's wager, take a single card, and stand
- **Surrender-**  Some casinos offer the player to forfeit half their bet and end the hand immediately. This option is only available as the first decision.
- **Split-**  If the two cards have the same value, separate them to make two hands!
- **Insurance-**  If the dealer shows an ace as the first card, an "insurance" bet is allowed. Insurance is a side bet that the dealer has a blackjack. The dealer asks for insurance bets before the first player plays. Insurance bets can go up to half the player's current bet and plays 2 to 1, thus offsetting some of the losses of the original bet.

Feel free to implement this in your own versions of blackjack before you convert this to a project, for a most realistic and exciting game!
