# How the AutoBleem manual is written

The manual is read by players, most of them not technical. Every section answers three questions: **what is
this for**, **how do I use it**, **what will I see**. Write it the way a friend who knows the console well would
explain it - in full, natural sentences.

## Rules

- **Start with the purpose.** First say what the feature gives the player and when they would want it
  ("If you want the game always at hand, without the disc..."), then how to do it, then what happens.
- **Full sentences, second person, present tense.** "Press Square", "you will see", "the game is then on the
  shelf like any other". No telegraph style, no lists of nouns.
- **Say why, not only what.** "Old TVs cut off the edges of the picture, so this setting shrinks everything a
  little" - not "the safe area, 0-10 %".
- **On-screen names only where the player looks for them.** Quote a menu row, a button label or a message in
  *italics* when the player has to find it or will read it on the screen. Do NOT list every message a screen can
  show; explain the situations instead ("if there is not enough room, AutoBleem tells you how much it needs").
  The exact names come from the launcher's language file `src/resources/lang/<Language>.txt`.
- **Tables only for quick look-up** (buttons, a list of settings). Each table cell is still a real sentence that
  says what the thing is for. Anything that needs explaining goes into paragraphs.
- **Warnings and limits plainly.** "This does not work on Windows." "A copy of a scratched disc may or may not
  work."
- **Keep every fact.** A rewrite never drops a feature, a limit, a platform note or a cross-reference. Section
  numbers stay the same (other pages and languages point to them); images stay where they are.
- **Platforms:** say which ones a feature is on only when it is not on all of them.
- **No marketing**, no exclamation marks, no "simply"/"just", no internal names (tickets, branches, people,
  tools of the development team).

## Translations

The English manual is the master for the facts, not for the sentences. A translation is **written in the
target language**, as a native writer would explain the same thing: reorder, split or join sentences freely,
use the language's own idioms and the launcher's own words from `<Language>.txt`. Never translate sentence by
sentence. Read your paragraph aloud: if it sounds translated, rewrite it.

## A model paragraph

> ### 3.8a A disc in a USB drive
>
> You can connect an ordinary USB CD/DVD drive to the console, a Raspberry Pi or a PC started from the
> AutoBleem stick and play straight from an original PlayStation disc - without copying anything. A disc you
> put in appears in the launcher like one more game. This does not work on Windows.
>
> **Copying a disc to the stick.** If you want the game always at hand, without the disc, press Square
> (*Copy disc*). AutoBleem first asks whether to copy the game and how much room it will take, then saves it in
> the `Games` folder as a single CHD file (a game on several discs also gets an `.m3u` file, so changing discs
> works in the game). While it copies you see the speed and the time left, and *Abort* stops it. When it is
> done, the game is on the shelf like any other. AutoBleem will not copy a game that is already in `Games`, or
> one there is no room for - it then tells you how much room it needs. A scratched disc can be copied too: the
> parts that could not be read are filled with zeros, and AutoBleem tells you how many there were. Such a copy
> may or may not work.
