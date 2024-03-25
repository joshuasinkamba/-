# -
智能写作助手利用大语言模型和自然语言生成技术,为作家提供创意灵感、写作提示和自动编辑建议,促进创意写作过程,提高写作效率和质量。
from transformers import pipeline, set_seed
import random

# Initialize the GPT-2 model pipeline
generator = pipeline('text-generation', model='gpt-2')
set_seed(42)

def get_creative_prompt():
    # You can customize these prompts or add more to suit different creative needs
    prompts = [
        "Write a short story about a time-traveling adventure.",
        "Describe a day in the life of a person who can talk to animals.",
        "Imagine a world where humans live in harmony with nature. Describe it.",
    ]
    return random.choice(prompts)

def get_inspiration(topic):
    # Generate a creative paragraph based on a given topic
    return generator(f"Write something inspiring about {topic}", max_length=100, num_return_sequences=1)[0]['generated_text']

def get_editing_suggestion(text):
    # This is a placeholder function. Ideally, you would implement more complex NLP-based editing suggestions.
    suggestions = [
        "Consider using more active voice.",
        "Try to show, not tell.",
        "Use more sensory details to bring your scenes to life."
    ]
    return random.choice(suggestions)

def main():
    print("Welcome to the Intelligent Writing Assistant.")
    while True:
        print("\nWhat do you need help with?")
        print("1: Get a creative writing prompt")
        print("2: Get inspiration on a topic")
        print("3: Get editing suggestions")
        print("4: Exit")
        choice = input("> ")

        if choice == "1":
            print(f"\nPrompt: {get_creative_prompt()}")
        elif choice == "2":
            topic = input("Enter a topic: ")
            print(f"\nInspiration: {get_inspiration(topic)}")
        elif choice == "3":
            text = input("Enter a piece of text for editing suggestions: ")
            print(f"\nSuggestion: {get_editing_suggestion(text)}")
        elif choice == "4":
            print("Goodbye!")
            break
        else:
            print("Invalid choice. Please enter 1, 2, 3, or 4.")

if __name__ == "__main__":
    main()
