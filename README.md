## Rusty Chess

*** This is a WIP ***

### Can ChatGPT build a Chess game in Rust? Let's see...

I initially attempted this with ChatGPT 3.1. It was a bit of a struggle, it made basic mistakes and misunderstood some concepts. 
Experienced programmers learning Rust might have found it a useful tool to accelerate learning and development, but those with limited previous programming 
experience would have likely struggled.

I've tried this again with GPT 4o with much greater success. This time I decided to ask it to create a front end first, then add in some logic. I used the 
following prompts:

> We're going to write a game of chess in Rust. First of all, let's create a simple web application to display a chess board, and the pieces in their starting positions. For simplicity, the pieces can be represented by letters, e.g. King = K, Knight = Kn etc.

There was one error in its code (it forgot to add a `Content-Type` response header), but when presented with the error message it worked that out for itself. It's now created a rather nice little app

![Game screenshot](/images/screenshot-1.png)

I then asked it to create some logic:
>ok that's great. let's add methods to make moves. The input to move can be from a text field in the page, and should be in the standard chess move format (Algebraic notation).
Upon entering a move, the page should display the state of the board after the move

It wasn't brave enough to fully embrace the algebraic notation (which would have required a decent amount of parsing logic), and instead opted for an unvalidated 
4 character move input requirement (e.g. c2c4)

##### Time taken to get this far with GPT 4o: 15 minutes

### Adding tests

This is where GPT had a few issues. When asked to add tests, it rightly wanted to refactor the code to make it more testable. Good start. However, it forgot 
one of the methods in its refactored code. It also, quite correctly by Rust standards, kept the tests in `lib.rs`. Being a newbie to Rust, I challenged this,
and rather than informing me this was the convention for Rust, it told me I was right and move the tests out. This caused issues running the tests ... we 
eventually got there however, with a few unit tests in `lib.rs` and some integration tests in a separate test file. Much better.

#### Next steps:
- Logic for capturing pieces
- Check and check mate

### Running the app

Make sure you have Rust installed. From the project's base directory:
```
cargo run
```