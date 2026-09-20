# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").

On my first session, I immediately experienced an issue where my hint was always "Go LOWER!" regardless of the answer, even if I guessed the lowest bound (1). I was unable to successfully guess the number. On Normal Difficulty I expected to have 8 attempts, but on my 7th attempt I received a "GAME OVER! ...". When I attempted a start a new game, the "GAME OVER! ..." message remained despite receiving new attempts. When I tried to enter a guess on my second session after starting a new game, a guess was failed to be accepted and the game stopped working.

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input | Expected Behavior | Actual Behavior | Console Output / Error |
|-------|-------------------|-----------------|------------------------|
| Guessed 1| Expected Go HIGHER! | Got Go LOWER! |  "None" |
| Guessed 0 | Invalid Input or Go HIGHER!| Got Go LOWER! | "None" |
| Started New Game | New Game Started | Unable to Guess | "None" |
| Any Guess | Go HIGHER! or Go LOWER! | Only Go LOWER! | "None" |
| Used 7 Attempts on Normal Difficulty | Expected 8th Attempt | Got GAME OVER! | "None"
| Normal Difficulty Has Hard Difficulty Stats | Expected 8th Attempt | Got GAME OVER! | "None"
---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion you did not accept as written (including what the AI suggested, why you rejected or changed it, and how you verified your version). It does not have to be a suggestion that was wrong: over-engineered, out of scope, harder to read, or a poor fit for this codebase all count.

I utilized Gopilot as my AI Tool. An example of an AI suggestion that was correct was in regard to the solution for the "Reversed Hints" problem. It successfully pointed out that within the check_guess function, the display message for "Too high" and "Too low" was reversed. However, at the same time it attempted to suggest a fix for a closely related issue with a type error in the comparison between the guess number and the secret number. On even guesses, the secret number would be turned into a string, which drastically affected the outcome of the comparison and could result in the wrong hint being displayed. Despite this observation by the AI assistant being correct, I chose to initially not accept this suggestion because it was outside of the scope of what I wanted it to. I was primarily focused on the "Reverse Hints" bugged first.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

To start with, I utilized a newly generated pytest to check if a bug had been patched. Once the bug I attempted to fix passed a pytest, I did a manual test through the application. One test I ran was for the "Reversed Hints" bug. I used the AI assistant to help me generate the "test_guess_hints_point_in_the_correct_direction" pytest, which let me test if the "Too high" outcome and message was appropriately selected with the test case of a guess number of 60 and a secret number of 50 and if the "Too low" outcome and message was appropriately selected with the test case of a guess number of 40 and a secret number of 50.

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
