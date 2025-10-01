# 🍁 2x Leveraged ETF Trading Guide & Paper Trader

An interactive educational paper trading simulator with comprehensive guidance on 2x leveraged ETFs (MSTU, MSTR, TSLL, IBIT). Features automatic FIFO position tracking, JSON import/export, and a beautiful autumn-themed UI.

## 🎯 Overview

This is an **educational thought exercise** and paper trading simulator designed to help you understand and practice trading strategies for 2x leveraged ETFs in a risk-free environment. The tool combines:

- **📊 Interactive Paper Trading Journal** - Track simulated trades with automatic FIFO pairing
- **📚 Comprehensive Educational Content** - Deep dive into leveraged ETF mechanics, risks, and strategies
- **🔄 Automatic Position Tracking** - FIFO (First In, First Out) pairing system
- **💾 Data Persistence** - localStorage + cookie backup with JSON import/export
- **🎨 Beautiful UI** - Autumn-themed design with intuitive controls

## ⚠️ Important Disclaimer

**This is purely educational and does not constitute financial advice.**

- All trades are simulated with no real money involved
- Designed for deep contemplation and strategy development
- No score system - only learning and reflection
- Do not use as a basis for real trading without consulting a qualified financial advisor
- Real trading involves substantial risk of loss

## ✨ Key Features

### 📈 Paper Trading Simulator

- **Add Trades**: Input ticker, BUY/SELL, shares, price, date, and notes
- **Automatic FIFO Pairing**: Sells automatically match with oldest available buy shares
- **Position Tracking**: See available shares for each open position
- **Split Trade Handling**: Large sells spanning multiple buys are automatically split
- **Magic Shares**: Tracks sells without prior buys (short positions or data entry errors)

### 🔗 Parent-Child Trade Hierarchy

- **BUY entries** are parents showing all child SELL trades
- **SELL entries** appear as children under their source BUY
- **Split sells** appear under multiple BUYs with clear indicators
- **Available shares** displayed after each BUY's children

### 💰 P&L Tracking

- **Individual P&L** for each SELL pairing
- **Total P&L** across all positions
- **Win/Loss Rate** statistics
- **Color-coded** results (green for profit, red for loss)

### 🎮 Demo Data

Pre-loaded with 32 realistic trades across 2025 demonstrating:
- Bull Rocket scenarios (MSTU)
- Earnings plays (TSLL)
- ATM dilution impacts (MSTR)
- Scaling in/out of positions
- Loss scenarios and recovery attempts
- Partial position management

### 💾 Data Management

- **Auto-save**: localStorage + cookie backup (365-day expiration)
- **Download JSON**: Export all trades with timestamp
- **Upload JSON**: Import previously exported data
- **Clear All**: Reset to empty state
- **Demo Data**: Load 32 sample trades

### ⚡ Quick Actions

- **Auto-fill SELL**: One-click form population from available shares
- **Edit Trades**: Modify any trade details
- **Delete Trades**: Remove trades with automatic re-pairing
- **Collapsible Views**: Clean UI with expandable trade details

## 📚 Educational Content Included

### Core Topics Covered:

1. **What are 2x Leveraged ETFs?**
   - Mechanics and daily reset
   - Volatility decay explained
   - When to use vs. avoid

2. **Covered Tickers:**
   - **MSTU** - Defiance Daily Target 2X Long MSTR ETF
   - **MSTR** - MicroStrategy (unleveraged)
   - **TSLL** - Direxion Daily TSLA Bull 2X Shares
   - **IBIT** - BlackRock iShares Bitcoin Trust

3. **Trading Strategies:**
   - Bull Rocket scenario
   - Choppy Waters (when to avoid)
   - ATM Dilution Drag
   - ATM Completion Pop
   - Steady Climb (unleveraged safer)
   - FOMO Peak (profit taking)
   - Black Swan events

4. **Decision Matrix:**
   - BTC price trends
   - IBIT flows
   - M2 money supply
   - MSTR holdings
   - VIX levels
   - SEC filings

