---
title:  "Best age to buy an annuity"
date:   2024-09-23 22:22:00 +0100
tags: annuities
layout: single
classes: wide
mortality_chart_js: |
  google.charts.load('current', {'packages':['corechart']});
  google.charts.setOnLoadCallback(drawChart);

  function drawChart() {
    var data = google.visualization.arrayToDataTable([
      ['Age', 'qx'],
      [ 20, 0.000351], [ 21, 0.000357], [ 22, 0.000367], [ 23, 0.000383], [ 24, 0.000401],
      [ 25, 0.000424], [ 26, 0.000450], [ 27, 0.000479], [ 28, 0.000510], [ 29, 0.000544],
      [ 30, 0.000580], [ 31, 0.000617], [ 32, 0.000657], [ 33, 0.000697], [ 34, 0.000742],
      [ 35, 0.000789], [ 36, 0.000842], [ 37, 0.000900], [ 38, 0.000966], [ 39, 0.001039],
      [ 40, 0.001122], [ 41, 0.001215], [ 42, 0.001319], [ 43, 0.001436], [ 44, 0.001566],
      [ 45, 0.001710], [ 46, 0.001870], [ 47, 0.002046], [ 48, 0.002236], [ 49, 0.002443],
      [ 50, 0.002663], [ 51, 0.002895], [ 52, 0.003134], [ 53, 0.003377], [ 54, 0.003618],
      [ 55, 0.003852], [ 56, 0.004070], [ 57, 0.004265], [ 58, 0.004425], [ 59, 0.004534],
      [ 60, 0.004649], [ 61, 0.004852], [ 62, 0.005114], [ 63, 0.005443], [ 64, 0.005850],
      [ 65, 0.006343], [ 66, 0.006930], [ 67, 0.007619], [ 68, 0.008413], [ 69, 0.009318],
      [ 70, 0.010340], [ 71, 0.011489], [ 72, 0.012783], [ 73, 0.014250], [ 74, 0.015930],
      [ 75, 0.017873], [ 76, 0.020144], [ 77, 0.022812], [ 78, 0.025948], [ 79, 0.029620],
      [ 80, 0.033888], [ 81, 0.038807], [ 82, 0.044431], [ 83, 0.050818], [ 84, 0.058034],
      [ 85, 0.066273], [ 86, 0.075679], [ 87, 0.086343], [ 88, 0.098488], [ 89, 0.112353],
      [ 90, 0.128161], [ 91, 0.146104], [ 92, 0.166292], [ 93, 0.188724], [ 94, 0.213232],
      [ 95, 0.239437], [ 96, 0.267737], [ 97, 0.297019], [ 98, 0.326601], [ 99, 0.356076],
      [100, 0.385118], [101, 0.407648], [102, 0.428729], [103, 0.448340], [104, 0.466560],
      [105, 0.479899], [106, 0.489144], [107, 0.498155], [108, 0.506973], [109, 0.515683],
      [110, 0.524402], [111, 0.535959], [112, 0.547229], [113, 0.558218], [114, 0.568932],
      [115, 0.579378], [116, 0.589561], [117, 0.599488], [118, 0.609164], [119, 0.618596],
    ]);

    var formatter = new google.visualization.NumberFormat({ pattern: '#.##%' });
    formatter.format(data, /* column */ 1);

    var options = {
      curveType: 'function',
      legend: { position: 'none' },
      vAxis: { title: 'Mortality rate', format: 'percent' },
      hAxis: { title: 'Age', viewWindow: { min: 40, max: 100 } }
    };

    var chart_div = document.getElementById('mortality_chart');
    var chart = new google.visualization.LineChart(chart_div);

    // https://developers.google.com/chart/interactive/docs/printing
    /*
    google.visualization.events.addListener(chart, 'ready', function () {
      chart_div.innerHTML = '<img src="' + chart.getImageURI() + '">';
    });
    */

    chart.draw(data, options);
  }
---

Surprisingly little advice has been written in the UK on the best age to buy an annuity, perhaps because the annuitisation of defined contribution pots was compulsory until the introduction of _Pension Freedoms_ in 2015, and the low annuity rates resulting from the _Zero Interest Rate Policy_ of the past two decades.

LCP research [^lcp-paper-1] [^lcp-paper-2] suggested that for many people the best time to buy an annuity might be in one's late 70s or early 80s[^this-money-article].
LCP derived this optimal ages through a complex utility maximisation based model and the papers are an excellent reading.

[^lcp-paper-1]: <https://www.lcp.com/en/insights/on-point-paper/is-there-a-right-time-to-buy-an-annuity>
[^lcp-paper-2]: <https://www.lcp.com/en/insights/on-point-paper/the-flex-first-fix-later-pension-is-this-the-future-of-retirement>
[^this-money-article]: <https://www.thisismoney.co.uk/money/pensions/article-12026015/What-best-age-use-220k-pension-buy-annuity.html>

