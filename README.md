# LLM-driven Iterative Project Synthesis (LIPS)
## Overview
LLM-driven Iterative Project Synthesis (LIPS) is a pipeline designed to help developers and teams rapidly generate, refine, and implement software projects using large language models.  

The workflow is iterative: you provide high-level project requirements, which the system converts into detailed specifications, scaffolds project files, and progressively generates code through stages.  

LIPS supports multiple AI providers via configurable API keys and allows for repeated refinement at each stage. 
  
## Usage
### 1. Installation
```
pip install --force-reinstall --upgrade git+https://github.com/Mandelbroetchen/LIPS.git
```

### 2. Download Project Template
Download the [templates](https://github.com/Mandelbroetchen/LIPS-project-templates) manually or use command
```
git clone https://github.com/Mandelbroetchen/LIPS-project-templates
```

### 3. API Key
First, `cd` into the working folder. 
```
cd LIPS-project-templates/general-code-project
```
Create an empty file `.env` and add the line
```
MISTRAL_API_KEY=YOUR_MISTRAL_AI_API_KAY
```
Replace `YOUR_MISTRAL_AI_API_KAY` with your own API key. Add multiple lines if you have multiple or other providers. Edit the following files to choose which API key to use for each stage. 
```
requirements/configs/api.json
specifications/configs/api.json
code-raw/configs/api.json
code-final/configs/api.json
```

### Workflow
Write your first prompt into `requirements/contents/product-requirements.md`, something like

```
# Blackhole Simulation

## Scope
A simple program run in the terminal with:

python -m blackhole.mp4 input.json


## Input
Reads a JSON file as input.

## Output
Generates a GIF file as output. Each frame of the GIF file is a plot chart. 

## Requirements
- Specify the input format and provide an example.
- Implement an accurate general relativity simulation.

```
and run command
```
python -m lips.compile requirements
```
The folder `specifications/contents` will update according to your prompt. 

```
specifications/contents/
    development-guidelines.md
    README.md
    class-diagram.puml
    package-diagram.puml
    usecase-diagram.puml
```

You can continue to run command 
```
python -m lips.compile specifications
```
The folder `code-raw/contents` will update according to the specifications in `specifications/contents`. 
```
code-raw/contents/
    YOUR_PROJECT_NAME/
        file1.extension1
        file2.extension2
        folder1/
            file3.extension3
            file4.extension4
        ...
    resources/
        resource1.extension1
        resource2.extension2
        ...
    ...
```