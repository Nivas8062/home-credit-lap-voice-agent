# Test Cases — Home Credit LAP Voice Agent

Record only outcomes actually observed in Retell. The results below reflect the test transcripts described during development; transfer execution still requires checking in Retell.

| ID | Scenario / test input | Expected behavior | Actual result / status |
|---|---|---|---|
| TC-01 | Customer confirms identity and provides all required eligible details: residential property, sole ownership, original documents available, ₹50 lakh request, salaried, income credited through bank, estimated market value ₹1 crore, 10-year tenure. | Capture all eight fields, do not repeat answered questions, then offer preliminary handoff without claiming approval. | **Passed in test transcript**; agent asked for remaining market value and tenure, then gave a preliminary handoff. |
| TC-02 | Customer says the property is agricultural. | Immediately explain that agricultural property does not meet the criteria, thank the customer, and end the call. | **Passed in test transcript**. |
| TC-03 | Customer says income is received in cash. | Explain that bank-received income is required and end the call; do not continue qualification or promise a callback. | **Passed in test transcript**. |
| TC-04 | Customer says they already have a loan against their residential property and want to reduce their existing EMI / transfer the loan. | Stop fresh-loan qualification and route to the loan-transfer specialist. Call `transfer_call` only if configured; verify function execution and call ending in Retell. | **Response behavior observed**: agent said it would connect the customer with the appropriate specialist. **Function execution not yet verified**; do not mark live transfer as passed until Retell confirms it. |
| TC-05 | Greeting test. | Agent says “Home Credit,” not “Home Credits.” | **Latest transcript passed** with “Home Credit.” |
| TC-06 | Requested amount exceeds ₹75 lakh. | Explain the maximum is ₹75 lakh and ask whether the customer accepts it; continue only if accepted. | Not yet verified. |
| TC-07 | Original property documents are unavailable. | Disqualify immediately and end the call. | Not yet verified. |
| TC-08 | Customer chooses a tenure below 3 years or above 15 years. | Ask for a valid tenure; disqualify if the customer will not select 3–15 years. | Not yet verified. |
| TC-09 | Customer is busy. | Ask for a convenient callback time, record it if supported, and end the call without starting qualification. | Not yet verified. |
| TC-10 | Customer is not the intended person. | Do not disclose offer details; politely end the call. | Not yet verified. |

## Overall status
The basic qualification, agricultural-property rejection, cash-income rejection, and corrected greeting have been observed in test transcripts. Existing-loan transfer wording has been observed, but actual function execution and transfer destination must be verified. Run the remaining cases before claiming complete test coverage.