5. **TSLA/TSLL Deep Dive:**
   - When to trade TSLL vs. TSLA
   - Earnings plays
   - Product launches
   - FSD news catalysts
   - Risk factors unique to Tesla

6. **Saylor's ATM Strategy:**
   - Understanding MicroStrategy's at-the-market offerings
   - Impact on MSTR and MSTU
   - Trading around ATM periods

## 🚀 Getting Started

### Installation

1. **Clone or download** this repository
2. **Open `index.html`** in any modern web browser
3. **No dependencies** required - pure HTML/CSS/JavaScript

### First Steps

1. **Load Demo Data**: Click "🎮 Demo Data" to see 32 sample trades
2. **Explore Trades**: Click on collapsed bars (▶) to expand details
3. **Add Your Own**: Use the form to add paper trades
4. **Auto-fill**: Click "⚡ Auto-fill SELL" on positions with available shares
5. **Export**: Download your trades as JSON for backup

## 📖 How to Use

### Adding a Trade

1. Fill in the form fields:
   - **Ticker**: Stock symbol (e.g., MSTU, TSLL)
   - **Action**: BUY or SELL
   - **Shares**: Number of shares
   - **Price**: Price per share
   - **Date**: Trade date
   - **Notes**: Optional trade rationale

2. Click "Add Trade"

3. Trade automatically pairs via FIFO if applicable

### Using Auto-fill SELL

1. Find a BUY with available shares
2. Click "⚡ Auto-fill SELL" button
3. Form scrolls into view with pre-filled data
4. Enter the sell price
5. Click "Add Trade"

### Managing Trades

- **Edit**: Click ✏️ to modify trade details
- **Delete**: Click 🗑️ to remove a trade
- **Expand/Collapse**: Click the pairing bar to show/hide children

### Understanding the Display

```
📈 MSTR
  #1 BUY 300 shares @ $420.00
    🔗 SELL #2 (40 shares @ $410.00) P&L: -$400 (-2.4%) [✏️] [🗑️]
    🔗 SELL #3 (80 shares @ $385.00) P&L: -$2,800 (-8.3%) [✏️] [🗑️]
    📦 Available: 180 shares (Can sell up to 180 more) [⚡ Auto-fill SELL]
```

- **Green border**: BUY trades
- **Red border**: SELL trades (as children)
- **Purple border**: Magic BUY (sells without prior buy)
- **Collapsed bar**: Click to expand multiple pairings

## 🎨 Features Breakdown

### FIFO Pairing System

The app uses **First In, First Out** logic:

1. Each SELL automatically pairs with the oldest available BUY shares
2. If a SELL is larger than one BUY, it splits across multiple BUYs
3. Each portion shows accurate P&L for that specific pairing
4. Remaining shares tracked automatically

### Split Trade Example

```
BUY #1: 100 shares @ $50
BUY #2: 100 shares @ $52
SELL #3: 150 shares @ $55

Result:
  BUY #1 → SELL #3 (100 shares) [100 of 150 total]
  BUY #2 → SELL #3 (50 shares) [50 of 150 total]
```

### Magic Shares

When you sell without a prior buy (or exceed buy quantity):

```
✨ MAGIC BUY ∞ shares @ $0.00
  🔗 SELL #5 (20 shares @ $350) Revenue: $7,000
```

This tracks short positions or data entry errors.

## 📊 Portfolio Summary

The summary section shows:

- **Total Trades**: Count of all trades
- **Completed Pairs**: Number of buy-sell pairings
- **Win Rate**: Percentage of profitable trades
- **Total P&L**: Net profit/loss across all positions

## 🎓 Educational Outcomes

This tool helps you learn:

1. **Position Management**: How to scale in/out of positions
2. **Risk Management**: Understanding stop-losses and position sizing
3. **FIFO Accounting**: How shares are matched for tax/accounting
4. **Volatility Decay**: Why leveraged ETFs lose value in choppy markets
5. **Strategy Testing**: Try different approaches risk-free
6. **Trade Journaling**: Document your thought process

