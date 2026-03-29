Exception 1: 2025-02-20 - AUDUSD - stale price

Exception summary:
On 2025-02-20, the dashboard flagged a high-severity variance in AUDUSD. Expected P&L was -$4,470.56 versus reported P&L of -$148.06, creating a variance of +$4,322.50.

Why it was material:
This was one of the largest breaks in the entire sample and far exceeded the project materiality threshold of $150. Because of its size, it would have materially distorted daily book-level P&L reporting and would require immediate review in a real middle-office environment.

Investigation steps:
I first compared expected and reported P&L at the date-instrument level. I then reviewed end-of-day position, current close, and prior close data for AUDUSD. I compared the variance to the stale-price candidate calculation, defined as end position multiplied by the difference between prior close and current close. I also ruled out missing trade and duplicate booking explanations by checking the same-day trade impact tests.

Conclusion:
The variance was consistent with a stale price break. The exception matched the mark difference that would result from using prior close instead of current close to value the end-of-day AUDUSD position.

Control recommendation:
Add a control that compares current-day marks to prior-day marks and flags unchanged prices when the instrument had a non-zero position and a measurable market move.

Exception 2: 2025-01-20 - GBPUSD - duplicate booking

Exception summary:
On 2025-01-20, the dashboard flagged a medium-severity variance in GBPUSD. Expected P&L was -$267.22 versus reported P&L of -$630.08, producing a variance of -$362.86.

Why it was material:
The break exceeded the materiality threshold and ranked as a meaningful daily reporting difference. In a live environment, a variance of this size would warrant same-day review because duplicate trade booking can affect both P&L and downstream operational records.

Investigation steps:
I reviewed the trade-level detail for GBPUSD on the flagged date and tested the variance against the same-day trade impact logic. I then checked whether the variance closely matched the contribution of any individual trade if that trade were counted twice in the reported system. I also ruled out stale price and wrong-position explanations by comparing the variance to those candidate calculations.

Conclusion:
The variance was most consistent with duplicate booking. The observed difference aligned with the P&L contribution of one same-day GBPUSD trade being counted an additional time in reported P&L.

Control recommendation:
Add a duplicate-trade control that checks for repeated trade IDs or repeated economic trade fingerprints before reported P&L is finalized.

Exception 3: 2025-01-06 - GBPUSD - missing trade

Exception summary:
On 2025-01-06, the dashboard flagged a low-severity but material variance in GBPUSD. Expected P&L was -$1,018.23 versus reported P&L of -$782.78, creating a variance of +$235.45.

Why it was material:
Although smaller than the largest breaks in the sample, the variance still breached the project threshold and represented a meaningful difference in desk-level daily reporting. Missing trades are also operationally important because they can affect position, P&L, and reconciliation workflows.

Investigation steps:
I reviewed the same-day GBPUSD trade activity and compared the variance against the expected impact of each trade using the trade-level contribution logic. I specifically tested whether the reported-versus-expected difference could be explained by one trade being absent from the reported view. I also ruled out stale price and fee explanations because the variance aligned more closely with trade-level booking logic.

Conclusion:
The variance was most consistent with a missing trade. The break matched the removal of one same-day GBPUSD trade’s P&L contribution from the reported system.

Control recommendation:
Implement a daily trade completeness reconciliation between executed trades and reported trades before finalizing P&L.

Exception 4: 2025-01-03 - AUDUSD - wrong position

Exception summary:
On 2025-01-03, the dashboard flagged a low-severity variance in AUDUSD. Expected P&L was -$474.68 versus reported P&L of -$695.18, producing a variance of -$220.50.

Why it was material:
The break exceeded the $150 threshold and indicated that reported P&L may have been distorted by a position-level issue rather than a pure trade-booking issue. Position errors are important because they can affect both daily marks and broader risk reporting.

Investigation steps:
I reviewed the daily close and prior close movement for AUDUSD and compared the variance to an implied quantity mismatch calculation. I then assessed whether the variance could be explained by a plausible round-lot position difference rather than stale price or trade-level booking effects. Trade-based explanations were weaker than the position-based explanation.

Conclusion:
The variance was most consistent with wrong position. The implied quantity mismatch was in line with a plausible round-lot difference in the reported end-of-day position, which would distort mark-to-market P&L.

Control recommendation:
Add a daily position roll-forward control that compares start position, net trade activity, and end position, with automatic escalation for unexplained quantity differences.