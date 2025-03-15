:material-code-braces: Object Oriented Programming
========================
## Tips from POODR

Some tips from the book [Practical Object Oriented Design in Ruby (POODR) by Sandi Metz](https://www.poodr.com/):

- Don't decide; preserve your ability to make decisions later.

- Depend on things that change less often than you do.

- Public methods should read like a description of responsibilities. They should:

    - Be explicitly identified as public
    - Be more about "what" than "how". Blind trust.
 > "I know what I want and I trust you to do your part."
    - Have names that, insofar as you can anticipate, will not change.
    - Not have order dependent parameters

- Private methods should be clearly marked (with an underscore "_")

- The public interface is like a menu; the private interface is the kitchen. Both together will eventually lead to food being served to the customer, but the customer only has to interact with the menu.

- Use message based design rather than class based.
> "I need to send this message (ask for something), who should respond to it?"

---

## Design Patterns

I think design patterns might be useful for planning out dependencies.

- [JavaScript Design Patterns – Explained with Examples  from freecodecamp](https://www.freecodecamp.org/news/javascript-design-patterns-explained/)

- [Learning JavaScript Design Patterns by Addy Osmani and Lydia Hallie](https://www.patterns.dev/) -  one of the additional reading from TOP

- [Design Patterns from OODesign](https://www.oodesign.com/)

--

## OOP examples

- [Kevin Makes Games PICO-8 star field example](../gamedevNotes/pico-8/oop-in-pico8.md#Star%20field%20example)