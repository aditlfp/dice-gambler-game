## 2025-05-14 - [Optimizing Elemental Combo Detection]
**Learning:** In action-heavy functions like `processRoll`, redundant array iterations for conditional checks (e.g., checking for Fire, then Water, then Wind) create O(E*D) overhead where E is the number of elements and D is the number of dice. Aggregating dice state into a frequency and position map in a single O(D) pass allows for O(1) or O(E) checks later, significantly reducing allocation and iteration overhead.
**Action:** Always look for patterns where multiple `filter()` or `includes()` calls are used on the same small collection to check for different conditions. Replace with a single-pass frequency/state map.

## 2025-05-14 - [Scope and Definition Vigilance]
**Learning:** Even when optimizing algorithms, forgetting to define local aliases for global or object-property variables (like `B` for `G.B`) can lead to critical `ReferenceError` crashes.
**Action:** Before finalizing any refactor, perform a manual "definition sweep" to ensure every variable used is either defined in the local scope or explicitly accessed from its parent object.

## 2025-05-14 - [State Leakage and UI Stale States]
**Learning:** In frontend applications that reuse UI elements across different game states (like a shared roll button across battles), failing to reset UI properties (like `disabled`) when entering a new state can lead to "soft locks" where the user cannot interact with the game.
**Action:** Always include a comprehensive UI state reset in the initialization or entry function of a state (e.g., `renderBattle`).
