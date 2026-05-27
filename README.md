## Prototype Development for Image Generation Using the Stable Diffusion Model and Gradio Framework

### AIM:
To design and deploy a prototype application for image generation utilizing the Stable Diffusion model, integrated with the Gradio UI framework for interactive user engagement and evaluation.

### PROBLEM STATEMENT:

The task involves creating a user-friendly interface where users can input text descriptions (prompts) to generate high-quality, realistic images using the Stable Diffusion model. The prototype aims to demonstrate the capabilities of the model while ensuring ease of interaction through Gradio.

### DESIGN STEPS:

#### STEP 1: Set Up Environment Install the required libraries (diffusers, transformers, torch, gradio). Verify GPU support for running Stable Diffusion.

#### STEP 2: Load the Stable Diffusion Model Use the diffusers library to load the Stable Diffusion pipeline. 

#### STEP 3: Define the Gradio Interface Design the user interface to accept text prompts and generate corresponding images.Add parameters for customization (e.g., number of inference steps, guidance scale).

#### STEP 4: Integrate the Model with the Interface Connect the Stable Diffusion model to the Gradio interface for real-time inference. 

#### STEP 5: Deploy and Test Launch the Gradio application locally or on a server. Test with diverse prompts to ensure functionality.

### PROGRAM:
```
NAME: Danica
REG.NO : 212223240022
```
```
import os, io, requests, gradio as gr
from PIL import Image
from dotenv import load_dotenv

load_dotenv()

API = os.environ['HF_API_TTI_BASE']
KEY = os.environ['HF_API_KEY']

def generate(prompt):
    r = requests.post(
        API,
        headers={"Authorization": f"Bearer {KEY}"},
        json={"inputs": prompt}
    )

    img = Image.open(io.BytesIO(r.content))
    return img

gr.Interface(
    fn=generate,
    inputs="text",
    outputs="image",
    title="Stable Diffusion Image Generator"
).launch(share=True)
```
### OUTPUT:

<img width="1010" height="699" alt="image" src="https://github.com/user-attachments/assets/ccb5355f-75c8-4c70-9444-c5aa4b91cbef" />


 
### RESULT:
The prototype successfully demonstrates text-to-image generation using Stable Diffusion, providing an interactive and user-friendly interface. Users can modify parameters to influence the output quality and style.
