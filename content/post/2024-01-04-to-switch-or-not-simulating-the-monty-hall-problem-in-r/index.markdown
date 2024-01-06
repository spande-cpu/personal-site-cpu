---
title: To Switch or Not? Simulating the Monty-Hall Problem
author: Shashwat M. Pande
date: '2024-01-04'
slug: to-switch-or-not-simulating-the-monty-hall-problem
categories: [Data Science, Decision Making]
tags: []
subtitle: ''
summary: ''
authors: []
lastmod: '2024-01-04T12:04:59Z'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

The Monty-Hall problem is perhaps one the most well-known examples of a situation when arguments about matters of chance and probability make it into the general public discourse. Initially proposed and solved by Steve Selvin in a letter to the editor of the *The American Statistician*, the problem became known more broadly when the correctness of the perhaps slightly unintuitive solution became the [subject of a bitter public disagreement](https://web.archive.org/web/20130121183432/http://marilynvossavant.com/game-show-problem/) between a famous American columnist and (some of) her more distinguished readers.

Here’s a reproduction of the problem originally posed (and solved) in Selvin’s letter. The set-up can be summarised as follows:

*There is a prize hidden behind 1 of 3 doors. A contestant can select a door at random with a 1/3 chance of winning. Once the selection is made, the eponymous Monty Hall reveals what’s behind one of the remaining doors but the catch is that he must not reveal the winning choice. Now, the contestant must decide – stick to the original selection or switch to the remaining door.* What would you do?

## The Simple Solution

Using enumeration to solve the problem, we could describe the various possibilities in such a game with the decision matrix below. Clearly, the odds of winning when a player switches are 2/3 or about 66.67%.

<div id="nbpuwurazk" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>@import url("https://fonts.googleapis.com/css2?family=Chivo:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
#nbpuwurazk table {
  font-family: Chivo, system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
&#10;#nbpuwurazk thead, #nbpuwurazk tbody, #nbpuwurazk tfoot, #nbpuwurazk tr, #nbpuwurazk td, #nbpuwurazk th {
  border-style: none;
}
&#10;#nbpuwurazk p {
  margin: 0;
  padding: 0;
}
&#10;#nbpuwurazk .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: 300;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: none;
  border-top-width: 3px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}
&#10;#nbpuwurazk .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}
&#10;#nbpuwurazk .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}
&#10;#nbpuwurazk .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}
&#10;#nbpuwurazk .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#nbpuwurazk .gt_bottom_border {
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#nbpuwurazk .gt_col_headings {
  border-top-style: none;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#nbpuwurazk .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}
&#10;#nbpuwurazk .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: normal;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}
&#10;#nbpuwurazk .gt_column_spanner_outer:first-child {
  padding-left: 0;
}
&#10;#nbpuwurazk .gt_column_spanner_outer:last-child {
  padding-right: 0;
}
&#10;#nbpuwurazk .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}
&#10;#nbpuwurazk .gt_spanner_row {
  border-bottom-style: hidden;
}
&#10;#nbpuwurazk .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: none;
  border-top-width: 2px;
  border-top-color: #000000;
  border-bottom-style: solid;
  border-bottom-width: 1px;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}
&#10;#nbpuwurazk .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: none;
  border-top-width: 2px;
  border-top-color: #000000;
  border-bottom-style: solid;
  border-bottom-width: 1px;
  border-bottom-color: #FFFFFF;
  vertical-align: middle;
}
&#10;#nbpuwurazk .gt_from_md > :first-child {
  margin-top: 0;
}
&#10;#nbpuwurazk .gt_from_md > :last-child {
  margin-bottom: 0;
}
&#10;#nbpuwurazk .gt_row {
  padding-top: 3px;
  padding-bottom: 3px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}
&#10;#nbpuwurazk .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 0px;
  border-right-color: #FFFFFF;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#nbpuwurazk .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}
