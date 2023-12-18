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

coding

2

ninias coding

ninja

#### Sample Output 1:

cod coding codding code coly

cod coding codding code coly

cod coding codding code coly

coding

coding

coding

ninjas

ninjas

ninjas

ninjas

ninjas

#### Explanation To Sample Input 1:

In the first test case,

The suggestions for "c" is {"cod", "coding", "codding", "code", "coly"}.

The suggestions for "co" is {"cod", "coding", "codding", "code", "coly"}.

The suggestions for "cod" is {"cod", "coding", "codding", "code", "coly").

The suggestion for "codi" is {"coding").

The suggestion for "codin" is {"coding"}.

The suggestion for "coding" is {"coding"}.

In the second test case,

The suggestion for "n" is ["ninjas"}.

The suggestion for "ni" is {"ninjas").

The suggestion for "nin" is ("ninjas").

The suggestion for "ninj" is {"ninjas").

The suggestion for "ninja" is {"ninjas").

#### Code:

```C++

class trieNode
{
    public:
    char data;
    bool terminal;
    trieNode *children[26];
    trieNode(char data)
    {
        this->data = data;
        terminal = false;
        for(int i=0;i<26;i++)
        {
            children[i] = NULL;
        }
    }
};
class trie
{
    public:
    trieNode *root;
    trie(char ch)
    {
        root = new trieNode(ch);
    }
    void insertWord(trieNode *root, string word)
    {
        if(word.length()==0)
        {
            root->terminal = true;
            return;
        }
        int index = word[0]-'a';
        trieNode *child;
        if(root->children[index]!=NULL)
        {
            child = root->children[index];
        }
        else
        {
            child = new trieNode(word[0]);
            root->children[index] = child;
        }
        insertWord(child, word.substr(1));
    }
    void insert(string word)
    {
        trieNode *temp = root;
        insertWord(temp, word);
    }
    void printSuggestion(trieNode *current, vector<string> &temp, string prefix)
    {
        if(current->terminal)
        {
            temp.push_back(prefix);
            // return;
        }
        for(char ch='a';ch<='z';ch++)
        {
            trieNode *next = current->children[ch-'a'];
            if(next != NULL)
            {
                prefix+=ch;
                printSuggestion(next, temp, prefix);
                prefix.pop_back();
            }
        }
    }
    vector<vector<string>> phone(string query)
    {
        vector<vector<string>> ans;
        string prefix = "";
        trieNode *prev = root;
        for(int i=0;i<query.size();i++)
        {
            char last = query[i];
            prefix+=last;
            int index = query[i]-'a';
            trieNode *current = prev->children[index];
            if(current==NULL)
            {
                break;
            }
            vector<string>temp;
            printSuggestion(current, temp, prefix);
            ans.push_back(temp);
            temp.clear();
            prev = current;
        }
        return ans;
    }    
};
vector<vector<string>> phoneDirectory(vector<string>&contactList, string &queryStr)
{
    //    Write your code here.
    trie *root = new trie('\0');
    int n = contactList.size();
    for(int i=0;i<n;i++)
    {
        root->insert(contactList[i]);
    }
    return root->phone(queryStr);
}

```
