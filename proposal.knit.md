---
title: "The Power of Voters" 
subtitle: "Proposal"
format: 
  html: 
   embed-resources: true
   code-fold: true
toc: true
editor: visual
execute:
  echo: false
  warning: false
---

::: {.cell}

:::


## Dataset

#### US House Election Results


::: {.cell}

:::


| Variable         | Description                                                                               |
|-------------------|-----------------------------------------------------|
| `year`           | Year in which election was held.                                                          |
| `state_po`       | State name.                                                                               |
| `party`          | Party of the candidate.                                                                   |
| `candidate`      | Name of the candidate as it appears in the House Clerk report.                            |
| `candidatevotes` | No. of votes the candidate received.                                                      |
| `fusion ticket`  | Same Candidate will receive votes from multiple party.                                    |
| `district`       | District number in state                                                                  |
| `runoff`         | Second election held to determine a winner                                                |
| `special`        | Special Election.                                                                         |
| `totalvotes`     | Total Votes in District                                                                   |
| `Writein`        | Candidate name does not appear on the ballot and must be physically written in by voters. |

**Preview of dataset**


::: {.cell}
::: {.cell-output .cell-output-stdout}

```
# A tibble: 5 × 11
   year state_po party    candidate candidatevotes fusion_ticket district runoff
  <dbl> <chr>    <chr>    <chr>              <dbl> <lgl>         <chr>    <lgl> 
1  1976 AL       DEMOCRAT BILL DAV…          58906 FALSE         001      FALSE 
2  1976 AK       REPUBLI… DON YOUNG          83722 FALSE         000      FALSE 
3  1976 CA       DEMOCRAT ROBERT L…          75844 FALSE         004      FALSE 
4  1976 FL       DEMOCRAT GABRIEL …          80821 FALSE         006      FALSE 
5  1976 HI       REPUBLI… FREDERIC…          53745 FALSE         001      FALSE 
# ℹ 3 more variables: special <lgl>, totalvotes <dbl>, writein <lgl>
```


:::
:::

::: {.cell}

:::


**About the dataset**

The dataset, [US House Election Results](https://github.com/rfordatascience/tidytuesday/tree/master/data/2023/2023-11-07) sourced from MIT Election Data and Science Lab (MEDSL), offers a comprehensive overview of US House elections.

This dataset contains observations for elections held over 47 years from 1976 to 2022, encompassing a total of 32,452 recorded events. Each event is represented as a row with 20 attributes as columns. These columns provide details including the year, state, district, political party, candidate's name, votes received, and various indicators such as whether it was a runoff election or if it was a write-in candidate.

**Reason for choosing dataset**

The US House Election dataset offers a rich and comprehensive source of data, encompassing multiple variables such as election years, state information, candidate details, and voting outcomes. This abundance of data provides ample opportunities for rigorous analysis and exploration within the scope of the academic project.

## Questions

Question 1: How did US voting trends change in the 2016-2020 presidential term?

Question 2: How is the type of voting influenced by population and how does that influence who looses?

## Analysis plan

**For Question 1:**

*Variables Involved:*

-   **`state_po`**: The two-letter postal abbreviation for the state.

-   **`party`**: The political party of the candidate.

-   **`year`**: Year of the election, focusing on the most recent general election or a specific year of interest.

-   **`candidatevotes`**: The number of votes the candidate received.

Analysis Approach:

1.  **Filter Data**: Data selection from the general elections (**`stage`** variable) for the most recent year or a specific year of interest.The analysis focuses on data from the general elections (stage variable) for the most recent year or a specific year of interest within the 2016-2020 presidential term. This data includes information such as the two-letter postal abbreviation for each state (state_po), the political party of the candidate (party), the year of the election (year), and the number of votes each candidate received (candidatevotes).

2.  **Determine Winners**: For each state, the analysis identifies the party with the highest aggregate candidate votes in the general election. This involves summing up the candidate votes for each party within each state and selecting the party with the highest total votes as the winner for that state.

3.  **Visualization**: Create a map of the USA, coloring each state based on the winning party. This visualization provides a clear depiction of the political landscape across the states for the selected election year, highlighting which party won each state.

**For Question 2:**

*Variables Involved:*

-   **`district`**: The congressional district number.

-   **`fusion ticket`** : allowing candidate to receive votes from multiple party.

-   **`runoff`** : second election held to determine a winner

-   **`special`** : Special election

-   **`party`**: The political party of the candidate.

-   **`year`**: Year of the election, focusing on the most recent general election or a specific year of interest.

-   **`candidatevotes`**: The number of votes the candidate received.

-   **`candidate`**: Name of candidate

-   **`totalvotes`**: Total Votes in District

*Variables to be Created:*

-   **`population`**: This will require merging external data containing population

***Analysis Approach:***

1.  **Merge External Data**: The first step involves incorporating population data from a reliable source, such as the U.S. Census Bureau. This additional dataset will provide information on the population within each congressional district, which is essential for analyzing the relationship between population and voting type.

2.  **Analyze Voting Type by Population**: Examine the relationship between population and the type of voting, using statistical analysis .how the type of voting (e.g., fusion ticket, runoff, special elections) varies with population size. This analysis could involve methods such as regression analysis, chi-square tests, or other appropriate statistical techniques to identify any significant relationships or patterns.

3.  **Correlate with Election Outcomes**: Focusing on which party tends to loose with certain characteristics.the next step is to assess how these factors correlate with election outcomes. Specifically, the focus will be on understanding which party tends to lose under certain conditions.

***Visualization and Reporting:***

-   Use scatter plots or heat maps to show the relationship between population and mode of voting.

-   Create comparative visualizations to illustrate how these factors influence election outcomes, potentially using bar charts and pie chart

