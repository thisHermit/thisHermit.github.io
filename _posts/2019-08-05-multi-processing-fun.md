---
layout: post
title: "Multi processing fun"
date: 2019-08-05
---

Last week on Saturday, we got a project to make a multi-threaded program
to find the word count of all words in all the files giving in a directory.

First I created 8 files as the source. The code for that:
```python
import random


def main():
    s = [
        "the", "of", "that", "this",
        "at", "a", "to", "in", "is",
        "you", "be", "it", "he", "she",
        "have", "from", "or", "for",
        "one", "had", "by", "word",
        "but", "there", "use", "an",
        "each", "which", "she", "do",
        "how", "their", "if", "will",
        "some", "her", "would", "make",
        "like", "him", "into", "time",
        "has", "look", "two"
        ]

    for i in range(7):
        with open('file00' + str(i) + '.txt', 'w') as f:
            no_lines = int(random.gauss(10, 3))
            for j in range(no_lines):
                f.write(' '.join([random.choice(s) for k in range(int(random.gauss(20, 3)))]))
                f.write('\n')


if __name__ == '__main__':
    main()

```

The words' set is selected from the most common English words from this website
[here](https://www.rypeapp.com/most-common-english-words/).

The actual code to find the word count

```python
from multiprocessing import Process, Manager


def word_counter(words_freq: dict, file):
    for line in file:
        words = line.split()
        for word in words:
            if word in words_freq:
                words_freq[word] += 1
            else:
                words_freq[word] = 1


def main():
    print("Program starts...")

    print("Getting list of files...")
    # maybe implement this properly next time
    files = ['file00' + str(i) + '.txt' for i in range(8)]
    print("Done!")

    with Manager() as manager:
        words_dictionary = manager.dict()
        for file in files:
            p = Process(target=word_counter, args=(words_dictionary, open(file)))
        p.start()
        p.join()
        print(words_dictionary)

    print("Exiting Main Program")


if __name__ == '__main__':
    main()

```

To count the words, I first create a shared dictionary and pass all the instances
of the worker the same dictionary. The worker here is simply a function running
in a separate Process. Imagine many small children coloring the same picture.

At the last, the program waits for all the workers to stop.
