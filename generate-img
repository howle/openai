import os
import json
import requests
from datetime import datetime
import time
import random

# Read the API key from the $HOME/.openai-key file
key_file = os.path.join(os.environ['HOME'], '.openai-key')
if not os.path.exists(key_file):
    print("Please ensure your key is stored in $HOME/.openai-key")
    exit(1)
with open(key_file, 'r') as f:
    api_key = f.read().strip()

# Prompt the user for input
prompt = input("Enter a prompt: ")
count = int(input("Enter the count: "))
size = input("Enter a size (1 for 256x256, 2 for 512x512, 3 for 1024x1024): ")

# Map the size input to the corresponding size value
if size == '1':
    size = '256x256'
elif size == '2':
    size = '512x512'
elif size == '3':
    size = '1024x1024'

# Build the request payload
data = {
    "prompt": prompt,
    "n": count,
    "size": size
}

# Display a progress bar while generating the images
print("Generating images...")
for i in range(20):
    time.sleep(random.uniform(0.5, 1.5))
    print("#", end='', flush=True)

# Send the request to the API
response = requests.post(
    'https://api.openai.com/v1/images/generations',
    headers={'Authorization': f'Bearer {api_key}', 'Content-Type': 'application/json'},
    data=json.dumps(data)
)

# Print the response in a human-readable format
response_data = response.json()
print(f'\n\nCreated: {response_data["created"]}')

# Extract the image URLs from the response data
image_urls = [image['url'] for image in response_data['data']]

# Print the image URLs in underlined blue text, with a newline between each URL
print('\n\nImage URLs:')
for i, url in enumerate(image_urls):
    print(f'\033[4m\033[94m{prompt}-#{i+1}\033[0m {url}')
    print()

# Prompt the user for the number of images to download
download_count = int(input(f'Enter the number of images to download (1-{len(image_urls)}): '))

# Abbreviate the prompt for use in the filename
abbrev_prompt = ''.join([word[0] for word in prompt.split()]).upper()

# Download the specified number of images
for i, url in enumerate(image_urls[:download_count]):
    print(f'\nDownloading image {i+1} of {download_count}')
    response = requests.get(url)
    filename = f'{abbrev_prompt}_{datetime.now().strftime("%m-%d-%Y-%H:%M:%S")}.png'
    with open(filename, 'wb') as f:
        f.write(response.content)
    print(f'Saved as {filename}')
