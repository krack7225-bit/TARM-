# TARM-
Trade and risk management algo


Discipline Guardian (MT5 Expert Advisor) (PC only as of creating this version)

DisciplineGuardian is a robust, production-ready risk-management Expert Advisor (EA) built for MetaTrader 5 (MQL5). It enforces strict trading discipline, eliminates emotional overtrading, protects capital during volatile market conditions, and automates key trade-management targets.

Key Features

Advanced Streak & Trade Mix Lockouts: Automatically locks out the account for the remainder of the trading week based on configurable individual trade performance thresholds.
Automated Trade Management: Manages open positions dynamically by shifting the Stop Loss (SL) to Break-Even (BE) at a 1.5% profit move and automatically closing full positions at a 3.0% profit target.
Time-Zone Specific Safety Rules: Features a built-in time rule that automatically locks out trading at **12:00 PM UTC+3 (Nairobi Time) every Friday to prevent weekend holding risks.
Real-Time On-Screen Dashboard: Renders a clean graphical canvas overlay directly on the MT5 chart showing account starting balance, active streak counts, and color-coded status (`NORMAL` vs ` LOCKED OUT`).
Automated Email Notifications: Integrates with MT5's native SMTP system to send instant alerts for break-even adjustments, target closures, and lockout triggers. Persistent Weekly Enforcement: Once a lockout is initiated, it cannot be manually bypassed by restarting the platform—it automatically resets only when a new trading week begins on Monday.


Lockout & Risk Rules

| Rule Type | Trigger Condition | Description |

| Loss Streak | 2 Consecutive Losses | Triggers if 2 trades in a row each lose more than 0.45% of the starting balance (ignoring small break-even trades). |
| Win Streak | 2 Consecutive Wins | Triggers if 2 trades in a row each yield 2.0% or more of the starting balance. |
| Trade Mix | 1 Loss + 1 Win + 1 BE | Triggers if the last 3 closed trades contain a mix of 1 Loss, 1 Win, and 1 Break-Even trade in any order. |
| Thursday Win | Win $\ge 2.0\%$ on Thursday | Triggers an immediate weekly lockout if any trade closes on a Thursday with a profit of 2% or greater. |
| Friday Time Limit | Friday at 12:00 PM UTC+3 | Automatically initiates a hard account lockout every Friday at 12:00 PM Nairobi time. |


 Input Parameters

| Parameter Group | Input Name | Default Value | Description |
| --- | --- | --- | --- |
| Streak & Rules | `InpLossThresholdPct` | `0.45` | Minimum percentage loss for a trade to count as a loss. |
|  | `InpMaxLossStreak` | `2` | Maximum consecutive losses allowed per week. |
|  | `InpWinThresholdPct` | `2.00` | Minimum percentage gain for a trade to count as a win. |
|  | `InpMaxWinStreak` | `2` | Maximum consecutive wins allowed per week. |
| Trade Management | `InpMoveToBEPct` | `1.50` | Profit percentage required before moving SL to Break-Even. |
|  | `InpFullTargetPct` | `3.00` | Profit percentage required to close the full trade. |
| Notifications | `InpEnableEmailAlerts` | `true` | Enables or disables SMTP email alerts via MT5 `SendMail`. |


Installation & Setup

1. Open your MetaTrader 5 desktop platform and press F4 to open MetaEditor.
2. Create a new Expert Advisor file (`File -> New -> Expert Advisor (template)`), name it `DisciplineGuardian`, and click Finish.
3. Replace the template code with the contents of `DisciplineGuardian.mq5`.
4. Click Compile (`F7`) and verify it compiles with 0 errors and 0 warnings.
5. Return to MT5, and ensure Algorithmic Trading is enabled in the top toolbar.
6. Drag DisciplineGuardian from the Navigator window onto any chart, adjust your inputs, and click OK.



Requirements
Platform: MetaTrader 5 (Desktop version required for execution loops; mobile apps can be used for monitoring).
Environment: Compatible with any standard MT5 broker setup. Recommended to run on a 24/7 VPS for uninterrupted automated protection.

---

*Developed by Stanley Mwangi (11/13/2026).*
