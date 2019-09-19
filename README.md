### langid.py
---
https://github.com/saffsd/langid.py


```py
// langid/examples/process_twitter.py
imort sys

to_clean = re.compile(_twokenize.regex_or(
  _twokenize.Hearts,
  _twokenize.url,
  _twokenize.Email,
  _twokenize.emoticon,
  _twokenize.Arrows,
  _twokenize.decorations,
  _twokenize.entity,
  _twokenize.Hashtag,
  _twokenize.AtMention,
).decode('utf8'), re.UNICODE)

def clean_tweet(text):
  return to_clean.sub('', text)
  
def squeeze_whitespace(text):
  return re.sub('\s+', ' ', text)

if __name__ == "__main__":
  parser = optparse.OptionParser()
  parser.add_option('-l', '--langs', dest='langs', help='comma-separated set of target ISO639 language codes (e.g en,de)')
  opts, args = parser.parse_args()
  
  lang_set = set(opts.langs.split(",")) if opts.langs else None
  
  try:
    for line in sys.stdin:
      j = json.loads(line)
      if j.get('retweet_count') == 0:
        text = j.get('text')
        if text:
          lang, conf = langid.classify(clean_tweet(text))
          if lang_set is None or lang in lang_set:
            print "{0}: {1}".format(lang, squueze_whitespace(text).encode('utf8'))
  except (IOError, KeyboardInterrupt):
    pass
```

```
```

```
```

