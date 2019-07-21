#### https://www.youtube.com/watch?v=E87XhgYBM-Y

# Bootiful TDD By Josh Long

- Desire to stay in the zone / dopamine / video games 
- In order to take advantage of this fast movement, you need safety
- We want validation that everytime we introduce a change
- We want to move quickly and safely to production, early and often

## Bob Martins 3 laws of TDD
1. You are not allowed to write any production code unless it is to make a failing unit test pass.
2. You are not allowed to write any more of a unit test than is sufficient to fail; and compilation failures are failures.
3. You are not allowed to write any more production code than is sufficient to pass the one failing unit test.


## The goal: Optimize for fast feedback

- Stay perpetually in the zone
- We want to enjoy that sense that we're continously moving forward
- That desire to constantly have feedback

## When you write your tests first:

- You write code that can be tested


## Steps

- Create the test
- Instantiate a class that doesnt exist
- Create the non-existant class ( Auto generate here )
- Instantiate example classes and use Matcher ( BaseMatcher ) 22:27

## Write an Entity Test next

- Prove that the mapping is correct
- Prove that I can talk to the DB
- Prove that I can make queries and the id is not null
-

## Write an [Class]HTTPTest

- Inject the WebTestClient
- WebTestClient expects certain responses and statuses
