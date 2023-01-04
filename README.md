# OpenAI Image Generation Script

This script allows you to generate and download images using OpenAI's image generation API.

## Prerequisites

- You will need an API key from OpenAI, which you can obtain by creating an account at [https://beta.openai.com/signup/](https://beta.openai.com/signup/)
- Your API key should be stored in a file called `.openai-key` in your home directory.

## Running the script

To run the script, execute the following command:

python3 generate-img.py

You will be prompted to enter the following:

- A prompt, which is a text description of the image you want to generate
- The number of images you want to generate
- The size of the images you want to generate (options are 256x256, 512x512, or 1024x1024)

The script will then generate the requested images and print the URLs of the generated images. You will be prompted to enter the number of images you want to download, and the chosen images will be downloaded and saved to your current working directory.
