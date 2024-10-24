![AyaMCooking Logo](./assets/AyaMCookingLogo.png)

# AyaMCooking 🍳
Bhavnick Minhas*<sup>1</sup>, Sree Harsha Nelaturu*<sup>1</sup> </br>
<sup>1</sup> ML Efficiency Group, Cohere For AI Community
(*contributed equally)


🍳 AyaMCooking is a Voice-to-Voice Multi-lingual RAG Agent that makes a perfect sous chef for your kitchen, in 10 languages!

In this notebook, we demo just one of the numerous capabilities enabled by a truly multilingual workflow as that which is enabled by Aya Expanse by Cohere For AI and Cohere.

## 🍽️ What can AyaMCooking do?

AyaMCooking is a versatile tool that can assist you in various culinary tasks. Here are some of the things it can do:

1. **🍲 Recipe Generation**: AyaMCooking can generate recipes based on the ingredients you have at hand, ensuring you can always cook something delicious with what you have.

2. **🌐 Multilingual Support**: It supports up to 10 languages, allowing you to access and understand recipes from different cuisines around the world.

3. **🎙️ Voice-to-Voice Interaction**: You can interact with AyaMCooking using voice commands, making it easy to use while cooking without needing to touch your device.

4. **🔄 Ingredient Substitution**: AyaMCooking can suggest substitutes for ingredients you might not have, helping you adapt recipes to what is available.

5. **🍎 Nutritional Information**: It can provide nutritional information for recipes, helping you make healthier choices.

6. **👩‍🍳 Cooking Tips**: AyaMCooking offers cooking tips and tricks to improve your culinary skills and make your cooking process more efficient.

7. **📅 Meal Planning**: It can help you plan your meals for the week, ensuring you have a balanced diet and reducing food waste.

8. **🛒 Shopping List Generation**: Based on your meal plan or selected recipes, AyaMCooking can generate a shopping list for you.

9. **🥗 Dietary Preferences**: It can filter recipes based on dietary preferences or restrictions, such as vegetarian, vegan, gluten-free, etc.

10. **📖 Step-by-Step Instructions**: AyaMCooking provides step-by-step cooking instructions, making it easy to follow along and cook complex dishes.

With these capabilities, AyaMCooking becomes an indispensable assistant in your kitchen, helping you explore new cuisines, improve your cooking skills, and make meal preparation more convenient.

## 🌍 Languages Supported

AyaMCooking supports the following languages and their respective language codes:

- **English** (`en`)
- **French** (`fr`)
- **Spanish** (`es`)
- **German** (`de`)
- **Italian** (`it`)
- **Turkish** (`tr`)
- **Hindi** (`hi`)
- **Korean** (`ko`)
- **Japanese** (`ja`)
- **Persian** (`fa`)

**Note:** While Aya Expanse supports 23 Languges, AyaMCooking supports 10 only since other components in the pipeline like the ASR model, Embedding, Rerank and TTS model support different collections of languages. We tried to find a good itersection for all these models and our own culinary preferences to create this set of 10 langauges. 

## 🧪 Methodology

People often would like to try a local cuisine, but the authentic recipes are often in the language of origin -- finding the ingredients, substitutes, and other information is challenging and limits creativity.

- We first use Aya Expanse to generate recipe candidates, which are then used to generate recipes as well. This forms our dataset, which we subsequently embed at a later stage to form our index.

- Often, rather than typing a query and reading a recipe, you'd prefer if it was audio-based - it's just easier to follow with all the ingredients around. Therefore, we build a workflow where you can speak to Aya and get a response back in audio form.

- The pipeline uses Whisper to transcribe recorded audio across a wide variety. The textual question transcribed in the original language is then passed through a Multi-lingual RAG system where the index and embeddings are constructed using Cohere-multilingual-v3-Embed, and for refinement, we use Cohere ReRank3.

- The context extracted from the RAG, and our prompt, are combined with the language code and passed through Aya Expanse to generate a textual response. This is then used to generate a voice response using Coqui TTS in the language of the user's query.

- The multi-lingual capabilities allow us to extract recipes and information from various other languages and provide context, which can lead to some very creative recipe suggestions that are still grounded in local culture and taste.

The notebook is documented, and the only thing you'll need on your end is a bit of creativity, luck (the hope is the audio recording, GPU VM on Colab, etc., are readily available), and a Cohere API key.

Have fun leveraging the power of open source!

Harsha | Bhavnick

## 📦 Recipe Dataset

We provide a default dataset containing 100 recipes from the 10 languages and cultures that were generated using Aya Expanse. These recipes are available on [Hugging Face](https://huggingface.co/datasets/deepmage121/aya_recipes).

Here's a _truncated_ sample from the dataset: 

```json
{
    "language" : "en", 
    "recipe" : "# Fish and Chips ## Description: A classic British dish consisting of battered and fried fish, typically cod or haddock, served with thick-cut chips (French fries). This comforting meal is often accompanied by malt vinegar, lemon wedges, and a side of mushy peas. ## Instructions: 1. **Prepare the Fish:** - Cut the fish fillets into serving-size pieces. You'll need about 4-6 pieces per person, depending on appetite. - Pat the fish dry with paper towels. This step is crucial for achieving a crispy batter. ..." 
}
```

## 🙏 Acknowledgement

We would like to extend our heartfelt thanks to the entire **Aya Expanse** team from **Cohere for AI** and **Cohere** for making this notebook possible and for their support throughout the development process. Additionally, we are grateful to Cohere for providing the API credits that made this project feasible.

## 📚 Citation 
```bibtex
@software{AyaMCooking,
    title        = {AyaMCooking: A Voice-to-Voice Multilingual RAG Bot for Cooking},
    author       = {Minhas, Bhavnick and Nelaturu, Sree Harsha},
    year         = 2024,
    month        = 10,
    version      = {0.0.1}
}
```