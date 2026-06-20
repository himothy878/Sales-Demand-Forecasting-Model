# Sales Forecast Summary: Superstore 2018 Projection

## What the forecast means

A Random Forest model was trained on four years of historical order data (2014 to 2017)
to predict monthly sales. The model projects **$843,268 in total sales for 2018**, an
increase of roughly 15% over 2017's actual total of $733,215. This continues the steady
year-over-year growth already present in the historical data: $381,504 (2014), $470,533
(2015), $609,206 (2016), and $733,215 (2017).

The forecast also reflects a clear seasonal pattern that recurs every year in the data.
January and February are consistently the weakest months, with February typically the
lowest point in the calendar. Sales then build steadily from July onward, peaking in the
September to November window, with November historically the strongest month of all. The
2018 forecast follows this same shape: projected sales rise from around $57,000 to
$59,000 in the early months, reach a peak of roughly $96,600 in November, and dip
slightly in December.

This pattern is not an artifact of the model. It reflects a genuine, recurring buying
trend present in all four years of historical data.

It is worth noting that the model's test-period error (MAPE) sits at around 23.5%, which
is fairly wide. Monthly sales in this dataset are naturally volatile, with order volume
fluctuating considerably from month to month. For this reason, the forecast is best
treated as directional, useful for understanding the overall growth trend and the timing
of seasonal demand, rather than as a precise prediction for any single month.

## How a business can use it for planning

**Inventory.** Stock levels should be increased ahead of the third and fourth quarters,
particularly in the run-up to September through November, to avoid stockouts during the
busiest period of the year. Inventory in January and February can be kept leaner, which
frees up cash that would otherwise sit unsold on shelves.

**Cash flow.** With revenue projected to be roughly three times higher in November than
in February, working capital should be planned accordingly. Building cash reserves
through the slower first quarter would help fund inventory purchases ahead of the autumn
peak, rather than assuming revenue stays flat across the year.

**Staffing.** Temporary or seasonal staff should be brought on from around July, with
further increases through September to November, then scaled back in December and
January once the peak has passed.

**Growth planning.** Because the model treats time as a continuous trend rather than
simply repeating last year's pattern, it captures the business's underlying growth
trajectory in addition to seasonality. This makes it a more reasonable basis for
budgeting or hiring decisions than a model that assumes 2018 will look identical to 2017.

## A modeling note worth flagging

An earlier version of this model used calendar month (1 to 12) as a raw category. With
four years of history available, this allowed the model to rely almost entirely on "what
month is it" (accounting for 67.7% of its decision weight) while giving very little
weight to the year-over-year growth trend. As a result, that version actually forecast
2018 sales lower than 2017's real total, despite four consecutive years of growth, which
did not make business sense.

This was corrected by replacing raw month with a continuous time index (months elapsed
since the start of the dataset), along with a smoother, cyclical encoding of
month-of-year using sine and cosine transformations. The corrected model balances trend
and seasonality more evenly, and produces a 2018 forecast that is consistent with the
business's actual growth pattern.
