>Draw an Activity Chart to depict the process of cancellation of booked train tickets.

![](attachments/Pasted%20image%2020260509214406.png)

**Activity Chart: Cancellation of Booked Train Tickets**

**Flow Narrative:**

1. **Start:** User logs into the IRCTC/Railway portal.
2. **Selection:** User navigates to "Booked Tickets" and selects the specific PNR for cancellation.
3. **Validation (Decision):** System checks if the train has already departed or if the chart is prepared.
    - _If Yes:_ Display "Cancellation Not Possible" and end.
    - _If No:_ Proceed to cancellation request.
4. **Confirmation:** System calculates the refund amount based on current railway rules (e.g., time remaining before departure) and displays it to the user.
5. **User Decision (Decision):** User confirms "Cancel Ticket" or "Abort."
6. **Concurrent Activities (Fork):** If confirmed, the system simultaneously:
    - **Activity A:** Update the database to release the seat/berth for others.
    - **Activity B:** Initiate the refund process through the payment gateway.
    - **Activity C:** Generate and send a cancellation SMS/Email to the user.
7. **Join:** Merge parallel tasks.
8. **End:** Bullseye node indicating completion.