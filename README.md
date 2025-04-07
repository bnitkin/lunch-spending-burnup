# lunch-spending-burnup
Little widget for Lunch Money that shows current and last-month spending/savings.

It's inspired by the Rocket Money burn-up graph to show cumulative monthly income
and spending. It's a good way to show a lot of data in a pretty readable format.
(theirs is more polished, but I won't sell your personal data. Or see it.
I don't want your personal data.)

![widget preview](https://github.com/user-attachments/assets/0def4828-50bf-4389-a84e-d096213f5f0d)

(the top numbers use the Plaid account API, and that doesn't work for Lunch's demo budget)

### Key
 - Past expenses are shown in pale red (last month's income is pale green)
 - Current month's actual income is green; expenses are red.
 - Recurring expenses are used to generate expected future income/expenses,
   and are shown as dotted.

The top fields show cash holdings (synchronized accounts only) and a [reverse budget](https://lunchmoney.app/blog/pay-yourself-first-reverse-budgeting)
 - Savings: the total balance in savings accounts. The right side
   estimates months of expenses, based on last month's spending.
 - Checking: total balance in checking accounts.
 - Cards: total balance on credit cards. Net shows the difference
   between checking and cards. If you have one checking
   account that all the cards pay from, a positive net means there's
   enough in checking to autopay the cards.
 - Spent: This is total spending for the month. It includes future
   recurring transactions, if they're enabled (see `expected` option).
   The `net` field on the right generates remaining spending for the
   month using your `save_spend` and current+recurring spending 
   
### Other Features
 - The chart automatically resizes, rounding to the next $500.
 - Options to customize the chart
 - Privacy-first: no third party calls, no complicated libraries.
   It's all plain javascript in a single HTML file.

### Usage
First, generate a Lunch Money (API Key)[https://my.lunchmoney.app/developers]. Then either:
 - go to https://nitkin.net/lunch/chart.html#API_KEY
 - download `netcash.html` and open it in your favorite browser. Something like
   `file:///home/username/chart.html#API_KEY`
 - for iOS, use (Glimpse 2)[https://apps.apple.com/us/app/glimpse-2/id1524217845] (or similar)
   to view the webpage as a widget. Use a 4h+ refresh interval to not spam the Lunch API.
 - I'm sure there's something similar on Android, but I don't have one to check.

### Configuration
There are a bunch of options you can cinfigure with URL parameters: which trendlines draw,
whether to include future recurring expenses, and other stuff. Parameters are all URL-encoded, i.e.
```
nitkin.net/lunch/netcash.html?income_last=true&expected_transactions=false&safe_spend=4000#API_KEY
```

 - `income`: `true` or `false`. Default `true`. Shows current-month income
 - `income_last`: `true` or `false`. Default `false`. Shows prior-month income
 - `expenses`: `true` or `false`. Default `true`. Shows current-month expenses
 - `expenses_last`: `true` or `false`. Default `true`. Shows prior-month expenses
 - `fill_last`: `true` or `false`. Default `true`. Render last-month transactions as filled instead of a line
 - `expected`: `true` or `false`. Default `true`. Parse and show expected
        recurring transactions for the month. They render on the chart as a dotted line,
        and will also impact `Spent`/`left` math in the top box.
 - `safe_spend`: Numeric. Default `3250`. Safe-spend provides a reverse budget -
        if you like to calculate savings goals and work backwards to
        a comfortable spending level. This field shows how much is left
        for the month after your actual and expected transactions.
