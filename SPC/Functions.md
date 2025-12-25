| Function Type              | Real-World Use Cases                                                  |
| -------------------------- | --------------------------------------------------------------------- |
| **No args, No return**     | Display menus, show messages, initialize systems, play sounds         |
| **With args, No return**   | Print receipts, send notifications, log data, update displays         |
| **No args, With return**   | Get current time, generate random numbers, read sensors, check status |
| **With args, With return** | Calculate prices, validate inputs, convert units, process data        |

┌─────────────────────┐
│   CODE SEGMENT      │  ← Program instructions
├─────────────────────┤
│   DATA SEGMENT      │  ← Global/static variables
├─────────────────────┤
│   HEAP              │  ← Dynamic memory (malloc)
│   (grows down)      │
│         ↓           │
│                     │
│         ↑           │
│   STACK             │  ← Function calls (grows up)
│   (grows up)        │     Each recursive call adds a frame here! 
├─────────────────────┤
│ main() stack frame  │
│ recursiveFunc(3)    │
│ recursiveFunc(2)    │
│ recursiveFunc(1)    │
│ recursiveFunc(0)    │
└─────────────────────┘