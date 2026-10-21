# Cadent Family privacy policy — proposed additions for 1.0.9

Draft by Science Officer WEB · Site, 2026-10-20, revised the same day with
facts verified against the code by Captain CAD · App (migrations 012, 032;
billing path). For Fleet Commander to carry to Grant. **Nothing here is on the site.** `privacy.html` changes only after
Grant approves the exact wording below; then "Last updated" moves to the day
it ships, and `fcc_app/PLAY_DATA_SAFETY.md` and the Play Data safety form
gain the Purchase history row at the same time.

Sources checked: `fcc_app/CLAUDE.md` (Membership, Links, Kid mode, Claiming a
device, The points economy, act-as), `fcc_app/MONETIZATION.md`,
`fcc_app/PLAY_DATA_SAFETY.md`, `fcc_app/site-handoff/README.md`. Every
sentence below states something the code does today; nothing is aspirational.

Why these four are needed: 1.0.9 shipped (1) a paid membership through Google
Play, (2) permanent contact links that resolve to a display name for anyone
holding the link, (3) kid mode with a PIN, and (4) device claims. The current
policy (dated 12 September 2026) mentions none of them. (1) is a Play
requirement: the Data safety form must list Purchase history once billing is
live, and the policy must match the form.

---

## A. "What we collect" table — one new row

Insert after the row "Chores you complete, the points they earn, and rewards you ask for":

| What | Why |
|---|---|
| Your family's membership record from Google Play: a Google purchase token, the order numbers, the product, the subscription's state (active, in grace, cancelled or expired), its expiry date and whether it renews | To know how many schedule imports your family has each month. **What we hold is that record and nothing more: the purchase happens in Google Play's own payment sheet, and the app sends us only the product name and the purchase token. No card, payment method, billing address or payer name reaches our server or the app.** |

## B. New section, after "Family sharing and privacy within a family"

### Membership and payments

Cadent Family is free. A family can buy an optional monthly membership that
adds schedule imports. You buy it in Google Play's own payment sheet, and
Google processes the payment under its own terms and
[privacy policy](https://policies.google.com/privacy). The app sends our
server the product name and a purchase token; our server asks Google what
that token is worth and stores the answer: the order numbers, the product,
the subscription's state, its expiry date and whether it renews. That record
is what tells the app how many imports your family has. Your card, payment
method, billing address and the name on the payment never reach us.

The subscription itself belongs to the Google account that bought it. To
stop it, cancel it in Google Play; it then runs to the end of the paid month
and nothing else in the app changes. **Deleting your Cadent Family account
or your family removes our record of the membership but does not cancel the
subscription**: only Google Play can do that.

### Contact links

Each person has a contact link, shown on the Contacts screen, that they can
send to a grandparent, a co-parent in another home or a coach. **Anyone who
opens your link can see your display name and ask to add you as a contact**;
you are asked before anyone is added, and you choose which events to share
with each contact afterwards. Because a link can be forwarded, treat it like
a phone number: share it with people you know, and tap **Reset my link** to
make every copy of the old one stop working.

### Kid mode

Kid mode locks a shared tablet to one child's view behind a PIN. **The PIN is
stored only on that tablet**, as a salted hash, and is never sent to our
server or shared with the family. Clearing the app's data on the tablet
removes it. Kid mode does not create an account for the child and does not
change what the server allows; it only keeps the tablet on the child's view.

### Claiming a place in the family

Children added by a parent have no account. When a child is old enough for
their own sign-in, a parent can make a one-time claim code. The child signs
in with their own Google account or email, enters the code, and that sign-in
becomes attached to their existing place in the family, so their chores,
points and streak carry over. The code works once and expires; a code cannot
take over a member who already has a sign-in. From then on the child's name,
email and sign-in account are collected as described under "What we collect".

### When a parent acts for a child

A parent can tick a chore or redeem a reward on a child's behalf. The points
land on the child, and we record which parent did it. Only the child, the
parent who acted, or a family parent can undo a chore completion, and only
within the current period, so points already earned are not quietly removed.

## C. "What is deleted" list — one added line

- If the family is deleted with you: the family's membership record and its record of schedule imports used. If the family carries on, those records stay with the family with your name removed from them. **Neither case cancels a Google Play subscription; cancel that in Google Play.**

## D. Owner-notes comment (invisible) — replace the "STILL OPEN" block

```
     Revised <date>: adds the Play membership (migration 032), contact links
     (023/033, link.longtablelabs.com Worker), kid mode PIN (device-local,
     lib/state/kid_mode.dart), member claims (036) and act-as (035) from app
     1.0.9. Data safety form gains "Purchase history" the same day.
     STILL OPEN: confirm the Anthropic links and their current commercial-terms
     wording; postal address only if a store or region requires it.
```

## E. Header

"Last updated: September 12, 2026" → the ship date.

---

## Points for Grant to decide

1. **Section B, Contact links** states plainly that the display name is visible
   to anyone holding the link (this is how a pasted link unfurls as "Add
   Grant"). It is true today. Keep the sentence, or soften to "can see who the
   link belongs to"?
2. *Answered 2026-10-20 by Captain CAD · App.* Deleting the family deletes
   its membership record and import-credit ledger (`ON DELETE CASCADE`,
   migrations 032:52 and 012:27); if the family continues, the records stay
   and the departing person's id is set to NULL. Sections B and C above say
   exactly that, and both state that deletion does not cancel the Google
   Play subscription.
3. The policy's existing Children section says children have no login. With
   claims, a child *can* end up with a login at an age the parent chooses.
   Suggested one-line addition to "Children": "When a parent chooses to give a
   grown child their own sign-in (see *Claiming a place in the family*), that
   child becomes an ordinary account holder." Google's Families policy and the
   13+ target audience declaration should be re-read against this.
4. `support.html` already states the price and "cancel in Google Play"; the
   policy text above matches it.
