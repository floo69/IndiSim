# PRD: Indian Stock Paper Trading Simulator

## 1) Product Summary

**App:** An Indian stock paper trading simulator where users practice investing in NSE/BSE stocks using virtual money, track their portfolio, and review trade history without risking real capital.

**Target user:** Beginner retail investors in India, especially college students and first-time stock market learners who want to practice buying and selling Indian stocks before trading with real money.

---

## 2) Problem Statement

New investors in India often want to learn how stock trading works, but they hesitate to use real money because they do not understand order flow, portfolio impact, profit/loss tracking, or market volatility. Existing learning tools are often U.S.-focused or too complex.

This app solves that by providing a simple, India-focused, virtual trading environment.

---

## 3) Product Goals

1. Help users learn stock trading basics safely.
2. Let users simulate Indian stock trades using virtual cash.
3. Show portfolio performance clearly and simply.
4. Make the product fast, intuitive, and good enough to demo as a portfolio project.

---

## 4) Success Metrics

* User can complete signup and first trade in under 3 minutes.
* User can buy and sell a stock without errors.
* Portfolio updates correctly after every trade.
* Trade history is accurate and readable.
* Users can understand their current P&L at a glance.

---

## 5) Core V1 Scope

### High Priority

* Sign up / login / logout
* Virtual wallet with starting cash
* Search Indian stocks
* View stock detail page with live or near-live price
* Buy stock
* Sell stock
* Portfolio dashboard
* Holdings list
* Transaction history
* Profit / loss tracking
* Basic validation for quantity and cash balance
* Mobile-responsive UI

### Medium Priority

* Watchlist
* Price chart for selected stock
* Search suggestions/autocomplete
* Filter holdings by gain/loss
* Sort portfolio by value or return
* Basic notifications for trade success/failure
* Dark mode

### Low Priority

* Leaderboard
* Competitions
* Achievements / badges
* News feed
* Advanced analytics
* Dividend simulation
* Stock split / bonus share simulation
* Options/F&O
* Social sharing

---

## 6) Feature List by Priority

### High Priority

#### Authentication

* Email/password signup
* Login/logout
* Session persistence
* Password reset later, not required in V1

#### Virtual Wallet

* Every new user starts with a fixed virtual balance
* Balance updates after each trade
* Display available cash prominently

#### Stock Search

* Search by company name or symbol
* Indian stocks only
* Show matching results with symbol and current price

#### Stock Detail Page

* Show stock name, symbol, latest price, daily change, and basic chart or price snapshot
* Show buy/sell controls

#### Buy Stock

* User enters quantity
* App calculates total cost
* Check if sufficient cash is available
* Confirm purchase
* Update holdings, balance, and transaction history

#### Sell Stock

* User enters quantity
* App checks user holdings
* Confirm sale
* Update holdings, balance, and transaction history

#### Portfolio Dashboard

* Show current cash
* Show total invested amount
* Show current portfolio value
* Show total profit/loss
* Show list of holdings

#### Trade History

* Show all buy and sell transactions
* Include date, stock, quantity, price, and total value

#### Validation and Error Handling

* Cannot buy without enough cash
* Cannot sell more than owned
* Cannot trade invalid quantity
* Clear error messages

---

### Medium Priority

#### Watchlist

* Save favorite stocks
* Quick access from dashboard

#### Charts

* Basic price chart for stock detail page
* Daily / weekly / monthly view

#### Sorting and Filtering

* Sort holdings by value, gain/loss, alphabetically
* Filter by gainers and losers

#### Search Enhancements

* Auto-suggest stock names and symbols
* Recent searches

#### UI Quality Improvements

* Dark mode
* Loading skeletons
* Empty states
* Toast notifications

#### Basic Alerts

* Notify after successful trade
* Notify when trade fails

---

### Low Priority

#### Leaderboard

* Compare performance across users
* Only useful if the product becomes multiplayer

#### Achievements

* First trade
* First profit
* 10 trades completed

#### Competitions

* Weekly trading contests
* Top return leaderboard

#### Social / Sharing

* Share portfolio result image
* Share trading achievements

#### Advanced Market Simulation

* Dividend payouts
* Bonus issues
* Stock splits
* Corporate actions

#### News

* Market news and stock-specific updates

---

## 7) User Flows

### Flow 1: Sign Up

1. User opens app.
2. User clicks “Sign Up”.
3. User enters email, password, and name.
4. App validates input.
5. Account is created.
6. User receives starting virtual cash.
7. User lands on dashboard.

**Success state:** User is authenticated and can start trading immediately.

---

### Flow 2: Login

1. User opens app.
2. User clicks “Login”.
3. User enters email and password.
4. App verifies credentials.
5. User is redirected to dashboard.

**Failure state:** Show clear error if credentials are wrong.

---

### Flow 3: Search Stock

1. User types company name or symbol.
2. App shows matching Indian stocks.
3. User selects one result.
4. App opens stock detail page.

**Success state:** User can reach the trade screen in one or two clicks.

---

### Flow 4: Buy Stock