## 🏗️ Program Architecture

### System Design

The paper trader is built as a **single-page application (SPA)** with a clean separation of concerns:

```
┌─────────────────────────────────────────────────────────────┐
│                        User Interface                        │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │  Trade Form  │  │ Trade Journal│  │   Summary    │      │
│  │   (Input)    │  │  (Display)   │  │  (Analytics) │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│                      Business Logic                          │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │ FIFO Pairing │  │  P&L Calc    │  │  Validation  │      │
│  │   Engine     │  │   Engine     │  │    Rules     │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│                      Data Layer                              │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │ localStorage │  │    Cookies   │  │ JSON Export  │      │
│  │  (Primary)   │  │   (Backup)   │  │  (Portable)  │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└─────────────────────────────────────────────────────────────┘
```

### Core Components

#### 1. **Trade Management System**
- **Input Handler**: Validates and processes new trade entries
- **Trade Store**: In-memory array of trade objects
- **ID Generator**: Auto-incrementing counter for unique trade IDs
- **Date Handler**: Manages trade dates and chronological ordering

#### 2. **FIFO Pairing Engine**
- **Algorithm**: First In, First Out matching logic
- **Split Handler**: Divides large sells across multiple buys
- **Magic Share Tracker**: Handles sells without prior buys
- **Remaining Share Calculator**: Tracks available shares per position

#### 3. **Rendering Engine**
- **Hierarchical Display**: Parent BUY with child SELL structure
- **Collapsible UI**: Expandable/collapsible pairing details
- **Color Coding**: Visual indicators for profit/loss
- **Responsive Layout**: Adapts to different screen sizes

#### 4. **Persistence Layer**
- **Dual Storage**: localStorage (primary) + cookies (backup)
- **Auto-save**: Triggers on every trade modification
- **Import/Export**: JSON serialization/deserialization
- **Version Control**: Data format versioning for future compatibility

#### 5. **Analytics Engine**
- **P&L Calculator**: Per-trade and aggregate profit/loss
- **Win Rate Tracker**: Percentage of profitable trades
- **Position Analyzer**: Open vs. closed positions
- **Summary Generator**: Real-time statistics updates

### Data Flow

```
User Action → Validation → Trade Store → FIFO Pairing → 
Render Update → Auto-save → localStorage + Cookie
```

### Key Algorithms

#### FIFO Pairing Algorithm
```
For each SELL trade (chronologically):
  1. Find all BUY trades of same ticker before SELL date
  2. Sort BUYs by date (oldest first)
  3. For each BUY with remaining shares:
     a. Calculate shares to pair (min of SELL remaining, BUY remaining)
     b. Create pairing record with share count
     c. Decrement remaining shares on both trades
  4. If SELL has remaining shares → create "Magic" pairing
```

#### P&L Calculation
```
For each pairing:
  P&L = (Sell Price - Buy Price) × Shares Paired
  P&L % = (P&L / (Buy Price × Shares Paired)) × 100
```

### Features Architecture

#### Feature 1: Auto-fill SELL
- **Trigger**: Click button on available shares bar
- **Action**: Pre-populate form with BUY details
- **UX**: Smooth scroll + focus on price field
- **Benefit**: Reduces data entry errors and time

#### Feature 2: Collapsible Pairings
- **Trigger**: Click on pairing summary bar
- **State**: Toggle between collapsed/expanded
- **Animation**: Smooth rotation of arrow icon
- **Benefit**: Clean UI for complex positions

#### Feature 3: Split Trade Display
- **Detection**: SELL shares > single BUY shares
- **Display**: Show under multiple BUY parents
- **Indicator**: "[X of Y total]" label + warning
- **Benefit**: Clear visualization of complex scenarios

#### Feature 4: Magic Share Tracking
- **Detection**: SELL without sufficient BUY
- **Display**: Virtual "Magic BUY" at $0
- **Color**: Purple theme for distinction
- **Benefit**: Tracks short positions or errors