**It's also possible to infer a simpler rule of thumb for the best age to buy an annuity.**

Let's imagine on their $x$-th birthday a retiree opts between one of the following two choices to fund the following year consumption:

1. Buy an immediate index-linked annuity paying $C$ per year, with first payment on the $x+1$ -th birthday.

2. Invest into an asset with average real return rate of $r$ for one year, withdraw $C$ on the $x+1$ -th birthday to fund that year's consumption, and then buy an immediate annuity paying $C$ from the $x+2$ -th birthday.

Both options have a expected yearly consumption of $C$ for as they live, but will not necessarily cost the same.
If $A_x$ is the cost of the annuity at age $x$, then buying annuity now is preferable when

$$ A_x < (C + A_{x+1}) \cdot (1 + r)^{-1} $$

that is, when the cost of the annuity now is less than the cost of the next year withdrawal and an annuity next year, discounted by the investment return rate.

If we price the annuity through its actuarial present value[^apv] it will cost

[^apv]: <https://en.wikipedia.org/wiki/Actuarial_present_value>

$$ A_x = \sum_{t=0}^\infty p_{x,t} \cdot (1 + y_{x,t})^{-t} \cdot C $$

where

- $p_{x,t}$ is the probability of surviving from age $x$ to $x + t$

- $y_{x,t}$ is the real forward gilts rate between the years corresponding to age $x$ and age $x + t$

Consecutive survival probabilities are related to one another through the mortality rate $q_x$

$$ p_{x,t} = (1 - q_x) \cdot p_{x+1,t} $$

and the forward rates according to

$$ y_{x,t + 1} = (1 + y_{x,1}) \cdot (1 + y_{x+1,t})  $$

which in turn means that that $A_x$ and $A_{x+1}$ are related as

$$ A_x = (1 - q_x) \cdot (1 + y_{x,1})^{-1} \cdot (C + A_{x+1}) $$

Substituting this into the earlier inequality we get

$$ (1 - q_x) \cdot (1 + y_{x,1})^{-1} \cdot (C + A_{x+1}) <  (C + A_{x+1}) \cdot (1 + r)^{-1} $$

which can be simplified to

$$ q_x > 1 - \frac{y_{x,1}}{1 + r} $$

If we take the Taylor series[^taylor-series] and ignore all second order products of rates we get

[^taylor-series]: <https://www.wolframalpha.com/input?i=taylor+series+of+1%2F%281%2Bx%29+at+x%3D0>

$$ q_x > r - y_{x,1} $$

**That is, an annuity becomes the cheapest choice when the mortality rate exceeds the difference between the investment return rate and the gilts yield.**

Which makes sense:

- when investing, future consumption can be discounted by the investment return rate;

- whereas with annuities future consumption can be discounted by the gilts yield, _and_ by the mortality credits.

All rates so far should have been the real (inflation adjusted) rates, but because we take the difference of two rates, the relation also holds true with nominal investment returns rates and gilts yield.

And if the investment is equities then it basically means that an annuity becomes cheaper when the mortality rate exceeds the equity risk premium.

We ignored fees, but they won't change things materially.
Mortality rates start with values very near zero for young ages, but then shoot up like an hockey stick later in life.
**There will be age from which mortality rates will dominate everything else: high investment return rates, low gilts yields, and even fees.**

These are the 2024/2025 unisex mortality rates from the Institute and Faculty of Actuaries[^mortality-table]:

[^mortality-table]: <https://www.actuaries.org.uk/learn-and-develop/continuous-mortality-investigation/other-cmi-outputs/unisex-rates-0>

<div id="mortality_chart" style="height: 500px;"></div>

<script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>
<script type="text/javascript">
{{ page.mortality_chart_js }}
</script>

If we assume a 100% equity portfolio on MSCI World Index, currently an annualized 9.64% return since inception[^msci-world], and use the
Latest 15-Year Gilt Yield[^gilt-yields], currently at 4.28%, as the gilts yield, then annuity will become cheaper when mortality rate reaches 5.36%, that is, 83-84 years old.

If we assume a 60%/40% MSCI World/Gilts portfolio instead, then annuity would become cheaper when mortality rate reaches 3.22%, that is, approximately 80 years old.

There is one caveat: the above calculations will not apply for someone in poor health and with a lower life expectancy below their cohort average.

[^msci-world]: <https://www.msci.com/documents/10199/f0e54c85-98b7-40eb-9a7b-bbb03288b523>
[^gilt-yields]: <https://markets.ft.com/data/bonds>
