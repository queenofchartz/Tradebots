# Multi-Session Breakout Strategy - Changes Documentation

## Overview
This enhanced version of your trading strategy now includes:
1. **Multi-session trading**: Asia, London, and New York sessions
2. **Automatic closure at entry price**: Exits trades when price returns to entry level
3. **Session visualization**: Background colors to identify active sessions

## Key Changes Made

### 1. Multi-Session Support
- **Asia Session**: 00:00 - 09:00 UTC (Tokyo time)
- **London Session**: 08:00 - 17:00 UTC
- **New York Session**: 13:00 - 22:00 UTC

Each session can be enabled/disabled independently through input settings:
- `Trade Asia Session`
- `Trade London Session`
- `Trade New York Session`

### 2. Session-Based Breakout Logic
- The strategy now captures the first 15-minute candle of EACH session
- Trades breakouts from each session's first candle high/low
- Maintains separate high/low levels for each session
- Only trades during active sessions

### 3. Automatic Closure at Entry Price
New feature that automatically closes positions when price returns to entry:
- **Long positions**: Close when price drops to entry + buffer
- **Short positions**: Close when price rises to entry - buffer
- Configurable entry buffer in pips (default: 0.1 pips)
- Can be enabled/disabled via `Auto Close at Entry Price` input

### 4. Visual Enhancements
- **Session backgrounds**: 
  - Yellow for Asia session
  - Blue for London session
  - Green for New York session
- **Entry price line**: Blue cross marks showing your entry level
- **Session levels**: Green/red lines showing session high/low

### 5. Session Time Considerations
The strategy uses UTC times by default. You may need to adjust these based on:
- Your broker's server time
- Daylight saving time changes
- Your preferred trading hours

To adjust session times, modify these variables in the code:
```pinescript
// Asia Session
asia_start_hour = 0
asia_end_hour = 9

// London Session
london_start_hour = 8
london_end_hour = 17

// New York Session
ny_start_hour = 13
ny_end_hour = 22
```

## Usage Tips

### 1. Session Selection
- Start by testing one session at a time to understand its behavior
- Asian session tends to have lower volatility
- London session often has good momentum
- NY session can have strong trends

### 2. Risk Management
- The strategy maintains the 6 trades per day limit across ALL sessions
- Each session's breakout is independent
- Consider adjusting position size based on session volatility

### 3. Entry Close Feature
- The auto-close at entry helps protect against losses
- Adjust the buffer based on spread and volatility
- Can act as a breakeven stop

### 4. Optimization Suggestions
- Test different TP multipliers for each session
- Consider tighter stops during low volatility sessions
- Adjust trailing stop activation based on session characteristics

## Performance Considerations
- More trading opportunities across three sessions
- Potential for both increased profits and losses
- Important to backtest thoroughly with your specific pairs
- Consider correlation between sessions (London/NY overlap)

## Next Steps
1. Backtest the strategy on your preferred currency pairs
2. Adjust session times for your timezone/broker
3. Fine-tune risk parameters for each session
4. Consider adding session-specific parameters (different TP/SL per session)