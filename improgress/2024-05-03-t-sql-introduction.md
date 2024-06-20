---
layout: single
title: "Relational Database Management System Introduction: From Mathematics to Relations"
header:
categories:
  - Databases
author_profile: True
---
# Developed About SQL 
Invented in the ealry 1970's by IBM called SEQUEL (strucut English quary Language) which provided a relation dabase manager system. This was then changed from SEQUEL to SQL due to trademark issues. 

People often rever to SQL was a American national standard istitude and Itnernation organisation for stadnardisation (ISO) standard laguage for relational model for manging/querying Relationsl dabase manager systems.

# What is a relational database?
Relantional models was invented by mathematicians who studies set theory and predicate logic.

Set theory is the study or collection of objectives. An exmaples lets S = {a,b,c}, where S is the set and the objetive are contained within the set (a,b,c). 
According to Georg Cantor, the discovery of set theory,  a set has a few main proeprties.

1. a set is a single entity - we should look at sets over individuals objects. 
2. eact elemtn is distinct - a set cant contains two of the same elements {a,a,b,c} is not a set 
3. sets are subjective - how a set is created is depdende on the person 
4. order of elements in a set doesnt matter - {a,b,c} = {b,c,a}

All of which was utilised in relational databases architecture 

1. When we do quries on on SQL we focus on say a whole colums (gender of table) over indviduals people (1 person gender)
2. defining key contraints
3. Relational database systems can be designed  depending on the applciation required. So data is not represented uniquely.
4. We dont care how a indviduals sits in a table but rather if it is containe din a table. 

Predicate logic is a branch of methamtcis which basically studies true or false statement. Relationals models relies on constrained to maing logic for queries. An exmaples given a salary, salary > 20,000. 

Set theory and predicate logic is linked by being able to define sets through predicate logic, since sets can have a infinte amount of elements. An example "x is a postive number thats is divible by 2" whicich {2,4,6,8,10...}.

# Initail mdoels of Relational Models

The intials models as invented in 1969 by IBM reseach reported valled "Derivbaility, Reudcndancy and COnsistency of rtleational stored Lsarge Data bnkas". 

A RDBMS implements a relational models to allows stroage, management, enforcement and query of data. In the paper the authors identfied proeprties of RDBS including propsotions,predicates,rleations,tuplaes and attributes.

# What is a proposition,predicates and relation?

Relational does not meaing relation between table, but rather 'relation' in set theory. which means a set of relation information.
So in a relational model a relation is a table which conatasins relational information.

When creating a relation you start of with a proposition/statement of truth or false. Given a relation (table) of Cars which includes car brand, car number, car type, year of manufacturting then a proposition is "The toyota supra is a 2-door sport car made in 2024". Then we cosider this prospotion to our relations. If true then we write it into our relation, in this case yes! Else we if its false prospotion then we dont right it, known as clsoe world asusmption.So what we have done is placing a predicate on a proposition.

(picture)

Next we take the data out of proposition if true through predicates. 

## how can we put predicate on prposition?
One was it puting type constraints, thats is the value of a attritube it either 'char, int, string' and length constrains.

Finally we place it into our relation by inseting it into a  set of tuples(row), under the corresponding set og attribtues (columns)

# Role of keys and Normilisation 

We have a problem John recently chnages his number we want to now chnage his number in our relation. How would we do this? Say we qeyr but we find there are 3 johns but we only want index 100 john. 

This process mathematically is called normalisation which guarenties a single relation for each relation, ensugin (1) minimisation of reducancy and (2) avoiding Anaomilies. 

# Type of Normisliations, correposbonding to key relationships
## 1-Normlisation
## 2-Normlsiation
## 3 normilisation 

candidate keys, doreign keys, altenrate keys, non key 