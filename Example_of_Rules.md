## Example of Rules:

### A SQLite Parsing Example:

When augmenting the grammar file of an adaptive parser, our approach encompasses not only the incorporation of dialect-specific elements but also the introduction of both terminal and non-terminal symbols. We employ an error recovery mechanism that identifies the topmost rule in the parse stack that failed to parse correctly. It's important to note that while the rule itself fails, some of its sub-rules may successfully parse. Consequently, when we add productions to our grammar, we might also introduce new non-terminal symbols.

Take, for example, the query `SELECT ALL ( c3 = 1 )::int  AS countt FROM v2` ;. The phrase IS NOT represents a dialect-specific construct unique to SQLite. The parsing tree for this query is illustrated in the provided diagram.

SQLess begins by identifying the node where the parsing failed, which is the fromClause in this instance. As observed, the subtree tableSources beneath fromClause is a non-terminal. The rule added to achieve this was:

```
fromClause : FROM tableSources WHERE ID IS NOT decimalLiteral
```

<p align="center">
  <img src="https://github.com/SQLess/Examples/assets/153704279/1a39f5c1-21a0-4418-a950-5fc5d022c337" width="50%" />
</p>



Some rules added by the adaptive parser in the SQLRight dataset for SQLite are as follows:

```
root : sqlStatements? (MINUS MINUS)? EOF
root : sqlStatements UNION VALUES LR_BRACKET timestampValue RR_BRACKET emptyStatement_
root : sqlStatements RETURNING limitClauseAtom COMMA userAuthOption LR_BRACKET limitClauseAtom RR_BRACKET emptyStatement_
root : sqlStatements RETURNING userAuthOption COMMA LR_BRACKET privilege userAuthOption FROM userAuthOption WHERE userAuthOption dottedId EQUAL_SYMBOL userAuthOption dottedId RR_BRACKET AS limitClauseAtom emptyStatement_
root : sqlStatements RETURNING userAuthOption COMMA userAuthOption COMMA userAuthOption COMMA userAuthOption emptyStatement_
root : sqlStatements RETURNING STAR emptyStatement_
root : sqlStatements RETURNING gtuidSet COMMA userAuthOption COMMA userAuthOption emptyStatement_
root : sqlStatements FROM userAuthOption WHERE userAuthOption dottedId EQUAL_SYMBOL userAuthOption dottedId RETURNING userAuthOption dottedId emptyStatement_
root : sqlStatements userAuthOption VALUES LR_BRACKET timestampValue RR_BRACKET VALUES LR_BRACKET timestampValue RR_BRACKET COMMA LR_BRACKET timestampValue RR_BRACKET COMMA LR_BRACKET timestampValue RR_BRACKET userAuthOption VALUES LR_BRACKET timestampValue RR_BRACKET COMMA LR_BRACKET timestampValue RR_BRACKET emptyStatement_
root : sqlStatements UNION showProfileType privilege timestampValue LIMIT timestampValue emptyStatement_
root : sqlStatements FROM userAuthOption WHERE userAuthOption dottedId EQUAL_SYMBOL userAuthOption dottedId RETURNING STAR COMMA gtuidSet emptyStatement_
root : sqlStatements RETURNING userAuthOption dottedId emptyStatement_
root : sqlStatements WHERE userAuthOption EQUAL_SYMBOL timestampValue emptyStatement_
sqlStatements : (sqlStatement ((MINUS MINUS)? SEMI)? | emptyStatement_)
querySpecification : SELECT selectElements filterClause fromClause
filterClause : FILTER '(' fromClause ')'
... ...
```





### A PostgreSQL Parsing Example：

The query `SELECT ALL ( c3 = 1 )::int  AS countt FROM v2 ;` contains PostgreSQL dialect. In the context of adapting an SQL parser to handle PostgreSQL-specific syntax, we encountered a scenario where the parser needed to support a query featuring a type cast to an integer. This is a common pattern in PostgreSQL, where expressions can be cast to specific types using the `::` syntax.

To accommodate this syntax, we proposed an extension to the existing grammar rules of the adaptive parser. The goal was to ensure that the parser could recognize and correctly interpret the type cast operation within the SELECT clause. The rule added to achieve this was:

```sql
querySpecification: SELECT selectSpec selectElement COLON_SYMB COLON_SYMB dataType AS ID fromClause
```

Some rules added by the adaptive parser in the SQLRight dataset for PostgreSQL are as follows:

```
root: sqlStatements IP_ADDRESS userAuthOption emptyStatement_
root: sqlStatements WHERE userAuthOption LESS_SYMBOL timestampValue emptyStatement_
root: SINGLE_QUOTE_SYMB routineOption emptyStatement_
root: sqlStatements BIT_OR_OP BIT_OR_OP userAuthOption BIT_OR_OP BIT_OR_OP gtuidSet emptyStatement_
root: sqlStatements RETURN userAuthOption emptyStatement_
root: sqlStatements MINUS timestampValue emptyStatement_
querySpecification: SELECT selectElements fromClause gtuidSet gtuidSet
querySpecification: SELECT selectSpec selectElement COLON_SYMB COLON_SYMB dataType AS ID fromClause
querySpecification: privilege defaultValue COLON_SYMB COLON_SYMB userAuthOption
selectStatement: querySpecification BETWEEN timestampValue logicalOperator timestampValue
fullColumnName: privilegeLevel
expressionAtom: left=expressionAtom jsonOperator right=expressionAtom 
```