#### Feature 5: Real-time Summary
- **Update**: On every trade add/edit/delete
- **Metrics**: Total trades, pairs, win rate, P&L
- **Display**: Grid layout with color-coded values
- **Benefit**: Instant performance feedback

## 📖 User Stories: Interface & Journaling

### Adding Trades

**Story 1: Creating a New BUY Position**
```
As a trader,
I want to record a new BUY trade,
So that I can track when I opened a position.

Steps:
1. I fill in ticker "MSTU"
2. I select "BUY" from dropdown
3. I enter 100 shares at $52.00
4. I pick today's date
5. I add note "Bull Rocket - BTC rallying"
6. I click "Add Trade"
7. System creates new BUY entry with ID #1
8. Trade appears in journal grouped by ticker
```

**Story 2: Recording a SELL with Auto-fill**
```
As a trader with an open position,
I want to quickly record a sell,
So that I can close my position efficiently.

Steps:
1. I see "📦 Available: 100 shares" under my BUY
2. I click "⚡ Auto-fill SELL"
3. Form scrolls into view with pre-filled data
4. Price field is highlighted and ready
5. I type "55.12" for the sell price
6. I press Enter or click "Add Trade"
7. System creates SELL and pairs it via FIFO
8. SELL appears as child under the BUY
9. P&L shows +$312 (+6%)
10. Available shares updates to 0
```

**Story 3: Adding Notes for Trade Rationale**
```
As a reflective trader,
I want to document why I made a trade,
So that I can learn from my decisions later.

Steps:
1. I'm filling out a trade form
2. I click in the "Notes" field
3. I type "ATM completion announced - dilution overhang removed"
4. I submit the trade
5. Note appears under the trade in italic gray text
6. When I review later, I remember my reasoning
```

### Viewing & Navigating

**Story 4: Exploring Collapsed Pairings**
```
As a trader with multiple sells,
I want to see a summary without clutter,
So that I can quickly scan my positions.

Steps:
1. I see my BUY with "🔗 5 Pairings (FIFO) Total P&L: -$7,250"
2. Bar is collapsed showing only summary
3. I click the collapsed bar
4. Arrow rotates from ▶ to ▼
5. All 5 SELL children expand with full details
6. Each shows individual P&L and date
7. I can click again to collapse
```

**Story 5: Understanding Split Trades**
```
As a trader who sold more than one position,
I want to see how my large sell was distributed,
So that I understand my cost basis.

Steps:
1. I sold 150 shares but had two 100-share buys
2. First BUY shows "SELL #3 (100 shares) [100 of 150 total]"
3. Warning shows "⚠️ This SELL spans multiple BUYs"
4. Second BUY shows "SELL #3 (50 shares) [50 of 150 total]"
5. Each shows accurate P&L for that portion
6. I understand the split clearly
```

**Story 6: Checking Available Shares**
```
As a trader managing positions,
I want to know how many shares I can still sell,
So that I don't over-sell my position.

Steps:
1. I look at my BUY entry
2. After all SELL children, I see "📦 Available: 80 shares"
3. Green color indicates shares available
4. Text says "(Can sell up to 80 more)"
5. I know exactly what's available
```

### Editing & Managing

**Story 7: Correcting a Trade Error**
```
As a trader who made a data entry mistake,
I want to edit a trade,
So that my records are accurate.

Steps:
1. I notice I entered 100 shares instead of 150
2. I click the "✏️ Edit" button on the trade
3. Prompt appears with current value "100"
4. I change it to "150"
5. I confirm each field (ticker, price, date, notes)
6. System re-pairs all trades automatically
7. Updated values appear immediately
8. P&L recalculates correctly
```

**Story 8: Deleting an Accidental Trade**
```
As a trader who entered a duplicate,
I want to delete a trade,
So that my journal is clean.

Steps:
1. I see a duplicate SELL entry
2. I click the "🗑️ Delete" button
3. Confirmation dialog asks "Delete this trade?"
4. I click OK
5. Trade is removed from journal
6. System automatically re-pairs remaining trades
7. Summary statistics update
8. Available shares recalculate
```

