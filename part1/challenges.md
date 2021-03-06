# Challenge tracking

## The Score Board

In order to motivate you to hunt for vulnerabilities, it makes sense to
give you at least an idea what challenges are available in the
application. Also you should know when you actually solved a challenge
successfully, so you can move on to another task. Both these cases are
covered by the application's score board.

![Partly solved Score Board](img/score-board_partly.png)

On the score board you can view a list of all available challenges with
a brief description. Some descriptions are very explicit hacking
instructions, others are vaguely describing what to do, leaving it to
you to find out what needs to be done.

The challenges are rated with a difficulty level between 1 and 5 stars,
with more stars suggesting a higher difficulty. These ratings have been
continually adjusted over time based on user feedback. Visible
difficulty ratings allow you to influence your own hacking pace and
learning curve significantly. When you pick a 4- or 5-star challenge you
_expect_ a real challenge and should be less frustrated if you fail on
it several times. On the other hand if hacking a 1- oder 2-star
challenge takes very long, you might realize quickly that you are on a
wrong track with your chosen hacking approach.

Finally, each challenge states if it is currently _unsolved_ or
_solved_. The current overall progress is represented in a progress bar
on top of the score board. Especially in group hacking sessions this
allows for a bit of competition between the participants.

## Success notifications

The OWASP Juice Shop employs a simple yet powerful gamification
mechanism: Instant success feedback! Whenever you solve a hacking
challenge, a notification is _immediately_ shown on the user interface.

!["Challenge solved!" push notification](img/notification.png)

This feature makes it unnecessary to switch back and forth between the
screen you are attacking and the score board to verify if you succeeded.
Some challenges will force you to perform an attack outside of the Juice
Shop web interface, e.g. by interacting with the REST API directly. In
these cases the success notification will light up when you come back to
the regular web UI the next time.

To make sure you do not miss any notifications they do not disappear
automatically after a timeout. You have to dismiss them explicitly. In
case a number of notifications "piled up" it is not necessary to dismiss
each one individually, as a simple reload of the UI in the browser (`F5`
key) will dismiss all at the same time.

## Continue codes {#continueCodes}

The ["self-healing" feature](running.md#selfHealing) - by wiping the
entire database on server start - of Juice Shop was advertised as a
benefit just a few pages before. This feature comes at a cost, though:
As the challenges are also part of the database schema, they will be
wiped along with all the other data. This means, that after every
restart you start with a "clean" 0% score board and all challenges in
_unsolved_ state.

To keep the resilience against data corruption but allow users to "pick
up where they left off" after a server restart, the concept of _continue
codes_ was introduced. The idea was taken from 80's and 90's console
games, where _saving_ the state of the game was not possible on the
read-only game cartridges.

At the bottom of the score board you can find a long character sequence
which represents your currently _solved_ challenges:

![Continue code section of the Score Board](img/continue-code.png)

You are strongnly encouraged to __copy or write down your latest
continue code regularly__, e.g. into some text file. After a server
crash, you can then simply restore the previous hacking progress:

1. Restart the application (e.g. via `npm start` or by restarting the
   Docker container).
2. Navigate to the (now wiped) score board.
3. Scroll to the bottom and click on the _Ambulance_ button.
4. Copy & paste (or type in) the latest continue code.
5. Click the _Restore Progress_ button.

The score board will now be restored to its prior state and - depending
on how many challenges you solved up to that point - a torrent of
success notifications will light up. As mentioned earlier these can be
bulk-dismissed by reloading the page with the `F5` key.
