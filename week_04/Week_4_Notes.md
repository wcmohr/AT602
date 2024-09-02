###### Standing Questions
Pure premium: to policyholder only or also administrative, etc?
#### Week 4 Notes - Loss Metrics

##### Loss Metrics - Vocabulary

* Perils - Classes of events that might cause damage.
* Exclusions - Perils explicitly not included in the policy (war, arson, etc.)
* Premium - based on rating variables (value of car, stops by police, etc.)
* Effective Date - Beginning of policy
* Expiration Date - Planned end of policy
* Cancellation Date - Date of cancellation, if applicable (difficult for insurers, so likely from policyholder)
* Incurred Losses - Total amound paid to settle claims.  Includes payments to insured/ victims of insured as well as payments to doctors, lawyers, inspectors involved in researching claim.
* Indemnification - return insured's vehicle, home. etc to condition prior to incident (not below, definitely not above, as excess compensation leads to adverse incentives).
* Limit: max payment

**Methods to reduce an insured's incentive to intentionally cause damage to insured aset** 
* Policy limit - Never above asset's worth.
* Deductible - portion of loss insured must pay themselves.
* Copay - percentage of loss rather than specific dollar amt.
* Short-tailed lines: lines of business with rapid settlement.
* Long-tailed lines: malpractice, workers comp. could involve payments of lifelong annuities.  ultimate cost thus hard to project

*HOW MUCH DATA TO USE?*
\
Short-tailed - makes sense not to look too far back, since risks change (car safety changes, global warming impacts, hurricane/fire risks, etc.).  Data should neither be too recent, since it takes time to process claims.

Accounting period: usually a period of a year that ends at most 3 months prior to current date.  Always pretend to be in accounting period when doing analysis.

##### Loss Metric Formulas Video Notes
*Formulas*
* **Frequency** 
#Claims/EarnedExposure
* **Severity** *$IncurredLosses/#Claims* --> average amount insurance company will pay for any claim that gets reported to the company
* **Pure Premium**, *\$IncurredLoss/EarnedExposure* = *Frequency\*Severity* --> average amount paid by insurer for each exposure
* **Loss Ratio** | *\$IncurredLoss/EarnedPremiums* | How many cents paid to customers for claims per dollar of premiums.

##### Loss Metric Calculations Part 1 Video Notes
**Policies Sheet**
1) Add territory info with VLOOKUP, creating named range for easy inter.
2) Written Premium w/ VLOOKUP & Named Range
3) Accounting Dates: AcctStart, AcctEnd. Note that time of day is an important part, so need to add 1 when subtracting 4/1/12 from 3/31/13 to get Earned Days, Earned Exposure values
4) Full Term Days: Expiration - Start 
5) earned exposure: earned days / full term
6) Start Date: max(acctstart, Effective Date)
7) end date: min(cancellation, expiration, acctend)
8) Earned Days: max(end - start,0)
Check work by sorting on earned exposure.
Formulas -> Calculation options -> manual so that sheet doesn't auto update calculations, saving time
9) Earned Premium: Written Premium* earned exposure
10) Claim Count: =sumifs(PolicyID matches, in accounting period = 1)
11) Incurred Loss: =sumifs(Incurred loss in acounting period)

**Claims Sheet**
Create "In Acct Period" column
* =if(and(B2>=acctstart,B2<=acctend),1,0)
Incurred Loss in Acct Period
* =sumifs("In Acct Period == 1", PolicyID matches)
* Loss payments can be negative, i.e. a 'taking down' of reserve 

**Loss Payments Sheet**
create "In Acct Period" column
1) =if(and(B2>=acctstart,B2<=acctend),1,0)

##### Loss Metric Calculations Part 2 Video Notes
1) Create *Loss Metrics* sheet, inserting pivot table using entire policies sheet with values of sum of earned exposure, sum of earned premium, sum of claim count, and sum of incurred loss
2) calculate with *cell references* not getpivotdata() Frequency (SumClaimCount/SumEarnedExposure), Severity (SumIncurredLoss/SumClaimCount), Pure Premium (SumIncurredLoss/SumEarnedPremium or equivalently Severity*Frequency), Loss Ratio (SumIncurred Loss/SumEarnedPremium) 
3) stratify pivot table by territory, adding territory to the rows of the pivot table.  Update cell references of metrics, add % to frequency and ratio, $ to severity and pure premium
4) Conditionally format with color scales for each column.
5) Aggregate next on Year Built, Group by decade.