&#10;#nbpuwurazk .gt_row_group_first td {
  border-top-width: 2px;
}
&#10;#nbpuwurazk .gt_row_group_first th {
  border-top-width: 2px;
}
&#10;#nbpuwurazk .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#nbpuwurazk .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}
&#10;#nbpuwurazk .gt_first_summary_row.thick {
  border-top-width: 2px;
}
&#10;#nbpuwurazk .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#nbpuwurazk .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#nbpuwurazk .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}
&#10;#nbpuwurazk .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}
&#10;#nbpuwurazk .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}
&#10;#nbpuwurazk .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#nbpuwurazk .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#nbpuwurazk .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#nbpuwurazk .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#nbpuwurazk .gt_sourcenote {
  font-size: 12px;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#nbpuwurazk .gt_left {
  text-align: left;
}
&#10;#nbpuwurazk .gt_center {
  text-align: center;
}
&#10;#nbpuwurazk .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}
&#10;#nbpuwurazk .gt_font_normal {
  font-weight: normal;
}
&#10;#nbpuwurazk .gt_font_bold {
  font-weight: bold;
}
&#10;#nbpuwurazk .gt_font_italic {
  font-style: italic;
}
&#10;#nbpuwurazk .gt_super {
  font-size: 65%;
}
&#10;#nbpuwurazk .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}
&#10;#nbpuwurazk .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}
&#10;#nbpuwurazk .gt_indent_1 {
  text-indent: 5px;
}
&#10;#nbpuwurazk .gt_indent_2 {
  text-indent: 10px;
}
&#10;#nbpuwurazk .gt_indent_3 {
  text-indent: 15px;
}
&#10;#nbpuwurazk .gt_indent_4 {
  text-indent: 20px;
}
&#10;#nbpuwurazk .gt_indent_5 {
  text-indent: 25px;
}
&#10;tbody tr:last-child {
  border-bottom: 2px solid #ffffff00;
}
</style>
<table class="gt_table" data-quarto-disable-processing="false" data-quarto-bootstrap="false">
  <thead>
    &#10;    <tr class="gt_col_headings">
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" style="border-top-width: 0px; border-top-style: solid; border-top-color: black;" scope="col" id="Prize Behind">Prize Behind</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" style="border-top-width: 0px; border-top-style: solid; border-top-color: black;" scope="col" id="Player Chooses">Player Chooses</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" style="border-top-width: 0px; border-top-style: solid; border-top-color: black;" scope="col" id="Monty Reveals">Monty Reveals</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" style="border-top-width: 0px; border-top-style: solid; border-top-color: black;" scope="col" id="Player Switches">Player Switches</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" style="border-top-width: 0px; border-top-style: solid; border-top-color: black;" scope="col" id="Outcome">Outcome</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="Prize Behind" class="gt_row gt_left">Door A</td>
<td headers="Player Chooses" class="gt_row gt_left">Door A</td>
<td headers="Monty Reveals" class="gt_row gt_left">Door B or C</td>
<td headers="Player Switches" class="gt_row gt_left">A -&gt; B or C</td>
<td headers="Outcome" class="gt_row gt_left">Loser</td></tr>
    <tr><td headers="Prize Behind" class="gt_row gt_left">Door A</td>
<td headers="Player Chooses" class="gt_row gt_left">Door B</td>
<td headers="Monty Reveals" class="gt_row gt_left">Door C</td>
<td headers="Player Switches" class="gt_row gt_left">B -&gt; A</td>
<td headers="Outcome" class="gt_row gt_left">Winner</td></tr>
    <tr><td headers="Prize Behind" class="gt_row gt_left">Door A</td>
<td headers="Player Chooses" class="gt_row gt_left">Door C</td>
<td headers="Monty Reveals" class="gt_row gt_left">Door B</td>
<td headers="Player Switches" class="gt_row gt_left">C -&gt; A</td>
<td headers="Outcome" class="gt_row gt_left">Winner</td></tr>
    <tr><td headers="Prize Behind" class="gt_row gt_left">Door B</td>
<td headers="Player Chooses" class="gt_row gt_left">Door A</td>
<td headers="Monty Reveals" class="gt_row gt_left">Door C</td>
<td headers="Player Switches" class="gt_row gt_left">A -&gt; B</td>
<td headers="Outcome" class="gt_row gt_left">Winner</td></tr>
    <tr><td headers="Prize Behind" class="gt_row gt_left">Door B</td>
<td headers="Player Chooses" class="gt_row gt_left">Door B</td>
<td headers="Monty Reveals" class="gt_row gt_left">Door A or C</td>
<td headers="Player Switches" class="gt_row gt_left">B -&gt; A or C</td>
<td headers="Outcome" class="gt_row gt_left">Loser</td></tr>
    <tr><td headers="Prize Behind" class="gt_row gt_left">Door B</td>
