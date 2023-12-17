# Implement a phone directory

#### Problem Statement:
You are given a list/array of strings which denotes the contacts that exist in your phone directory. The search query on a string 'str' which is a query string displays all the contacts which are present in the given directory with the prefix as 'str'. One special property of the search function is that when a user searches for a contact from the contact list then suggestions (contacts with prefix as the string entered so for) are shown after the user enters each character.

#### Note:
If no suggestions are found, return an empty 2D array.

#### For Example:

<img width="294" alt="image" src="https://github.com/Abhishekkumar200/DSA-questions/assets/84954320/5ea548dc-14b0-4ff3-997f-49ae55377aa4">

In the above example everytime we enter a character, a few suggestions display the strings which contain the entered string as prefixes.

#### Constraints:

* `1 <= T <= 50`

* `1 <= N <= 100`

* `1 <= len <= 10`

ARR[i] contains lowercase English alphabets.

All the given strings contain lowercase English alphabets.

Time Limit: 1 sec.

#### Sample Input 1:

2

5

cod coding codding code coly

coding

2

ninias coding

ninja

#### Sample Output 1:

cod coding codding code coly

