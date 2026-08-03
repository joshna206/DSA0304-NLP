import random

# Sample training text
text = """
natural language processing is a branch of artificial intelligence
natural language processing is used in chatbots
artificial intelligence is transforming the world
language models generate text
"""

# Tokenize text into words
words = text.lower().split()

# Create Bigram Dictionary
bigram = {}

for i in range(len(words) - 1):
    current_word = words[i]
    next_word = words[i + 1]

    if current_word not in bigram:
        bigram[current_word] = []

    bigram[current_word].append(next_word)

# Function to generate text
def generate_text(start_word, length=15):
    if start_word not in bigram:
        return "Start word not found."

    result = [start_word]
    current = start_word

    for _ in range(length - 1):
        if current in bigram:
            current = random.choice(bigram[current])
            result.append(current)
        else:
            break

    return " ".join(result)

# Display Bigram Dictionary
print("Bigram Model:\n")
for word, next_words in bigram.items():
    print(f"{word} -> {next_words}")

# Generate text
print("\nGenerated Text:\n")
print(generate_text("natural", 12))
