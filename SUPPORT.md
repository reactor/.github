## :question: Do you have a question?

> Search Stack Overflow first; discuss if necessary

If you're unsure why something isn't working or wondering if there is a better
way of doing it please check on **Stack Overflow** first and if necessary start
a discussion. Use relevant tags among the ones we monitor for that purpose:
 - [`reactor-netty`](https://stackoverflow.com/questions/tagged/reactor-netty) for specific reactor-netty questions
 - [`project-reactor`](https://stackoverflow.com/questions/tagged/project-reactor) for generic reactor questions

If you prefer real-time discussion, we also have a few **Gitter channels**:
 - [`reactor`](https://gitter.im/reactor/reactor) is the historic most active one, where most of the community can help
 - [`reactor-core`](https://gitter.im/reactor/reactor-core) is intended for more advanced pinpointed discussions around the inner workings of the library
 - [`reactor-netty`](https://gitter.im/reactor/reactor-netty) is intended for netty-specific questions

Refer to each project's README for potential other sources of information.
	
We generally discourage opening GitHub issues for questions, in favor of the two channels above.

## :recycle: Our policy on **deprecations**

When dealing with deprecations, given a version `A.B.C`, we'll ensure that:

 - deprecations introduced in version `A`.`B`.`0` will be removed **no sooner than** version `A`.**`B+1`**.`0`
 - deprecations introduced in version `A`.`B`.`1+` will be removed **no sooner than** version `A`.**`B+2`**.`0`
 - we'll strive to mention the following in the deprecation javadoc:
   - target minimum version for removal
   - pointers to replacements for the deprecated method
   - version in which method was deprecated

> This policy is officially in effect as of January 20201.

Note that deprecation removal targets are not a hard commitment, and the deprecated methods **could live on further than these minimum target GA versions** (ie. only the most problematic deprecated methods will be removed aggressively).

:warning: That said, deprecated code that has outlived its minimum removal target version may be removed in any subsequent release (including patch releases, aka service releases) without further notice. So users should still strive to update their code as early as possible.
