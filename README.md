
# OpenAI Image Generation Script

This script allows you to generate and download images using the OpenAI API.

## Requirements
    Python 3.6 or higher
    The requests library (can be installed with pip install requests)
## Usage

    Store your OpenAI API key in a file at $HOME/.openai-key.
    Run the script with python generate-img.py.
    Follow the prompts to enter a prompt, image count, and size.
    The script will generate and display a list of image URLs.
    Enter the number of images you want to download.
    The script will download the images and save them to the current directory with filenames in the format ABBREV_PROMPT_TIMESTAMP.png.




## Examples

```bash
$ python3 generate-img.py
Enter a prompt: dancing monkey
Enter the count: 2
Enter a size (1 for 256x256, 2 for 512x512, 3 for 1024x1024): 2
Generating images...
####################

Created: 1672811302


Image URLs:
dancing monkey-#1 https://image-url.png

dancing monkey-#2 https://image-url.png

Enter the number of images to download (1-2): 2

Downloading image 1 of 2
Saved as DM_01-03-2023-23:48:31.png

Downloading image 2 of 2
Saved as DM_01-03-2023-23:48:32.png
```
    
## Tech Stack


Python 3.9.2
