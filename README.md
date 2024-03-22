# Muse-Litt-raire-Atelier-d-criture-G-n-ratif-par-IA
Muse Littéraire utilise l'IA générative et les modèles de langage pour proposer des exercices d'écriture créative personnalisés et des suggestions de développement narratif, encourageant l'expression littéraire des utilisateurs.
import random
from transformers import pipeline

# Initialize the text generation model
generator = pipeline('text-generation', model='gpt-2')

# Sample writing prompts to inspire users
writing_prompts = [
    "Write a story about a lost city discovered under the ocean.",
    "Describe a day in the life of a person who can communicate with animals.",
    "Imagine a world where time travel is possible. Write about a character's journey to the past.",
    "Create a dialogue between two characters from different eras who meet by chance.",
    "Write a poem about the change of seasons in a magical forest."
]

# Function to generate a creative writing prompt
def generate_writing_prompt():
    return random.choice(writing_prompts)

# Function to develop narrative suggestions based on user input
def generate_narrative_development(user_input):
    prompt = f"Develop the narrative: {user_input}"
    suggestions = generator(prompt, max_length=100, num_return_sequences=1)
    return suggestions[0]['generated_text']

# Example usage
if __name__ == "__main__":
    # Generate a writing prompt for the user
    prompt = generate_writing_prompt()
    print(f"Writing Prompt: {prompt}\n")
    
    # Assuming the user writes something based on the prompt, we take that as input
    user_input = "The lost city under the ocean was not deserted. It was inhabited by..."
    
    # Generate narrative development based on the user's writing
    narrative_development = generate_narrative_development(user_input)
    print(f"Narrative Development: {narrative_development}")
