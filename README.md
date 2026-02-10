# VLMs & Robots

This project focuses on the use of **Vision-Language Models (VLMs)** and **Robotics**, with the goal of understanding how these algorithms can be used to perceive, reason, and act in the physical world.

The main objectives of the project are:
- to teach a robot pick-and-place operations through textual instructions,
- to implement the obtained task plan both in simulation and in real world experiments on an ABB GoFa robot,
- to bridge theory and practice through hands-on experimentation.

## Index
  
- [Colab notebook](https://github.com/artuurog/Machine_Learning_LAB/blob/main/README.md#colab-tutorial)
- [MuJoCo simulation environment](https://github.com/artuurog/Machine_Learning_LAB/blob/main/README.md#mujoco-simulation)
- [API keys on Huggingface](https://github.com/artuurog/Machine_Learning_LAB/blob/main/README.md#getting-a-hugging-face-api-key)  
- [Models](https://github.com/artuurog/Machine_Learning_LAB/blob/main/README.md#available-vision-language-models)  
- [Resources](https://github.com/artuurog/Machine_Learning_LAB/blob/main/README.md#resources)  

---

## Project Structure and Phases

The project is organized into the following phases:

1. **Background and Setup**  
   Define the problem, tools, and software environment. Installation and configuration of required libraries and frameworks.
   Clearly identify the inputs and outputs of each module and function you will use.

3. **Perception**  
   Processing sensor data (e.g. RGB images, robot states) to extract meaningful information about the environment.

4. **Reasoning and Decision-Making**  
   Applying VLMs to interpret perceptual inputs and decide which actions the robot should take. The model will receive a textual instruction from the human user, and generate an action plan accordingly.

5. **Action and Control**  
   Translating decisions ("pick red cube") into robot actions, such as motion ("x y z") and manipulation ("open/close gripper").

6. **Experiments**
   Test the action plan on the simulated robot. Try it on the real robot once you are satisfied with your simulations.

8. **Evaluation and Analysis**  
   Testing the system, analyzing performance, and discussing limitations and possible improvements.
   
---

## Materials Provided

The following materials are provided:

- **Colab notebook** to show an example of Python implementation for a MuJoCo simulation
- **List of models** you can work with using API keys provided by Huggingface Inference Providers
- **Documentation and tutorials** explaining key concepts and implementation details  

Students are encouraged to extend or modify the provided materials as part of the project.

---


## Colab tutorial 
how to use the Colab notebook 

## MuJoCo simulation
[Here](https://github.com/artuurog/GoFa_MuJoCo_sim/tree/main) you can find a MuJoCo simulation environment with an ABB GoFa robot for tabletop manipulation.
<img src="https://github.com/artuurog/Machine_Learning_LAB/blob/main/img/mujoco_scene.png" align="center" width="30%" height="30%">

The model consists of an XML file and various .STL meshes of the robot parts.
If you want to modify the `scene.xml` file, refer to the [MuJoCo XML Reference](https://mujoco.readthedocs.io/en/stable/XMLreference.html)


## Getting a Hugging Face API Key

This project uses models hosted on **Hugging Face**, a platform that provides access to many AI models through an API.  
To use these models, you need a **Hugging Face API key** (also called an *access token*).

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
`export HUGGINGFACE_API_KEY="your_token_here"`

#### On Windows
`setx HUGGINGFACE_API_KEY "your_token_here"`

---
## Available Vision-Language Models

Below is a non-exhaustive list of Hugging Face models that can be used with this project.  
Each entry includes the **model name**, a **link to its Hugging Face page**, and the **model size** (number of parameters).

### Model List

| Model Name | Hugging Face Page | Size (Parameters) |
|-----------|------------------|-------------------|
| `Molmo2-8B` | https://huggingface.co/allenai/Molmo2-8B?inference_provider=publicai | 8B |
| `Qwen2.5-VL` | https://huggingface.co/Qwen/Qwen2.5-VL-72B-Instruct?inference_provider=hyperbolic | 72B |
| `SmolVLM` | https://huggingface.co/HuggingFaceTB/SmolVLM-Instruct| 2B |
| `Kimi-K2.5` | https://huggingface.co/moonshotai/Kimi-K2.5?inference_provider=novita| 171B |

Explore more models from [this](https://huggingface.co/models?pipeline_tag=image-text-to-text&inference_provider=all&sort=trending) page!


## Resources
- [Vision Language Models Explained](https://huggingface.co/blog/vlms)
- [Vision Language Models (Better, faster, stronger)](https://huggingface.co/blog/vlms-2025)
- Articles
- [MuJoCo official documentation](https://mujoco.readthedocs.io/en/stable/overview.html)
- [MuJoCo Python tutorial](https://colab.research.google.com/github/google-deepmind/mujoco/blob/main/python/tutorial.ipynb)
- 
