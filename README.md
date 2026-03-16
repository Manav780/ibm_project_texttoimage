# Text-to-Image Generation with Stable Diffusion XL

This project implements a text-to-image generation application in Python using the Stable Diffusion XL model through the **Hugging Face Hub API.
The application allows users to enter a text prompt and generate an AI-created image through a simple web interface built with Gradio.

# Overview

The script installs the required libraries and connects to the Hugging Face inference API using an authentication token.

A function called generate_image() sends the user prompt to the model and receives the generated image.

The application then launches a Gradio web interface, where users can type a prompt and instantly view the generated image.

This demonstrates a simple implementation of Generative AI image creation using APIs.

# Dependencies

Make sure you have the following Python libraries installed before running the script:

pillow

requests

huggingface_hub

gradio

You can install them using pip:

pip install pillow requests huggingface_hub gradio

# How It Works

Authentication

The Hugging Face API requires an access token for authentication.
The token is stored in an environment variable using:

os.environ["HF_TOKEN"]

This allows secure access to the inference API.

Model Initialization

The application creates an inference client using the Hugging Face library and loads the Stable Diffusion XL model.

client = InferenceClient(
    provider="nscale",
    api_key=os.environ["HF_TOKEN"],
    model="stabilityai/stable-diffusion-xl-base-1.0"
)

This client will be used to send prompts and receive generated images.

Image Generation

The generate_image(prompt) function takes a text prompt from the user and sends it to the model.

image = client.text_to_image(prompt)

The model processes the prompt and generates a corresponding image.

User Interface

A web interface is created using Gradio.

iface = gr.Interface(
    fn=generate_image,
    inputs=gr.Textbox(),
    outputs=gr.Image()
)

This connects the backend image generation function to a simple UI where users can enter prompts.

Application Launch

Finally, the interface is launched using:

iface.launch()

This starts a local web server and opens the application in a browser.

# Usage

To run the application, execute the Python script:

python app.py

After running the script:

A Gradio web interface will open in your browser.

Enter a text prompt such as:

"A futuristic city at sunset"

The system will generate an image based on the prompt.

# Example Prompt
"A fantasy castle floating in the sky with dragons flying around"

The AI model will generate a corresponding image using Stable Diffusion XL.

# Features

Text-to-image generation using AI

Integration with Hugging Face Hub

Interactive web interface using Gradio

Simple and beginner-friendly Python implementation

# Future Improvements

Add multiple image styles

Allow image downloads

Improve generation speed

Add prompt history and gallery
