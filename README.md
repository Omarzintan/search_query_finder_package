# Python Search Query Finder

General rule-based function that extracts a search query from spoken text given search terms to look out for.

Some possible search terms include `'to', 'on', 'for', 'about'`
```
e.g. 'do a google search on Python.'
    search term = on
    query found = Python
```

This function also ignores false search_term_indicators such as `'like to', 'love to', 'want to'`
```
e.g. 'I want to do a google search on Python'
     false search term = to
     false search term indicator = want
     actual search term = on
     query found = Python
```

  Thus, in the above example, the function will correctly ignore `'do a google search on Python'` as a possible search query and will capture `'Python'` as the right query.

 Other exmaples of use cases:
 ```
'Send an email to Alex'
   search term = to
   query found = Alex
```

```
 Arguments: <string> spoken_text, <list> feature_patterns=[],
            <list> search_terms=['to', 'on', 'for', 'search'], <list> false_search_term_indicators=['like', 'love', 'want', 'ready']
Return type: <string> spoken_text (now stripped down to only the search query.)
```

## Installation
```bash
pip install search_query_finder
```

## Example usage
```python
from search_query_finder import find_query
# You can call the function, passing only the sentence.
query1 = find_query.find_query("do a google search on Python programming.")
# expected result = 'Python programming.'

# You can also call the function, passing the sentence along with the search_terms you would like the function to search for. By default, the search terms are set to be = ['to', 'on', 'for', 'search']
query2 = find_query.find_query("send an email to Alex", search_terms=["to"])
# expected result = 'Alex'

# You can also call the function, passing the sentence along with the false_search_term_indicators you want. By default, these are set to be = ['like', 'love', 'want', 'ready']
query3 = find_query.find_query("I would like to do a google search for the python programming language", false_search_term_indicators=["like"])
# expected result = 'the python programming language'
```

