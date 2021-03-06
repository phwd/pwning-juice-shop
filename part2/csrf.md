# Cross Site Request Forgery (CSRF)

> Cross-Site Request Forgery (CSRF) is an attack that forces an end user
> to execute unwanted actions on a web application in which they're
> currently authenticated. CSRF attacks specifically target
> state-changing requests, not theft of data, since the attacker has no
> way to see the response to the forged request. With a little help of
> social engineering (such as sending a link via email or chat), an
> attacker may trick the users of a web application into executing
> actions of the attacker's choosing. If the victim is a normal user, a
> successful CSRF attack can force the user to perform state changing
> requests like transferring funds, changing their email address, and so
> forth. If the victim is an administrative account, CSRF can compromise
> the entire web application.[^1]

## Challenges covered in this chapter

| Challenge                                                                 | Difficulty |
|:--------------------------------------------------------------------------|:-----------|
| Change Bender's password into _slurmCl4ssic_ without using SQL Injection. | 4 of 5     |

### Change Bender's password into _slurmCl4ssic_ without using SQL Injection {#csrfChallenge}

This challenge can only be solved by changing the password of user
Bender into _slurmCl4ssic_. Using any sort of SQL Injection will _not_
solve the challenge, even if the password is successfully changed in the
process.

#### Hints

* The fact that this challenge is in the CSRF category is already a huge
  hint.
* It might also have been put into the
  [Weak security mechanisms](weak-security.md) category.
* Bender's current password is so strong that brute force,
  [rainbow table](https://en.wikipedia.org/wiki/Rainbow_table) or
  guessing attacks will probably not work.

----

[^1]: https://www.owasp.org/index.php/CSRF
