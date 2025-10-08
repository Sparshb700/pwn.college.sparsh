
# BRATCHA

## Problem
In the problem, this captcha image was provided from through which you were supposed to go to the provided link and obtain the flag.  
![BRATCHA.jpg]
## My Solve

**Flag** : `citadel{1m_3v3rywh3r3_1m_s0_jul1a}`

It was apparent that in the second half of the image, each character has two placeholders.
So, as the name suggested I created a `python` script that brute forced its way through all the possible combinations of the link.

```python
import requests
import itertools

positions = [
    ['s','c'],
    ['g','q'],
    ['x','y'],
    ['h','n'],
    ['x','v'],
    ['B','D'],
    ['h','n'],
    ['Z','S']
]

combinations = [''.join(p) for p in itertools.product(*positions)]

url_template = "https://pastebin.com/{}"

for code in combinations:
    url = url_template.format(code)
    try:
        response = requests.get(url, timeout=5)
        if response.status_code != 404:
            print(f"[FOUND] {url} (Status code: {response.status_code})")
        else:
            print(f"[NOT FOUND] {url}")
    except requests.RequestException as e:
        print(f"[ERROR] {url} ({e})")

```

This program continued to execute until I didn't get a `404` error while pinging to a link.

```
...
[NOT FOUND] https://pastebin.com/sqxhvDnZ
[NOT FOUND] https://pastebin.com/sqxhvDnS
[FOUND] https://pastebin.com/sqxnxBhZ (Status code: 200)
[NOT FOUND] https://pastebin.com/sqxnxBhS
[NOT FOUND] https://pastebin.com/sqxnxBnZ
...
```
After a lot of iterations, I was able to get a status code of `200` and found the link which prompted me to the correct link where I found a text file with the following content;
```
Congrats!

You've proven you're human.

Here's your flag:

citadel{1m_3v3rywh3r3_1m_s0_jul1a}
```

## References
The problem statement provided was the reference used.

# The Sound of Music

## Problem
The problem situated us to search the web for a user `citadweller`'s music journey. And through that, find the flag.

## My Solve
**Flag**: `citadel{c0mputers_st0pped_exchang1ng_1nf0rmat10n_n_started_shar1ng_st0r1es_n_then_they_were_n0where_t0_be_f0und}`

1. First I frantically searched for various music platforms, searched `citadweller` on spotify but couldn't find anything there.
2. Then I tried locating his profile on `last.fm`, and by using the link `https://www.last.fm/user/citadweller`, I was able to open his profile on `last.fm`. 
![Pasted image 20251008131306.png]
3. Scrolling down to the comments, I was able to locate the first part of the flag which was `citadel{c0mputers_st0pped_exchang1ng_1nf0rmat10n`.
4. Then I searched `citadweller` on google and in the filters, I selected the `verbatim` setting. And I was able to locate the `rateyourmusic` profile of `citadwller` where the middle part of the flag was located which was `_n_started_shar1ng_st0r1es_`
![Pasted image 20251008131233.png]
5.  In there, I was able to locate a tinyurl link `https://tinyurl.com/citadweller` which prompted to his spotify account. A playlist named `OSINT pt2`'s description led to the last flag which was _n_then_they_were_n0where_t0_be_f0und}
![Pasted image 20251008131600.png]

## References
The problem statement provided was the reference used.