**Story 9: Deleting a SELL Child**
```
As a trader reviewing a child SELL,
I want to delete just that sell,
So that I can correct my position.

Steps:
1. I expand a BUY's children
2. I see a SELL I want to remove
3. I click "🗑️" on that specific SELL child
4. Confirmation appears
5. I confirm deletion
6. SELL is removed
7. Available shares increase
8. Parent BUY remains intact
```

### Data Management

**Story 10: Backing Up My Journal**
```
As a cautious trader,
I want to export my trades,
So that I have a backup.

Steps:
1. I click "📥 Download JSON"
2. File downloads as "paper-trades-2025-10-01.json"
3. File contains all my trades with metadata
4. I save it to my backup folder
5. I feel secure knowing I have a backup
```

**Story 11: Restoring from Backup**
```
As a trader who switched computers,
I want to import my previous trades,
So that I can continue my journal.

Steps:
1. I click "📤 Upload JSON"
2. File picker opens
3. I select my backup file
4. Warning asks "This will replace your current trades"
5. I confirm
6. All trades load successfully
7. Message shows "Successfully imported 32 trades!"
8. My journal is restored
```

**Story 12: Starting Fresh**
```
As a trader starting a new strategy,
I want to clear all trades,
So that I can start with a clean slate.

Steps:
1. I click "🗑️ Clear All"
2. Warning asks "Delete ALL trades? This cannot be undone!"
3. I confirm
4. All trades are removed
5. Journal shows "No trades yet"
6. Summary shows zeros
7. I'm ready to start fresh
```

### Learning & Analysis

**Story 13: Loading Demo Data**
```
As a new user,
I want to see example trades,
So that I can understand how the app works.

Steps:
1. I click "🎮 Demo Data"
2. Warning asks about replacing current trades
3. I confirm
4. 32 realistic trades load
5. I see various scenarios (wins, losses, splits)
6. I explore the interface with real examples
7. Message confirms "Demo data loaded!"
```

**Story 14: Reviewing Win Rate**
```
As a trader analyzing performance,
I want to see my success rate,
So that I can evaluate my strategy.

Steps:
1. I scroll to Portfolio Summary
2. I see "Win Rate: 66.7% (8W / 4L)"
3. I see "Total P&L: +$1,245"
4. Green color indicates overall profit
5. I understand my performance at a glance
```

**Story 15: Understanding Magic Shares**
```
As a trader who sold without buying,
I want to see this tracked,
So that I know I have a short position.

Steps:
1. I entered a SELL without a prior BUY
2. System creates "✨ MAGIC BUY ∞ shares @ $0.00"
3. My SELL appears under Magic BUY
4. Purple color distinguishes it
5. Shows "Revenue" instead of P&L
6. I understand this is a special case
```

### Position Management

**Story 16: Scaling Out of a Position**
```
As a trader taking partial profits,
I want to sell portions of my position,
So that I can manage risk.

Steps:
1. I have BUY of 150 shares
2. I click "⚡ Auto-fill SELL" 
3. I change shares from 150 to 50
4. I enter sell price and submit
5. SELL appears as child with 50 shares
6. Available updates to "100 shares"
7. I can repeat for more partial sells
8. Each SELL tracks separately
```

**Story 17: Viewing Position History**
```
As a trader reviewing a stock,
I want to see all my trades for that ticker,
So that I can understand my history.

Steps:
1. I scroll to the ticker section (e.g., "📈 MSTR")
2. All BUY entries are listed chronologically
3. Each BUY shows its SELL children
4. I see the full position lifecycle
5. Available shares shown for open positions
6. I understand my complete trading history
```

**Story 18: Tracking Multiple Tickers**
```
As a diversified trader,
I want to see each ticker separately,
So that I can track different positions.

Steps:
1. Journal groups trades by ticker
2. I see sections for MSTU, MSTR, TSLL, IBIT
3. Each section shows only that ticker's trades
4. Sections are alphabetically sorted
5. I can focus on one ticker at a time
6. Summary aggregates across all tickers
```

