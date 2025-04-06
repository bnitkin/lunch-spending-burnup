# lunch-spending-burnup
Little widget for Lunch Money that shows current and last-month spending/savings.

This widget was inspired by the Rocket Money burn-up graph to show cumulative income
and spending, per month. It's a good way to show a lot of data in a pretty readable format.
(theirs is more polished, but I won't sell your personal data. Or see it.)

Past income and expenses are shown as pale green and red lines.

Current month's actual income is dark green; expenses are dark red.

Recurring expenses are used to generate expected future income/expenses,
and are shown as dotted.

The chart automatically resizes, rounding to the next $500.

The top fields show net cash and a very simple budget.
 - Savings: the total balance in savings accounts. The right side
   converts to months of expenses, based on last month's spending.
 - Checking: total balance in checking accounts.
 - Cards: total balance on credit cards. Net shows the difference
   between checking and cards. If you have one checking
   account that all the cards pay from, a positive net means there's
   enough in checking to autopay the cards.
   (plus some margin since credit cards bill for statement-end
   balance, not current)
 - Spent: This is total spending for the month. It includes future
   recurring transactions, if they're enabled (see `expected` below)

## Usage
This little visualizer is a single HTML file and
has no dependencies (other than Lunch Money).
You'll need to generate an API key to use it.

Either go to https://nitkin.net/lunch/chart.html#<API KEY>
(the anchor tag isn't sent to the server, so only Lunch Money sees your key)

Or download the file and open it in your favorite browser. Something like
file:///home/username/chart.html#<API KEY>

## Configuration
The widget is configurable with URL parameters. You can customize which trendlines draw,
and adjust some of the numbers. Parameters are all URL-encoded, i.e.

`netcash.html?income=false&expected_transactions=true&safe_spend=4000#<API KEY>`

 - `income`: `true` or `false`. Default `true`. Shows current-month income
 - `income_last`: `true` or `false`. Default `false`. Shows prior-month income
 - `expenses`: `true` or `false`. Default `true`. Shows current-month expenses
 - `expenses_last`: `true` or `false`. Default `true`. Shows prior-month expenses
 - `expected`: `true` or `false`. Default `true`. Parse and show expected
        recurring transactions for the month. They render on the chart as a dotted line,
        and will also impact `Spent`/`left` math in the top box.
 - `safe_spend`: Numeric. Default `3250`. Safe-spend provides a reverse budget -
        if you like to calculate savings goals and work backwards to
        a comfortable spending level. This field shows how much is left
        for the month after your actual and expected transactions.

