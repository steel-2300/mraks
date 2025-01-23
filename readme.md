# scramby
An npm module for generating [random-state scrambles](https://www.speedsolving.com/wiki/index.php/Random_State_Scramble) for twisty puzzles.

## Installation
```bash
npm install scramby
```

## Usage
```js
import scramby from 'scramby'
const scrambler = scramby()

console.log(scrambler.getRandomScramble().scrambleString) // L2 U R2 B' R' B' L F2 D2 B D2 F D R2 U F2 R2 U' R2 F'
```

## API
### `scramby([puzzle])`
Creates a scrambler that can be used to generate random scrambles.

#### Params
* `{string}` **puzzle** - The type of puzzle.
  * Valid types: `'222'`, `'333'`, `'444'`, `'555'`, `'666'`, or `'777'`
  * default: `'333'`

#### Returns:
A `Scrambler` object.

#### Example:
```js
import scramby from 'scramby'
const scrambler5x5 = scramby('555')
```

---

### `scrambler.getRandomScramble()`
Generates a random scramble.

#### Returns:
 A `Scramble` object that has a `state` and a `scrambleString`. An example structure:

```json
{
  "state": "FRDFUBRFDBDRRRRRBBULLDFBLUUUFFUDLBFLDRBULLRBFFDLUBLUDD",
  "scrambleString": "L2 D2 L2 F2 D2 B' U2 L2 F' D2 B' R' F' U' L' D2 B' U2 B D' U"
}
```
The `state` is only needed if you want to draw the scramble.

#### Example:

```js
import scramby from 'scramby'
const scrambler = scramby()

const { scrambleString } = scrambler.getRandomScramble()
console.log(scrambleString) // L2 D2 L2 F2 D2 B' U2 L2 F' D2 B' R' F' U' L' D2 B' U2 B D' U
```
---

### `scrambler.drawScramble(el, state, width, height)`
Draws the scramble to an HTML Element.

#### Params
* `HTMLElement` **el** - The element to draw to.
* `string` **state** - The state received from `getRandomScramble()`.
* `number` **width** - The desired width for the drawing.
* `number` **height** - The desired height for the drawing.


#### Example:
```js
import scramby from 'scramby'
const scrambler = scramby()

const { state } = scrambler.getRandomScramble()
scrambler.drawScramble(document.getElementById('my-el'), state, 300, 180)
```

#### Output:
![](http://i.imgur.com/C4MW7JF.png)



## CLI

```
Usage
  $ scramby [options]

Options
  --puzzle, -p  Specify which puzzle you want a scramble for (222 - 777).
  --count, -c  The amount of scrambles you want.

Examples
  $ scramby
  F  L2 B' D2 F' R2 U2 F' L2 B2 F' R' F' R' D  R' D  R  U  F' R

  $ scramby -c 2
  F' D2 B  L2 F  D2 U2 B  F2 U2 F  L  F  U2 R  D2 U' R  B  L2 F'
  U2 R' D2 L' F2 D2 L  D2 F2 D2 L  B' D  U2 B2 L  F  L  B  R  U'

  $ scramby -p 222 -c 2
  F  U  F' U2 R  U  F  R' F
  U' R' U  R  F  R' F2 R'
```

## Running the examples
First, do:

```
npm run build:examples
```

Then open up the `index.html` file for the example you want to see.


## Credits
This is a fork of [jsss](https://github.com/cubing/jsss) in the form of an `npm` module. It's been modified to not require a global dependency of `Raphael` and it can work both in Node and on the browser.

## License
Uncertain. Read [this](https://github.com/cubing/jsss/issues/4) for more details.