### Advanced Scenarios

**Story 19: Handling a Large Sell Across Multiple Buys**
```
As a trader closing a scaled position,
I want to sell more than my largest buy,
So that I can exit completely.

Steps:
1. I have BUY #1 (100 shares) and BUY #2 (100 shares)
2. I create SELL of 150 shares
3. System automatically splits the sell
4. BUY #1 shows "SELL #3 (100 shares) [100 of 150 total]"
5. BUY #2 shows "SELL #3 (50 shares) [50 of 150 total]"
6. Each shows its own P&L calculation
7. Warning indicates split trade
8. I understand the FIFO distribution
```

**Story 20: Monitoring Real-time Updates**
```
As an active trader,
I want immediate feedback on changes,
So that I can see results instantly.

Steps:
1. I add a new trade
2. Journal updates immediately (no page refresh)
3. Summary statistics recalculate
4. Available shares update
5. P&L colors change if needed
6. Everything stays in sync
7. I can continue trading without interruption
```

## 🛠️ Technical Details

### Technology Stack

- **Pure HTML/CSS/JavaScript** - No frameworks required
- **localStorage** - Primary data storage
- **Cookies** - Backup storage (365-day expiration)
- **JSON** - Import/export format

### Data Structure

```javascript
{
  "trades": [
    {
      "id": 1,
      "ticker": "MSTU",
      "action": "BUY",
      "shares": 100,
      "price": 52.00,
      "date": "2025-10-01",
      "notes": "Bull Rocket scenario",
      "pairedWith": [
        { "id": 2, "shares": 100 }
      ],
      "remainingShares": 0
    }
  ],
  "counter": 3,
  "exportDate": "2025-10-01T18:00:00.000Z",
  "version": "1.0"
}
```

### Browser Compatibility

- Chrome/Edge (recommended)
- Firefox
- Safari
- Any modern browser with ES6 support

## 📝 License

MIT License - See LICENSE file for details

Copyright (c) 2025 ubermicrouser

## 🤝 Contributing

This is an educational project. Feel free to:

- Fork and modify for your own learning
- Share with others interested in trading education
- Suggest improvements via issues

## 📚 References

The educational content includes citations from:

- GraniteShares
- Fidelity Investments
- Direxion
- SEC EDGAR
- Federal Reserve Economic Data (FRED)
- And more...

## 🎯 Use Cases

### For Beginners

- Learn what leveraged ETFs are
- Understand FIFO accounting
- Practice position management
- Build trading discipline

### For Intermediate Traders

- Test new strategies risk-free
- Track paper trades before going live
- Analyze win/loss patterns
- Refine entry/exit timing

### For Educators

- Teaching tool for finance classes
- Demonstrate leveraged ETF mechanics
- Show real-world trading scenarios
- Interactive learning experience

## 🔮 Future Enhancements

Potential additions (not yet implemented):

- Real-time price integration
- Charts and visualizations
- Multiple portfolios
- Performance analytics
- Export to CSV
- Mobile-responsive improvements

## 💡 Tips for Best Use

1. **Start with Demo Data** to understand the interface
2. **Document your reasoning** in the notes field
3. **Review your trades** regularly to learn from mistakes
4. **Export regularly** to backup your data
5. **Use realistic prices** to simulate actual market conditions
6. **Practice discipline** as if it were real money

## 🆘 Support

For questions or issues:

1. Review this README thoroughly
2. Check the educational content in the app
3. Examine the demo data for examples
4. Remember: This is for educational purposes only

## 🎉 Acknowledgments

- Inspired by ABET accreditation standards for educational outcomes
- Autumn theme for cozy learning environment
- Built with focus on user experience and education

---

**Remember**: This is a thought exercise and learning tool. Always consult with qualified financial advisors before making real investment decisions. Past performance (even in simulations) does not guarantee future results.

Happy Paper Trading! 🍁📊
