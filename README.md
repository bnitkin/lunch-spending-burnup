# lunch-spending-burnup
Little widget for Lunch Money that shows current and last-month spending/savings.
It also displays overall balances in savings/checking/credit to provide an idea of
your cash position. Long-term savings like investments are intentionally omitted.

It's inspired by the Rocket Money burn-up graph to show cumulative monthly income
and spending. It's a good way to show a lot of data in a pretty readable format.
(theirs is more polished, but I won't sell your personal data. Or see it.
I don't want your personal data.)

<img alt="widget preview" src="https://github.com/user-attachments/assets/c4cd1a00-06a5-42af-bb75-f2ff44455e42" />

### Usage
First, generate a Lunch Money [API Key](https://my.lunchmoney.app/developers). Then either:
 - go to https://nitkin.net/lunch/netcash.html#API_KEY (use your API key)
 - download `netcash.html` and open it in your favorite browser. Something like
   `file:///home/username/netcash.html#API_KEY` (use your API key)
 - for iOS, use [Glimpse 2](https://apps.apple.com/us/app/glimpse-2/id1524217845) (or similar)
   to view the webpage as a widget. Use a 4h+ refresh interval to not spam the Lunch API.
 - I'm sure there's something similar on Android, but I don't have one to check.

### Configuration
There are a bunch of options you can cinfigure with URL parameters: which trendlines draw,
whether to include future recurring expenses, and other stuff. Parameters are all URL-encoded, i.e.
```
nitkin.net/lunch/netcash.html?income_last=true&expected_transactions=false&safe_spend=4000#API_KEY
```

Unless otherwise noted, fields can be set to `true` or `false`
 - `income`: Default `true`. Shows current-month income
 - `income_last`: Default `false`. Shows prior-month income
 - `expenses`: Default `true`. Shows current-month expenses
 - `expenses_last`: Default `true`. Shows prior-month expenses
 - `fill_last`: Default `true`. Render last-month transactions as filled instead of a line
 - `expected`: Default `true`. Parse and show expected
        recurring transactions for the month. They render on the chart as a dotted line,
        and will also impact `Spent`/`left` math in the top box.
 - `safe_spend`: Numeric. Default `3000`. This provides a reverse budget -
        if you like to calculate savings goals and work backwards to
        a comfortable spending level. It's used to compute the `left` field.

### Key
 - Expenses are red, income is green
 - Last month is shown as a translucent filled-box; this month is a line
 - Pending and expected recurring transactions are displayed as a dotted line
   (pending expenses usually clear quickly, but security holds for cars or hotels can be misleading for budgeting)

The top fields show cash holdings and a [reverse budget](https://lunchmoney.app/blog/pay-yourself-first-reverse-budgeting)
 - Savings: the total balance in savings accounts. The right side
   estimates cash reserve in months, based on last month's spending.
 - Checking: total balance in checking accounts.
 - Cards: total balance on credit cards. `net` shows the difference
   between checking and cards. A positive net means there's
   enough in checking to pay off the cards.
 - Spent: This is total spending for the month. It includes future
   recurring transactions, if they're enabled (see `expected` option).
   The `left` field computes safe spending for the month (`safe_spend - spent`)
   
### Other Features
 - The chart automatically resizes, rounding to the next $500.
 - Options to customize the chart
 - Privacy-first: no third party calls, no complicated libraries.
   It's all plain javascript in a single HTML file.

