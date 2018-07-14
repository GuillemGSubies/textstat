# textstat 
Python package to calculate statistics from text to determine readability, complexity and grade level of a particular corpus.

## Usage

```python
>>> import textstat

>>> test_data = (
    "Playing games has always been thought to be important to "
    "the development of well-balanced and creative children; "
    "however, what part, if any, they should play in the lives "
    "of adults has never been researched that deeply. I believe "
    "that playing games is every bit as important for adults "
    "as for children. Not only is taking time out to play games "
    "with our children and other adults valuable to building "
    "interpersonal relationships but is also a wonderful way "
    "to release built up tension."
)

>>> textstat.flesch_reading_ease(test_data)
>>> textstat.smog_index(test_data)
>>> textstat.flesch_kincaid_grade(test_data)
>>> textstat.coleman_liau_index(test_data)
>>> textstat.automated_readability_index(test_data)
>>> textstat.dale_chall_readability_score(test_data)
>>> textstat.difficult_words(test_data)
>>> textstat.linsear_write_formula(test_data)
>>> textstat.gunning_fog(test_data)
>>> textstat.text_standard(test_data)
```

The argument (text) for all the defined functions remains the same -
i.e the text for which statistics need to be calculated.

## Install

You can install textstat either via the Python Package Index (PyPI) or from source.

#### Install using pip

```shell
pip install textstat
```

#### Install using easy_install

```shell
easy_install textstat
```

#### Install lastest version from GitHub

```shell
git clone https://github.com/shivam5992/textstat.git
cd textstat
pip install .
```

#### Install from PyPI

Download the latest version of textstat from http://pypi.python.org/pypi/textstat/

You can install it by doing the following:

```shell
tar xfz textstat-*.tar.gz
cd textstat-*/
python setup.py build
python setup.py install # as root
```

## List of Functions

### Syllable Count

```python
textstat.syllable_count(text, lang='en_US')
```

Returns the number of syllables present in the given text.

Uses the Python module [Pyphen](https://github.com/Kozea/Pyphen)
for syllable calculation. Optional `lang` specifies to
Pyphen which language dictionary to use.

Default is `'en_US'`, `'en_GB'` will also work.


### Lexicon Count

```python
textstat.lexicon_count(text, removepunct=True)
```

Calculates the number of words present in the text.
Optional `removepunct` specifies whether we need to take
punctuation symbols into account while counting lexicons.
Default value is `True`, which removes the punctuation
before counting lexicon items.

### Sentence Count

```python
textstat.sentence_count(text)
```

Returns the number of sentences present in the given text.


### The Flesch Reading Ease formula

```python
textstat.flesch_reading_ease(text)
```

Returns the Flesch Reading Ease Score.

The following table can be helpful to assess the ease of
readability in a document.

The table is an _example_ of values. While the
maximum score is 121.22, there is no limit on how low
the score can be. A negative score is valid.

| Score |    Difficulty     |
|-------|-------------------|
|90-100 | Very Easy         |
| 80-89 | Easy              |
| 70-79 | Fairly Easy       |
| 60-69 | Standard          |
| 50-59 | Fairly Difficult  |
| 30-49 | Difficult         |
| 0-29  | Very Confusing    |

> Further reading on [Wikipedia](https://en.wikipedia.org/wiki/Flesch%E2%80%93Kincaid_readability_tests#Flesch_reading_ease)

### The Flesch-Kincaid Grade Level

```python
textstat.flesch_kincaid_grade(text)
```

Returns the grade score using the Flesch-Kincaid Grade Formula.

For example, a score of 9.3 means that a ninth grader would be able to
read the document.

### The Fog Scale (Gunning FOG Formula)

```python
textstat.gunning_fog(text)
```

Returns the FOG index of the given text.

### The SMOG Index

```python
textstat.smog_index(text)
```

Returns the SMOG index of the given text.

### Automated Readability Index

```python
textstat.automated_readability_index(text)
```

Returns the ARI (Automated Readability Index) which outputs
a number that approximates the grade level needed to
comprehend the text.

For example if the ARI is 6.5, then the grade level to comprehend
the text is 6th to 7th grade.

### The Coleman-Liau Index

```python
textstat.coleman_liau_index(text)
```

Returns the grade level of the text using the Coleman-Liau Formula.

### Linsear Write Formula

```python
textstat.linsear_write_formula(text)
```

Returns the grade level using the Linsear Write Formula.

### Dale-Chall Readability Score

```python
textstat.dale_chall_readability_score(text)
```

Different from other tests, since it uses a lookup table
of the most commonly used 3000 English words. Thus it returns
the grade level using the New Dale-Chall Formula.

### Readability Consensus based upon all the above tests

```python
textstat.text_standard(text, float_output=False)
```

Based upon all the above tests, returns the estimated school
grade level required to understand the text.

Optional `float_output` allows the score to be returned as a
`float`. Defaults to `False`.
