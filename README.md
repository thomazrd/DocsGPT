<h1 align="center">
  DocsGPT  🦖
</h1>

<p align="center">
  <strong>Open-Source Documentation Assistant</strong>
</p>

<p align="left">
  <strong>DocsGPT</strong> is a cutting-edge open-source solution that streamlines the process of finding information in project documentation. With its integration of the powerful <strong>GPT</strong> models, developers can easily ask questions about a project and receive accurate answers.
  
Say goodbye to time-consuming manual searches, and let <strong>DocsGPT</strong> help you quickly find the information you need. Try it out and see how it revolutionizes your project documentation experience. Contribute to its development and be a part of the future of AI-powered assistance.
</p>

<div align="center">
  
  <a href="https://discord.gg/n5BX8dh8rU">![example1](https://img.shields.io/github/stars/arc53/docsgpt?style=social)</a>
  <a href="https://discord.gg/n5BX8dh8rU">![example2](https://img.shields.io/github/forks/arc53/docsgpt?style=social)</a>
  <a href="https://discord.gg/n5BX8dh8rU">![example3](https://img.shields.io/github/license/arc53/docsgpt)</a>
  <a href="https://discord.gg/n5BX8dh8rU">![example3](https://img.shields.io/discord/1070046503302877216)</a>


  
</div>

### Enterprise Solutions: 

When deploying your DocsGPT to a live environment, we're eager to provide personalized assistance. Reach out to us via email [here]( mailto:contact@arc53.com?subject=DocsGPT%20Enterprise&body=Hi%20we%20are%20%3CCompany%20name%3E%20and%20we%20want%20to%20build%20%3CSolution%3E%20with%20DocsGPT) to discuss your project further, and our team will connect with you shortly.

### [🎉 Join the Hacktoberfest with DocsGPT and Earn a Free T-shirt! 🎉](https://github.com/arc53/DocsGPT/blob/main/HACKTOBERFEST.md)

![video-example-of-docs-gpt](https://d3dg1063dc54p9.cloudfront.net/videos/demov3.gif)


## Roadmap

You can find our [Roadmap](https://github.com/orgs/arc53/projects/2) here. Please don't hesitate to contribute or create issues, it helps us make DocsGPT better!

## Our open source models optimised for DocsGPT:

| Name              | Base Model | Requirements (or similar)                        |
|-------------------|------------|----------------------------------------------------------|
| [Docsgpt-7b-falcon](https://huggingface.co/Arc53/docsgpt-7b-falcon)  | Falcon-7b  |  1xA10G gpu   |
| [Docsgpt-14b](https://huggingface.co/Arc53/docsgpt-14b)              | llama-2-14b    | 2xA10 gpu's   |
| [Docsgpt-40b-falcon](https://huggingface.co/Arc53/docsgpt-40b-falcon)       | falcon-40b     | 8xA10G gpu's  |


If you don't have enough resources to run it you can use bitsnbytes to quantize


## Features

![Group 9](https://user-images.githubusercontent.com/17906039/220427472-2644cff4-7666-46a5-819f-fc4a521f63c7.png)


## Useful links
 [Live preview](https://docsgpt.arc53.com/)
 
 [Join Our Discord](https://discord.gg/n5BX8dh8rU)
 
 [Guides](https://docs.docsgpt.co.uk/)

 [Interested in contributing?](https://github.com/arc53/DocsGPT/blob/main/CONTRIBUTING.md)

 [How to use any other documentation](https://docs.docsgpt.co.uk/Guides/How-to-train-on-other-documentation)

 [How to host it locally (so all data will stay on-premises)](https://docs.docsgpt.co.uk/Guides/How-to-use-different-LLM)


## Project structure
- Application - Flask app (main application)

- Extensions - Chrome extension

- Scripts - Script that creates similarity search index and store for other libraries. 

- Frontend - Frontend uses Vite and React

## QuickStart

Note: Make sure you have Docker installed

1. Download and open this repository with `git clone https://github.com/arc53/DocsGPT.git`
2. Create a .env file in your root directory and set the env variable OPENAI_API_KEY with your OpenAI API key and  VITE_API_STREAMING to true or false, depending on if you want streaming answers or not
   It should look like this inside:
   
   ```
   OPENAI_API_KEY=Yourkey
   VITE_API_STREAMING=true
   SELF_HOSTED_MODEL=false
   ```
   See optional environment variables in the `/.env-template` and `/application/.env_sample` files.
3. Run `./run-with-docker-compose.sh`
4. Navigate to http://localhost:5173/

To stop just run Ctrl + C

## Development environments

### Spin up mongo and redis
For development only 2 containers are used from docker-compose.yaml (by deleting all services except for Redis and Mongo). 
See file [docker-compose-dev.yaml](./docker-compose-dev.yaml).

Run
```
docker compose -f docker-compose-dev.yaml build
docker compose -f docker-compose-dev.yaml up -d
```

### Run the backend

Make sure you have Python 3.10 or 3.11 installed.

1. Export required environment variables
```commandline
export CELERY_BROKER_URL=redis://localhost:6379/0   
export CELERY_RESULT_BACKEND=redis://localhost:6379/1
export MONGO_URI=mongodb://localhost:27017/docsgpt
```
2. Prepare .env file
Copy `.env_sample` and create `.env` with your OpenAI API token
3. (optional) Create a Python virtual environment
```commandline
python -m venv venv
. venv/bin/activate
```
4. Change to `application/` subdir and install dependencies for the backend
```commandline
cd application/ 
pip install -r requirements.txt
```
5. Run the app `python wsgi.py`
6. Start worker with `celery -A app.celery worker -l INFO`

### Start frontend 
Make sure you have Node version 16 or higher.

1. Navigate to `/frontend` folder
2. Install dependencies
`npm install`
3. Run the app 
`npm run dev`



Built with [🦜️🔗 LangChain](https://github.com/hwchase17/langchain)

