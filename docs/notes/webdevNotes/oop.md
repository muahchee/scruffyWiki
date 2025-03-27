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

## Visitor Pattern

[wikipedia](https://en.wikipedia.org/wiki/Visitor_pattern?ref=hackernoon.com)

Represent[ing] an operation to be performed on elements of an object structure. Visitor lets you define a new operation without changing the classes of the elements on which it operates.

The nature of the Visitor makes it an ideal pattern to plug into public APIs, thus allowing its clients to perform operations on a class using a "visiting" class without having to modify the source.

When new operations are needed frequently and the object structure consists of many unrelated classes, it's inflexible to add new subclasses each time a new operation is required because "[..] distributing all these operations across the various node classes leads to a system that's hard to understand, maintain, and change."

Define a separate (visitor) object that implements an operation to be performed on elements of an object structure.

![W3sDesign_Visitor_Design_Pattern_UML](../../media/W3sDesign_Visitor_Design_Pattern_UML.jpg)


--

## OOP examples

- [Kevin Makes Games PICO-8 star field example](../gamedevNotes/PICO-8/oop-in-pico8.md#star-field-example)