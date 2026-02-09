## 1. Installation
```
pip install --force-reinstall --upgrade git+https://github.com/Mandelbroetchen/LIPS.git

```

## 2. Download Project Template
```
git clone https://github.com/Mandelbroetchen/LIPS-project-templates
```

## 3. API Key
```
cd LIPS-project-templates/general-code-project
echo MISTRAL_API_KEY=YOUR_MISTRAL_AI_API_KAY > .env
```
If you have multiple or other providers, edit the following files to change which API key variable to use for each stage. 
```
requirements/configs/api.json
specifications/configs/api.json
code-raw/configs/api.json
code-final/configs/api.json
```

## Workflow
Write your first prompt into `requirements/contents/product-requirements.md`, something like

```
# Blackhole Simulation

## Scope
A simple program run in the terminal with:
```bash
python -m blackhole.mp4 input.json
```

## Input
Reads a JSON file as input.

## Output
Generates an MP4 video file.

## Requirements
- Specify the input format and provide an example.
- Implement an accurate general relativity simulation.

```
and run command
```
python -m lips.compile requirements
```
The folder `specifications/contents` will update according to your prompt. You can continue to run command 
```
python -m lips.compile specifications
```

