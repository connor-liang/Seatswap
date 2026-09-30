# SeatSwap

A clickable iPhone prototype. When a guest drops out of a group dinner at the last minute, the organizer can fill the seat with the right people.

Open `index.html` in any browser. It's a single file with no build step and no dependencies. On a desktop it renders inside an iPhone frame with a demo panel beside it. On a phone it fills the screen, and the **Demo** button in the header opens the same controls.

## Screens

| # | Screen | Where |
|---|--------|-------|
| 1 | Feed | **Open spots** tab. Each card shows the restaurant, time, seats, attendees, a countdown, a "why you see it" tag and Accept |
| 2 | My Reservations | **Reservations** tab. Status for each table, plus **+ Post an Open Spot** |
| 3 | Post flow | Six steps, one per screen: restaurant, date/time, who's going, seats open (1–4), note, no-show fee |
| 4 | Audience | Urgency banner, then Recommended, Close Friends, Lists, Individuals and Friends of friends, then Send |
| 5 | Live Status | Tap your own reservation. Shows notified/viewed/declined counts, the stage timeline, add/remove people and cancel |
| 6 | iMessage | The message icon in the header. Each text link opens the spot |
| 7 | Spot Detail | Tap a feed card. Shows details, mutuals, fee and seats left, with Accept / Not this time |
| 8 | Accepted | After accepting. Add to calendar, message the group, cancel your seat |
| 9 | Filled | Shown to the organizer when seats hit 0, and to anyone who opens a filled link |
| 10 | Friends | **Friends** tab. Tabs for Following, Close Friends, each list and Friends of friends; create and edit lists |

## Rules implemented

- **Send** creates a push notification and a text link for each person.
- **Under 12h to dinner:** Close Friends, Recommended and friends of friends are all notified at once.
- **Over 12h:** Close Friends and Recommended go first, and friends of friends are queued for stage 2. If the spot is still unfilled after 10h, or once dinner is under 12h away, the organizer is asked "Expand to friends of friends?"
- **Recommended** means people who know 2+ attendees, ranked by how many attendees they know and then by mutuals, with the reason shown ("Knows Maya & Sam").
- **Friends of friends** are tagged with who connects them ("Followed by Maya +1").
- The organizer can add or remove people at any stage. Removing someone hides only this spot from them.
- Only the organizer can post, edit or cancel. Canceling removes the spot from every feed and link.
- A spot is visible only to the people it was sent to.
- **Not this time** hides the spot for that person and shows them as declined to the organizer.
- The first accept wins. Each accept lowers the seat count and alerts the organizer. At 0 the spot shows as Filled and leaves every feed.
- Accepting adds the person to the attendees. The no-show fee applies only if they cancel later, and then the seat reopens to the same audience.
- Spots expire at start time.
- There is no login and no payments.

## Demo controls

- **Viewing as:** switch between 18 people to see the same spot from the organizer's side and a guest's side. Alerts sent to someone while you weren't viewing as them appear when you switch to them.
- **Fast-forward 10h** (and **+1h**): moves the simulated clock to trigger the expansion prompt and expiry.
- **Simulate guests:** a random recipient views, declines or accepts the spot you're looking at.
- **Reset demo** restores the seed data. Reloading the page does the same.

The simulated clock starts at 2:00 PM today every time the page loads.
