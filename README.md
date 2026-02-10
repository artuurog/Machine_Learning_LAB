# VLMs & Robots

## Colab tutorial
how to use the Colab notebook 

## MuJoCo simulation
Here you can find a MuJoCo simulation environment with an ABB GoFa robot for tabletop manipulation:
[GoFa MuJoCo sim](https://github.com/artuurog/GoFa_MuJoCo_sim/tree/main)

## Getting a Hugging Face API Key

This project uses models hosted on **Hugging Face**, a platform that provides access to many AI models through an API.  
To use these models, you need a **Hugging Face API key** (also called an *access token*).

No prior AI or API experience is required. Follow the steps below.

---

### What is an API key?

An API key is a secret string that identifies you when your code communicates with an online service.  
You can think of it as a **password for your program** that allows it to access Hugging Face models on your behalf.

⚠️ **Important:**  
- Do **not** share your API key publicly  
---

### Create a Hugging Face API key

1. **Create a Hugging Face account**
   - Go to https://huggingface.co
   - Click **Sign Up** (top right)
   - Create an account using email, Google, or GitHub

2. **Go to your Access Tokens page**
   - Once logged in, click on your **profile picture** (top right)
   - Select **Settings**
   - In the left sidebar, click **Access Tokens**

3. **Create a new token**
   - Click **New token**
   - Choose a name (e.g. `my-first-api-key`)
   - Select **Read** as the role (this is sufficient for most projects)
   - Select other options according to your needs
   - Click **Generate token**

4. **Copy and store the token**
   - Copy the generated token immediately
   - Save it in a secure place

   You will not be able to see it again after leaving the page.

---

### Using the API key in your project

Most projects expect the API key to be stored as an **environment variable**.

#### On Linux / macOS
export HUGGINGFACE_API_KEY="your_token_here"

#### On Windows
setx HUGGINGFACE_API_KEY "your_token_here"



## VLMs you can use
possibili modelli da usare con diverse caratteristiche e dimensioni
- Molmo
- SmolVLM
- Qwen-VL

## Available Vision-Language Models

Below is a non-exhaustive list of Hugging Face models that can be used with this project.  
Each entry includes the **model name**, a **link to its Hugging Face page**, and the **model size** (number of parameters).

You can choose a model based on your hardware constraints and performance needs.  
Smaller models are faster and require fewer resources; larger models are generally more capable but slower.

---

### Model List

| Model Name | Hugging Face Page | Size (Parameters) |
|-----------|------------------|-------------------|
| `model-name-1` | https://huggingface.co/organization/model-name-1 | 7B |
| `model-name-2` | https://huggingface.co/organization/model-name-2 | 3B |
| `model-name-3` | https://huggingface.co/organization/model-name-3 | 1.3B |
| `model-name-4` | https://huggingface.co/organization/model-name-4 | 350M |

---

### How to choose a model

- **≤ 1B parameters**: suitable for laptops and fast experimentation  
- **1B – 7B parameters**: good trade-off between performance and speed  
- **> 7B parameters**: higher quality results, but requires more memory and compute  

Refer to the model’s Hugging Face page for detailed documentation, usage examples, and license information.

You can replace the entries above with the specific models supported by this project.


## Resources
- [Vision Language Models Explained](https://huggingface.co/blog/vlms)
- [Vision Language Models (Better, faster, stronger)](https://huggingface.co/blog/vlms-2025)
- Articles
- [MuJoCo official documentation](https://mujoco.readthedocs.io/en/stable/overview.html)
- [MuJoCo Python tutorial](https://colab.research.google.com/github/google-deepmind/mujoco/blob/main/python/tutorial.ipynb)
- 
