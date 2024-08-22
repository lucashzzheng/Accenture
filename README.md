# Accenture
 Intership Program（Case study)
## Ask 

The client is Social Buzz. This report aims to figure out the top 5 categories with the largest popularity.

## Prepare

### Dataset selection

There are 7 datasets provided by the client. Our goal is to figure out the top 5 categories with the largest popularity. Hence we need datasets which contains category information and a measure of popularity. From the data model file, Content and ReactionType datasets must be chose. Furthermore, we need a dataset to connect the two datasets which is the Reaction dataset. Hence, Content, Reaction and ReactionType are chose.

## Process

### Deletion of irrelevant columns

Content
- row_num removed
- user_id: we don't care which user gives the reaction in this report so removed.
- url removed

Reaction:
- row_num removed
- user_id: we don't care which user gives the reaction in this report so removed.
- dateframe: we don't care when user gives the reaction in this report so removed.

ReactionType:
- row_num removed
- sentiment: we only care about scoring in this report so removed.

### Merging of three datasets

Note that one content can have more than one reactions, so we should use reaction as left join table.
Reaction left join Content table on Content ID.
Reaction left join ReactionType table on Category.

### Removng Missing Value rows

- remove missing value reactiontype rows: 982 rows deleted. (Note that we only have approximate 25000 rows here, so almost 4% data deleted in this operation. If it is not required by the program, I will do the avearge scoring to replacing the missing value)

### Data Type Consistency

- removed quotation makrs in Category from Content Table.
- make all categories lower case.

24573 rows keep as clean data.

## Analysis

### Calculating top 5 performance Category

Using Sumif we can have the following result by sorting total_score:

Category | Total Socre
---------|------------
animals	| 74965
science	| 71168
healthy eating	| 69339
technology	| 68738
food	| 66676
culture	| 66579
travel	| 64880
cooking	| 64756
soccer	| 57783
education	| 57436
fitness	| 55323
studying	| 54269
dogs	| 52511
tennis	| 50339
veganism	| 49619
public speaking	| 49264
  
