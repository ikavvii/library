| Scenario            | Input Data                         | Expected Result                       | Technique Used           |
| ------------------- | ---------------------------------- | ------------------------------------- | ------------------------ |
| **Card Validation** | Invalid Card                       | Eject card; "Invalid Card" message    | BBT                      |
| **PIN Entry**       | Correct PIN (1st try)              | Prompt for Amount                     | BBT                      |
| **PIN Security**    | Incorrect PIN (3 times)            | Seize card; "Contact Manager" message | State Transition         |
| **Amount Logic**    | Amount = 250 (Not multiple of 100) | "Enter amount in multiples of 100"    | Equivalence Partitioning |
| **Balance Check**   | Amount = 500 (Balance = 200)       | Eject card; "Insufficient Funds"      | BBT                      |
| **Successful Trx**  | Amount = 500 (Balance = 1000)      | Dispense ₹500; Eject card; Receipt    | BBT                      |
