# Task 3 Stretch Planning/ Insight

Here is a insight of ideas/ planning of how to apply the stretch task.

---

## Table of Contents

- [Implementing The Solution](#how-you-would-go-about-implementing-the-solution)
- [Problems](#what-problems-you-might-encounter)
- [Testing](#how-you-would-go-about-testing)
- [Next Time](#what-you-might-do-differently)
- [Added On](#currently-added)

---

## How you would go about implementing the solution

Currently we can see there is a implementation of tags in the conversation model object for the REST interface.
The schema for conversation looks to have tag field and if you use the below method to which creates a conversation you are able to include a tag.

```
POST /conversation
```

It seems possible to update the tag with the below method based on the conversation id.

```
PUT /conversation/{conversationId}/tags
```

Seems the approach to take would be to reuse the way tags are implemented in conversation for the REST interface but to a single chat message for the GraphQL interface. This would require:

- Adding into the message schema for graphQL the tags fields in a single chat message.
- Update the conversation schema for graphQL to provide the tag fields.
- Create a mutation for the ability to add a single chat message.
- Create a query that gathers chat messages in a conversation using matches anything that has that string.
- Create tests to validate the task and add ons.

---

## What problems you might encounter

Some of the possibilities that can be encountered when implementing this task can be, any user is being allowed to define their own tags if not monitored could lead to injection attacks in addition database performances could be impacted when dealing with large varies of tags or queries needed to obtain the tags.

---

## How you would go about testing

When testing we can take the approach of TDD (test driven development) this would mean creating the test's first to define the boundaries on expectations and then writing the source code. In addition we can overlook the current tests in place and see if
they need to updated or adapted to accommodate the changes.

Tests would include:

- Unit/Integration tests
- API tests

---

## Currently added

While I have not applied to much to the source code. I have made a slight start to the process to which you will see that I have added onto the graphQL schema for messages.

The files that have been updated are:

- `message.model.ts`
- `message.entity.ts`
