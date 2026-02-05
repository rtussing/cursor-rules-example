# Cursor Rules Examples

- [Overview](#overview)
- [How I use Cursor Rules](#how-i-use-cursor-rules)
- [Quick Guide to Cursor Rules](#quick-guide-to-cursor-rules)
- [Resources](#resources)

## Overview

This repo contains some of the Cursor rules that I use in my normal development process.

Some of them are really nice to use, like `@review`. Some of them don't really get me what I'm looking for, but they're still hanging around in my repo: `@api-endpoints-crud`.

I constantly adjust the rules as I see fit. Working with agents requires the ability to manage the development process and review changes. You have to learn to trust the agent, but never too much. And if the agent doesn't do something correct, it often comes back to giving it bad instructions.

If you've never used rules in an agentic coding app, this might help: [Quick Guide to Cursor Rules](#quick-guide-to-cursor-rules).

## How I use Cursor Rules

The way that I work with my agentic environment is constantly changing. When I first started working with Cursor, I was under the impression I could one-shot anything. I gave the agent a very rough guide and told it to build the app in full. As you can imagine, that's not how this works (yet).

After doing some research, I found out about the concept of rules. I saw videos and blog posts about how people were able to streamline their use of the agent by giving it specific, repeatable context. This context helped to specify requirements and keep the agent on track. I made some rules and started using them.

After some time experimenting, I began to run into a common issue: context management. It's a real pain. At some point, the agent stops feeling like magic and starts feeling like the version of you that didn't sleep last night. That's when I started with the concept of:

### "Harness Engineering"

I found that at some point my agent was more efficient if I took the valuable parts of my current chat and pasted them into a new chat. This quickly expanded to a process of using windows to do individual, manageable tasks. For example, individual agents to:

- Understand the changes you want to make, pull in relevant context, and write a high level plan
- Implement the plan
- Verify the updates

Here's the way I currently use Cursor for general, large-scale development:

1. I open a chat window and tag my `@analyze-and-plan` rule. I tell the agent what update I want to make, and I give it as much specific information as I can. The agent looks through the codebase and creates a markdown document that describes the changes, provides files, functions, line numbers, and example code, and whatever else I ask for.
2. I review the plan. If I want to make an update to the plan, I use my `@review` rule.
3. I take the finished plan and give it to a new agent, and tag my `@implement-plan` rule.
4. I review the implementation. I test, ask the agent questions, and make changes using my `@review` rule.

I recently watched the following video. It's where I got the name "harness engineering". It's a really good explanation of common context issues, and it makes a really strong case for how to manage context. It accurately describes the dev process that I've found to be the most effective.

[YouTube Video: Dex Horthy | AI Engineer](https://www.youtube.com/watch?v=rmvDxxNubIg)

## Quick Guide to Cursor Rules

Cursor rules are a Cursor specific concept. Claude Code has its own concept of rules. In general, these rules allow you to give context to an agent in a repeatable manner.

These rules allow you to create reusable prompts, which is convenient because it means you don't have to repeat as many instructions to the agent. As you get more comfortable using rules, they become integral to the development process. It's all about figuring out how to get the most out of the agent, which is specific to each person.

For example, I can create a rule that asks the agent to explain code to me. Rather than typing out a whole prompt every time I want an explanation, I can just use the Cursor rule. Here's an example of a rule I might use.

```txt
I am working on an API. It is a REST API built using Next.js. The functions in this file are helper functions that are called by the API. Explain what this function does.
```

These rules can be referenced in the chat. Here's a basic example of what that might look like:

```txt
@explain.mdc

explain getUserAttributes()
```

Each cursor rule contains a header at the top of the file. This is part of Cursor's rule concept. For example, they can be set to apply automatically based on the Agent's discretion. In this case, the rule is actually following the "Apply Intelligently" rule that

```md
---
description: Working with project architecture, frameworks, and languages
alwaysApply: false
---
```

They can also be set to attach to every chat window, meaning the context will always be available. Here's an example of the header for one of my rules that always applies:

```md
---
description: Central index for all Cursor rules in this repository
globs:
alwaysApply: true
---
```

## Resources

You can learn more about Cursor here: [Cursor.com](https://cursor.com/home)

And here is the documentation for Cursor rules: [Cursor Rules Doc](https://cursor.com/docs/context/rules)
