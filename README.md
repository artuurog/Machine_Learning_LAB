# Machine Learning Lab 2026

## Vision-Language Models for Robotic Manipulation

This laboratory course introduces **Vision-Language Models (VLMs)** and their use for controlling a robotic manipulator.

Students will design a system where:
- A human provides a natural language instruction
- A Vision-Language Model interprets the scene
- The model generates a task plan
- Task plan is converted into robot actions (_x, y, z_ coordinates)
- The plan is executed in:
    - Simulation (MuJoCo)
    - Real robot (ABB GoFa)

The objective is to bridge machine learning, perception, and robot control in a structured workflow.

## Learning Objectives

By the end of this lab, you should be able to:
1. Understand what a Vision-Language Model is and how it works.
2. Use an API-based AI model from Hugging Face.
3. Process visual input (RGB image) and textual input.
4. Convert high-level instructions (e.g., “pick the red cube”) into robot actions.
5. Execute a task pipeline in simulation.
6. Deploy the same logic to a real ABB GoFa robot.
7. Evaluate limitations and failure cases.

## Repo structure
  
- [Colab notebook](https://github.com/artuurog/Machine_Learning_LAB/blob/main/README.md#colab-tutorial)
- [MuJoCo simulation environment](https://github.com/artuurog/Machine_Learning_LAB/blob/main/README.md#mujoco-simulation)
- [API keys on Huggingface](https://github.com/artuurog/Machine_Learning_LAB/blob/main/README.md#getting-a-hugging-face-api-key)  
- [Models](https://github.com/artuurog/Machine_Learning_LAB/blob/main/README.md#available-vision-language-models)  
- [Resources](https://github.com/artuurog/Machine_Learning_LAB/blob/main/README.md#resources)  

---
## What is a Vision-Language Model?

A Vision-Language Model (VLM) is a neural network that can process:
- Images
- Text
- (Sometimes video)

It learns a shared representation between vision and language, allowing it to describe images, answer questions about images (_Visual Question Answering_), follow visual instructions (_Visual prompting_), generate action plans based on visual context and many other tasks.

In this lab, the VLM will receive:

**Input**
- RGB image of the scene
- Text instruction (e.g., “Pick the blue block and place it on the green block”)

**Output**
- A structured action plan (e.g., object → position → action sequence)

The action plan has to be converted into low-level control actions.

---

## Project Workflow

The project is organized into the following phases:

1. **Background and Setup**  
   - Define the problem, tools, and software environment
   - Installation and configuration of required libraries and frameworks
   - Set up MuJoCo simulation
   - Create a Hugging Face account and get an API key
   - Define the task (what the robot has to do)
   
    
2. **Perception**  
   Processing sensor data (e.g. RGB images, robot states) to extract meaningful information about the environment.
   Input:
    - RGB image (from simulation or real camera)
      
    Tasks:
    
    - Capture image
    
    - Preprocess image with segmentation model, object detection (if necessary)
    
    - Format input for the VLM (textual prompt + image)
    
    Output:
    
    - A function that returns structured scene information.

3. **Reasoning**  
   Applying VLMs to interpret perceptual inputs and decide which actions the robot should take.
   Input:

    - Scene image
    
    - User instruction
    
    Task:
    
    - Query the VLM
    
    - Extract structured output
    
    Here you may use prompt engineering and force structured JSON outputs to guide the reasoning and constrain response format.
        
    Deliverable:
    
    - A structured task plan

4. **Action translation**  
   Translating decisions (_"pick red cube"_) into robot actions, such as motion (_"x y z"_) and manipulation (_"open/close gripper"_).
   Convert semantic commands into:
   - Target Cartesian coordinates

   - Gripper commands (open/close)

   - Motion sequence

    Deliverable:
    
    - Executable motion plan in MuJoCo.

5. **Experiments**
   Test the action plan on the simulated robot. Try it on the real robot only when you are satisfied with your simulations.
    - Test success rate

    - Analyze errors

    - Identify failure modes

6. **Real Robot Deployment on ABB GoFa**
    Transfer validated pipeline to the physical robot.
    SAFETY AND VALIDATION ARE MANDATORY BEFORE EXECUTION!

7. **Evaluation and Analysis**  
   - Testing the system, analyzing performance, and discussing limitations and possible improvements
   - Use different models and compare their performance
   - Try different requests and check the task plan and robot execution
   
   
---

## Materials Provided

The following materials are provided:

- **Colab notebook** shows an example of Python implementation for a MuJoCo simulation
- **List of models** you can start using via Huggingface Inference Providers
- **Documentation and tutorials** explaining key concepts and implementation details  

Students are encouraged to extend or modify the provided materials as part of the project.

---


## Colab tutorial 
The Colab notebook can be accessed [here](https://github.com/artuurog/Machine_Learning_LAB/blob/main/Lab_example.ipynb).

It demonstrates:

1. Loading MuJoCo

2. Rendering the scene

3. Capturing an RGB image

4. Sending image + prompt to a VLM

5. Receiving a response

Use it as reference for API formatting, prompt construction, image encoding.


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

An API key is a private authentication token that allows your program to access hosted AI models.
You can think of it as a password for your program that allows it to access Hugging Face models on your behalf.

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

## Model Selection Guidelines

Choosing which model to use is not easy. Most of the times, you have to consider different aspects and make a trade-off decision. Here are some general indications

**Smaller models (2B–8B):**

- Faster

- Cheaper

- Less reasoning capability

**Larger models (70B+):**

- Better reasoning

- Slower

- Higher cost

For robotic planning:

Structured output quality is more important than conversational ability. Find the model that generates a good, structured plan that can be easily converted into robot actions.

--- 

## Resources
- [Vision Language Models Explained](https://huggingface.co/blog/vlms)
- [Vision Language Models (Better, faster, stronger)](https://huggingface.co/blog/vlms-2025)
- Demonstration-Free Robotic Control via LLM Agents [link](https://arxiv.org/abs/2601.20334)
- [MuJoCo official documentation](https://mujoco.readthedocs.io/en/stable/overview.html)
- [MuJoCo Python tutorial](https://colab.research.google.com/github/google-deepmind/mujoco/blob/main/python/tutorial.ipynb)

## Important Notes
Please keep in mind that:

- The VLM does NOT control the robot directly, it generates _semantic reasoning_.

- You are responsible for translating that reasoning into safe robot commands.

- ALWAYS validate motion plans in simulation before running on real hardware.
