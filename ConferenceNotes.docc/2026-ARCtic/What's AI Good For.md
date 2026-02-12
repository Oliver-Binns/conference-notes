# What's AI Good For? (Probably not that, but not nothing.)

@Metadata {
    @TitleHeading("Talk")
}

Rob Napier

## Abstract

As developers, we're pretty overwhelmed with AI-everything right now. You've probably heard all the arguments ranging from "all programmers will be out of a job by December" to "lying autocompletion engines have no practical uses." You've probably seen posts from people claiming incredible "one-shot" prompting that rewrites Safari from scratch in an afternoon. Maybe you've tried it out, and it wasn't quite...that. Are you doing it wrong? Is everyone lying? What's going on?

I spend much of my work time developing software and processes based on LLMs. I've talked extensively to people in other teams and other companies about what does and doesn't work. And I've learned a few things that aren't obvious.

AI is not particularly good at most of the things your boss probably wants it for. But there are problems it can help you solve that would be impractical without it. In this talk, I'll help you think a little more clearly about where AI will probably be unhelpful, where it may be harmful, and where it's worth considering.

## Key Takeaways

Inference: it predicts the most likely next token.

Oh, I see the problem (48%)
Oh, I see the issue (42%)
Oh, I see the 🐞 (0.2%)

> I came to bury Caesar, not to praise him.

### An AI is not a computer.
An AI is a terrible computer, the same way a human is a terrible computer.

### Context is not like RAM.
Context is part of the model, it's baked in when the model is created.

### Context has very little structure.
There's no deep distiction between prompts and other inputs (documents), which leads to prompt injection and confusion.

### Infinite interns:

They're bright, work remotely, but next week you get a new set of interns.

**How should you manage them?**

Tell the AI how the system works.
You know the system best, you should do this- or at the very least review the content and correct it.


### AI does not have "memory"

Not like human memory.

Humans can juggle context. AI does not.

AI does not know when to do a toolcall because it does not know when it doesn't know something.

### AI is leverage

You can get more out of your work, but you need to work harder for it.
You can go very far, very fast. So you need to be pointed in the right direction.

### AI does not understand itself

It cannot self-reflect.

AI coding tools are ~more trouble than they're worth~ very tricky.

### Hard-to-test requirements

If you forbid too many things, it ignores all of it.
It will say: "I know I'm not supposed to do this, but it's probably ok this time".

### A good artisan doesn't blame their tools.

But that doesn't mean they use bad tools, or the wrong tools.
Good artisans stay in control.

You need to read the code, **more closely** than you would normally.

You saved a lot of time writing the code, so you should use some of that time properly reviewing what it's produced.

### "I felt faster" is not data.

### It unlocks projects I wouldn't have done

Try out different approaches to things very quickly to see which is best.

### Small(er) bytes

Don't let AI produce 

### Reviewing code

AI is great as a code review.

You can run it in parallel with your review:
- Often it's wrong.
- Often it's duplicative.
- Often it will find unexpected errors that you didn't find.

Let AI review its own code, but not exclusively.

### Writing tests

It's great at writing tests.
It's bad at writing _good_ tests.

AI writes tests that test the implementation, not the requirements.

Tests are prompts.

Real example of AI trying to _"fix"_ a test
```
// This should return 5, but the implementation returns 4.
// Fix this test when the code is fixed.
assert(value == 4)
```

You have to prompt like a lawyer.

### Documentation

Architecture docs can be useful.
You have to review them closely to ensure they're correct, and cover what you want them to cover.

Ask the AI to be more concise: big docs are not good for anyone.

### AI is best when:

- it's not a big deal when it's wrong
- you can and will review the output
- the code is documented well enough to ensure that a new hire could do it

You need to know what you want.

> AI is not a computer.
> AI is not a person.
> AI is not magic.

## Links

- [Slides](https://github.com/rnapier/ai-what)