<td headers="Player Chooses" class="gt_row gt_left">Door C</td>
<td headers="Monty Reveals" class="gt_row gt_left">Door A</td>
<td headers="Player Switches" class="gt_row gt_left">C -&gt; B</td>
<td headers="Outcome" class="gt_row gt_left">Winner</td></tr>
    <tr><td headers="Prize Behind" class="gt_row gt_left">Door C</td>
<td headers="Player Chooses" class="gt_row gt_left">Door A</td>
<td headers="Monty Reveals" class="gt_row gt_left">Door B</td>
<td headers="Player Switches" class="gt_row gt_left">A -&gt; C</td>
<td headers="Outcome" class="gt_row gt_left">Winner</td></tr>
    <tr><td headers="Prize Behind" class="gt_row gt_left">Door C</td>
<td headers="Player Chooses" class="gt_row gt_left">Door B</td>
<td headers="Monty Reveals" class="gt_row gt_left">Door A</td>
<td headers="Player Switches" class="gt_row gt_left">B -&gt; C</td>
<td headers="Outcome" class="gt_row gt_left">Winner</td></tr>
    <tr><td headers="Prize Behind" class="gt_row gt_left">Door C</td>
<td headers="Player Chooses" class="gt_row gt_left">Door C</td>
<td headers="Monty Reveals" class="gt_row gt_left">Door A or B</td>
<td headers="Player Switches" class="gt_row gt_left">C -&gt; A or B</td>
<td headers="Outcome" class="gt_row gt_left">Loser</td></tr>
  </tbody>
  &#10;  
</table>
</div>

## Simulating the Problem with some R Code

Simulating this problem is a fun way to understand how functions and loops work in `R` and can be a good way for students to grasp concepts around simulating probabilistic scenarios.

``` r
# Define f() to simulate n runs of the Monty-Hall problem given our strategy
monty_hall <- function(strategy = "switch", n = 100) {
  
  # Initialise doors and wins
  doors <- 1:3
  wins <- 0
  
  for (i in 1:n) {
    
    # Winning door
    winning_door <- floor(runif(1, 1, 4))
    # Initial guess
    my_guess <- floor(runif(1, 1, 4))
    
    # Monty reveals a losing door
    monty_opens <- ifelse(
      winning_door == my_guess,
      sample(doors[-c(winning_door)]),
      doors[-c(winning_door, my_guess)]
    )
    
    # Final Player Selection
    my_selection <- if(strategy == "stick") {
      my_guess
    } else if(strategy == "switch") {
      doors[-c(my_guess, monty_opens)]
    } else if(strategy %in% c("", "random", "both")) {
      sample(c(doors[-c(my_guess, monty_opens)], my_guess), 1)
    } else {
      print("Please select a valid strategy.")
    }
    
    outcome <- ifelse(winning_door == my_selection, "Winner", "Loser")
    wins <- ifelse(outcome == "Winner", wins+1, wins)
    losses <- n-wins
    win_rate = wins / n
    
  }
  
  # A tibble to store outomes
  tidyr::tibble(strategy, trials = n, wins, losses, win_rate)
  
}
```

We can now use our function to generate data for any `n` under different strategies. Let’s plot the results from our simulation and see which strategy wins in the long-run.

``` r
# Generate Monty Hall Data
library(ggplot2)
out <- tidyr::tibble()
for (i in 1:1000) {
  out <- dplyr::bind_rows(
    out, do.call(
      rbind, lapply(c("switch", "stick", "random"), function(x) monty_hall(x, n = i))
    ) 
  )
}
ggplot(aes(trials, win_rate), data = out) + 
  geom_line(aes(col = strategy)) +
  scale_y_continuous(label = scales::percent_format()) +
  ggtitle("No. of Games v/s Win-Rate") +
  xlab("Number of Times the Game is Played") +
  ylab("% of Games Where Player Wins") +
  theme_bw() 
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-3-1.png" width="672" />

Hmm…it would seem that we have a winner! Try working with the code on your own machine and messing with some parameters. What happens to the odds when we change the number of doors to 4 or more?
