# Booking Lab Evidence Record

**Name:** Chaiyanun Sakulsaowapakkul
**Student ID:** 6681299
**Repository:** https://github.com/chaiyanunSaku/iccs471-booking-lab-Chaiyanun-Sak

## Goal
The service incorrectly accepts overlapping bookings in the same room. I had to change the booking that overlaps an existing booking in the same room raises ValueError and must not store a rejected booking. 

## Constraints / Out of Scope
Permitted edits are only 1. booking_app/booking.py and 2. tests/test_booking.py only. What had to remain intact is current validation and
baseline tests. Other files should remain the unchanged. 

## Key Decision and Agent Claim
I always love planning with AI because it gives me a big picture. The plan it suggested was great and made sense because the prompt was very specific, for example, we deliberately told the Ai to preserve all the existing validation and tests, and it added new tests. It would only edit those files that I told them to which were booking.py and test_booking.py. So I accepted the implementation. 

Copilot said it had implemented the overlap rule in booking.py and add tests in test_booking.py then 7 tests passed; reported with no errors so I checked it by myself whether it changed any test it was not supposed to. Checked on how valid the new tests are and ran the demo one last time. Copilot's claim were accurate because Stored bookings went down to 3 from 4 and overlapping booking in room A has been rejected.

## Verification: Claim → Evidence
- **Claim:** Overlapping booking in the same room are rejected and not stored.
- **Command or test I ran:** uv run python -m unittest discover -s tests -v
- **Actual result:** Ran 7 tests and all were OK.
- **What this supports:** The claim was true because the test case about overlapping rule were passed. 

## Manual Validation
When I first ran demo the Stored bookings was 4 and the Overlapping booking in room A were accepted which was a (BUG) so after all the fixes and when I ran demo.py again, the Stored bookings went down from 4 to 3 and the overlapping booking in room A were rejected because the booking overlaps an existing booking whilst all other type of booking are working as expected so the Copilot didn't break anything and did its job well. 

## Remaining Uncertainty
Even though all of the tests passed but it doesn't mean that I've covered all of the possible case. I was thinking about concurrency, what if two booking booked at the same time and caused data racing.