1. User opens a stock detail page.
2. User enters quantity.
3. App shows estimated total cost.
4. User clicks “Buy”.
5. App checks cash balance.
6. If valid, trade is executed.
7. Cash balance decreases.
8. Holdings and transaction history update.
9. Success message appears.

**Error state:** If cash is insufficient, show a clear message and prevent the trade.

---

### Flow 5: Sell Stock

1. User opens a stock detail page or holdings card.
2. User enters quantity to sell.
3. App checks owned quantity.
4. User clicks “Sell”.
5. If valid, trade is executed.
6. Cash balance increases.
7. Holdings and transaction history update.
8. Success message appears.

**Error state:** If user tries to sell more than owned, block the action.

---

### Flow 6: View Portfolio

1. User opens dashboard.
2. App shows available cash.
3. App shows holdings and each holding’s current value.
4. App calculates portfolio value and total profit/loss.
5. User can click into any stock for more details.

---

### Flow 7: Review Trade History

1. User opens “Transactions”.
2. App shows recent buy/sell records.
3. User can scroll through history.
4. User can see date, symbol, quantity, price, and total.

---

## 8) Data Model Overview

### User

* id
* name
* email
* password_hash
* virtual_cash_balance
* created_at

### Holding

* id
* user_id
* stock_symbol
* stock_name
* quantity
* average_buy_price
* updated_at

### Transaction

* id
* user_id
* stock_symbol
* transaction_type (`BUY` / `SELL`)
* quantity
* price_per_share
* total_value
* timestamp

### Stock

* symbol
* company_name
* last_price
* change_percent
* updated_at

---

## 9) Visual Style Direction

### Overall Look

Clean, modern, fintech-style, simple enough for beginners.

### Visual Principles

* Minimal clutter
* High readability
* Strong hierarchy for cash, portfolio value, and P&L
* Cards and clean spacing
* Responsive layout for mobile and desktop

### Color Direction

* Neutral base background
* One accent color for primary actions
* Green for gains
* Red for losses
* Avoid overly flashy gradients

### Typography

* Use a modern sans-serif font
* Large, bold numbers for balance and portfolio value
* Clear labels and compact metadata

### Components

* Stock cards
* Portfolio summary cards
* Transaction table
* Search bar with results dropdown
* Buy/Sell modal or side panel
* Small charts for price movement

### Tone

* Trustworthy
* Simple
* Financially clean
* Beginner-friendly

---

## 10) What to Exclude from V1

Do not build these in V1:

* Real-money trading
* Brokerage integration
* KYC
* UPI / bank payments
* Options/F&O
* Margin trading
* News feed
* Social feed
* Leaderboard
* Competitions
* Corporate actions simulation
* Dividend simulation
* Real-time streaming charts
* Advanced analytics dashboard
* Multi-language support
* Referral system
* Push notifications
* Admin panel unless absolutely needed

---

## 11) Acceptance Criteria for the 3 Most Important Features

### Feature 1: Signup/Login

**Acceptance Criteria**

* User can create an account with valid email and password.
* User can log in and remain logged in after refresh.
* User sees a dashboard after successful login.
* Invalid credentials show a helpful error message.
* New user receives the default virtual balance automatically.

---

### Feature 2: Buy/Sell Trading

**Acceptance Criteria**

* User can buy an Indian stock only if sufficient virtual cash is available.
* User can sell only up to the quantity they own.
* After a successful buy, cash balance decreases correctly and holdings increase correctly.
* After a successful sell, cash balance increases correctly and holdings decrease correctly.
* Every successful trade is saved to transaction history.
* Failed trades do not change balance or holdings.

---

### Feature 3: Portfolio Dashboard

**Acceptance Criteria**

* Dashboard shows current cash balance.
* Dashboard shows all holdings with quantity, average buy price, current price, and current value.
* Dashboard calculates total portfolio value correctly.
* Dashboard calculates total profit/loss correctly.
* Dashboard updates after each trade without requiring manual refresh.
* Empty portfolio state is shown clearly for new users.

---

## 12) Non-Functional Requirements

### Performance

* Main dashboard should load quickly.
* Search should feel responsive.
* Trade execution should complete immediately after validation.

### Reliability

* Trades must be atomic from the user’s perspective.
* No duplicate transaction records.
* Portfolio numbers must remain consistent.

### Usability

* First-time users should understand the app without onboarding complexity.
* Trade actions should be obvious and safe.

### Security

* Store passwords securely.
* Protect authenticated routes.
* Prevent unauthorized access to trade history and holdings.

### Scalability

* V1 can be simple, but the structure should allow future expansion to more users and more stock data.

---

## 13) Future Enhancements

* Watchlist
* Price alerts
* Charts
* Competitions
* Leaderboard
* Achievements
* Market news
* Dividend simulation
* Admin moderation tools
* Advanced reporting

---

## 14) Final V1 Definition

A successful V1 is a web app where a user can:

1. Sign up and log in
2. Receive virtual Indian trading capital
3. Search a stock
4. Buy and sell it
5. See accurate portfolio and transaction updates

That is enough to be useful, demo-worthy, and expandable later.
