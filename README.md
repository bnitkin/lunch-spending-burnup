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

Text on top is kinda work-in-progress. Right now it's checking and
credit card balances, and net cash (the difference)

## Usage
This little visualizer is a single HTML file and
has no dependencies (other than Lunch Money).
You'll need to generate an API key to use it.

Either go to https://nitkin.net/lunch/chart.html#<API KEY>
(the anchor tag isn't sent to the server, so only Lunch Money sees your key)

Or download the file and open it in your favorite browser. Something like
file:///home/username/chart.html#<API KEY>

