#### Supplementary Data Explanation for AvgC and AvgA

The datasets derived from PINOLO and SQLRight tools have been meticulously analyzed, yielding detailed statistics that shed light on the complexity and structure of the SQL queries within. Specifically, the **AvgC** (Average Clauses) and **AvgA** (Average Aliases) metrics offer insights into the intricacies of the queries.

![image](https://github.com/SQLess/Examples/assets/153704279/b8e96879-ca64-4e59-b4f8-556f2cb4a6bf)


**AvgC (Average Clauses)**

- For the **PINOLO Dataset**, the average number of Clauses per query stands at **16.38**. This metric underlines the complexity of the queries in terms of their structural components, such as WHERE, JOIN conditions, and other clause types.The **SQLRight Dataset** presents a significantly lower average of **4.04** Clauses per query, indicating a less complex structure in comparison to the PINOLO Dataset.

**AvgA (Average Aliases)**

- Within the **PINOLO Dataset**, there is an average of **19.76** Aliases per query. Conversely, the **SQLRight Dataset** shows an average of only **3.82** Aliases per query, suggesting a simpler and more straightforward query structure.

The presence of a higher average number of Clauses and Aliases in the PINOLO Dataset compared to the SQLRight Dataset suggests that PINOLO is capable of generating more complex queries. This complexity is not merely in terms of length, but also in the depth of nesting and the use of SQL constructs, which could potentially lead to more intricate scenarios for testing and benchmarking SQL query processors.

These datasets are rich in variety, incorporating numerous clause types such as `filterClause`, `fromClause`, `groupByClause`, `havingClause`, `windowClause`, `orderByClause`, and `limitClause`, among others. The detailed experimental data, which will be provided in the revised paper, will further elaborate on these aspects.

