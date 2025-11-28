+++ 
date = '2025-11-28T10:15:53+01:00' 
draft = false 
title = 'Dabbling with coding agents? Remember Encapsulation' 
+++

![wavefunction](./wfc2.png "a wave!")

**TLDR:** AI aided software engineering offers productivity gains but also
challenges Sosftware Engineers to integrate stochastic AI-generated code while
keeping projects maintainable. Reinterpreting the classic software engineering
principle of **encapsulation**, defining robust, data-oriented module
**interfaces (fixed points)** and rigorous **unit tests (rules)**, we can treat
the agent's work as a controllable **black box**. This approach allows the
agents to operate autonomously and by so doing offering the maximum viable
benefits that will still see the human retain domain understanding and project
control.

---

### Delegating code to an AI agent can be a frustrating experience

Collaborating with an AI agent is remarkably similar to collaborating with a
flesh-and-bone colleague. It requires clarity, effort put into good
communication, and gets better with experience. Most importantly, the more
exactly you know what you want, the better an experience you will have. This is
now a cliche, and taken to an extreme you could say that the whole point of
coding agents, the entire value proposition, is that you don't _want_ to know
exactly what you want (or, I propose, you'd write the code yourself), the same
way you'd delegate a task to a colleague so they can figure things out
autonomously and you can get on with something else.

I don't think we are anywhere near the point where, generally, you can vaguely
describe your intent to an agent and then be satisfied with the results, the
same way you could with a trusted human collaborator.

---

### What do we even want?

Glad you asked:

1.  Agents should be independent to the maximum degree possible: reading and
    fixing generated code is not what I want to get from cooperating with AI.
2.  **The project** should stay maintainable for humans, despite Agents
    participating in the factoring of the code: I am not comfortable with
    embracing any digitally induced vibes, I would like to continue
    understanding what is going on for the foreseeable future.

So how do we achieve these very high level goals? we turn to a fundamental
computer science principle: **Encapsulation**.

---

### An aside: wave function collapse

![constrained](./wfc1.png "a constrained wave!")

Wave function collapse is something cool in quantum physics which I don't claim
to be smart enough to talk about, but also something a bit more reachable in
procedural generation. Given a universe, a set of rules defining how elements in
the universe relate to each other and a set of fixed, defined points, wave
function collapse can fill the universe in a random but **coherent** way. LLMs
are stochastic machines so randomness is part of the deal.

Do you see where I am going with this? We need to constrain the system.

### LLM produced code can get very messy

To shape it into a useful tool one needs to constrain and limit the output to
the good parts. Internet literature on the topic advises to keep tasks small,
use tests, provide relevant context via MCP, specifically earmarking files for
the LLM to refer to. All of this works to some extent, but used separately or
without a coherent strategy was not sufficient for me.

What I add are **fixed points and rules** to impose **coherence**.

- **Fixed Points:** The module interfaces, its API on one side, and for other
  side effecting modules the side effects that we either already have or want
  the model to produce.
- **Rules:** Tests, ideally of the in-process, free-of-dependencies type (unit
  tests if the unit of code is chosen to be the module).

In practice, we describe the module interface we want the agent to implement, we
ground the agent to reality by defining tests for the module to pass, and then
we leave complete ownership of the module to the agent. This is the **full black
box approach** enabled by **encapsulation**.

### Maintainability considerations

In the goals, I specified that my proprity is for the project to stay
maintainable, but what about the AI owned module? As long as it passes the
tests, I am assuming it works well enough for now. If I start having issues with
the it, I write a new test based on input/output and feed it to the agent again.

I consider the code inside as not my problem, even throaway. If and when it
becomes a bottleneck, I can either try to feed it back to a more advanced model,
or worst case scenario I can just rewrite it from scratch: Thanks to the
methodology used to create and validate the code I have a decoupled module that
it is simple (perhaps not easy) to rip out and reimplement.

The project stays maintainable, I keep my domain understanding (except for the
innards of the modules) and I am able to move fast (and stay not overwhelmed by
lack of understanding) thanks to a more controllable AI workforce.
