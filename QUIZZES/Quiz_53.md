# QUIZ 053
![Screen Shot 2023-04-04 at 22 45 05](https://user-images.githubusercontent.com/111819437/229812724-92c2aec8-d302-45c5-8b8f-8c542af159dd.png)


## CODE
```.py
class WordCounter:
    def __init__(self, text: str):
        self.text = text

    def count(self):
        # Initialize an empty dictionary to store word counts
         occurrences = {}

         # Split the text into words
         text = self.text.split()

         # Iterate over each word in the text
         for word in text:
             if word in occurrences:
                 # If the word is already in the dictionary, increment its count
                 occurrences[word] += 1
             else:
                 # If the word is not yet in the dictionary, add it with a count of 1
                 occurrences[word] = 1

         # Return the dictionary of word counts
         return occurrences


text = "This is a sample text. It contains some words that will be counted."
word_counter = WordCounter(text)
counts = word_counter.count()

# Print each word and its count on a separate line
for word, count in counts.items():
    print(f"{word}: {count}")
```
## EVIDENCE
![Screen Shot 2023-04-05 at 0 44 09](https://user-images.githubusercontent.com/111819437/229846153-7fb46677-149e-4eab-9f9c-b810ec0ad28b.png)



