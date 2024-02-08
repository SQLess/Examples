## More details of datasets

#### Supplementary Data Explanation for AvgC and AvgA

The datasets derived from PINOLO and SQLRight tools have been meticulously analyzed, yielding detailed statistics that shed light on the complexity and structure of the SQL queries within. Specifically, the **AvgC** (Average Clauses) and **AvgA** (Average Aliases) metrics offer insights into the intricacies of the queries.

![image](https://github.com/SQLess/Examples/assets/153704279/66d4dd6a-39e3-4a7e-95ed-1274d14a4221)


**AvgC (Average Clauses)**

- For the **PINOLO Dataset**, the average number of Clauses per query stands at **16.38**. This metric underlines the complexity of the queries in terms of their structural components, such as WHERE, JOIN conditions, and other clause types.The **SQLRight Dataset** presents a significantly lower average of **4.04** Clauses per query, indicating a less complex structure in comparison to the PINOLO Dataset.

**AvgA (Average Aliases)**

- Within the **PINOLO Dataset**, there is an average of **19.76** Aliases per query. Conversely, the **SQLRight Dataset** shows an average of only **3.82** Aliases per query, suggesting a simpler and more straightforward query structure.

The presence of a higher average number of Clauses and Aliases in the PINOLO Dataset compared to the SQLRight Dataset suggests that PINOLO is capable of generating more complex queries. This complexity is not merely in terms of length, but also in the depth of nesting and the use of SQL constructs, which could potentially lead to more intricate scenarios for testing and benchmarking SQL query processors.

These datasets are rich in variety, incorporating numerous clause types such as `filterClause`, `fromClause`, `groupByClause`, `havingClause`, `windowClause`, `orderByClause`, and `limitClause`, among others. The detailed experimental data, which will be provided in the revised paper, will further elaborate on these aspects.





```
# Based on the provided table, we will calculate the averages for AvgC and AvgA for both PINOLO and SQLRight datasets.

# Data from the table
pinolo_data = {
    'MySQL': {'ALLN': 8934, 'AvgT': 185.2, 'MaxT': 538, 'AvgC': 17.95, 'AvgA': 21.03},
    'MariaDB': {'ALLN': 18507, 'AvgT': 152.2, 'MaxT': 517, 'AvgC': 15.36, 'AvgA': 18.96},
    'Oceanbase': {'ALLN': 1777, 'AvgT': 190.5, 'MaxT': 464, 'AvgC': 19.10, 'AvgA': 22.50},
    'TiDB': {'ALLN': 3523, 'AvgT': 165.6, 'MaxT': 490, 'AvgC': 16.43, 'AvgA': 19.34}
}

sqlright_data = {
    'PostgreSQL': {'ALLN': 35, 'AvgT': 42.9, 'MaxT': 128, 'AvgC': 4.08, 'AvgA': 2.00},
    'SQLite': {'ALLN': 143, 'AvgT': 48.7, 'MaxT': 153, 'AvgC': 4.03, 'AvgA': 4.27}
}

# Calculate the weighted averages for AvgC and AvgA for PINOLO dataset
pinolo_weighted_avgC = sum([data['AvgC'] * data['ALLN'] for data in pinolo_data.values()]) / sum([data['ALLN'] for data in pinolo_data.values()])
pinolo_weighted_avgA = sum([data['AvgA'] * data['ALLN'] for data in pinolo_data.values()]) / sum([data['ALLN'] for data in pinolo_data.values()])

# Calculate the weighted averages for AvgC and AvgA for SQLRight dataset
sqlright_weighted_avgC = sum([data['AvgC'] * data['ALLN'] for data in sqlright_data.values()]) / sum([data['ALLN'] for data in sqlright_data.values()])
sqlright_weighted_avgA = sum([data['AvgA'] * data['ALLN'] for data in sqlright_data.values()]) / sum([data['ALLN'] for data in sqlright_data.values()])

pinolo_weighted_avgC, pinolo_weighted_avgA, sqlright_weighted_avgC, sqlright_weighted_avgA
```

