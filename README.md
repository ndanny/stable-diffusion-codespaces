# How to run Stable Diffusion in GitHub Codespaces
Setup your own Stable Diffusion instance in the cloud to generate AI images in minutes using [GitHub Codespaces](https://github.com/features/codespaces). **You don’t need an expensive GPU, storage, or a fast internet connection.**

## Getting Started

### Step 1: Create a Codespace

We'll be using [stable-diffusion-webui](https://github.com/AUTOMATIC1111/stable-diffusion-webui). You can use another UI, but with over 25k stars  and 280 contributers, this project is a good open source project that works.

1. Navigate to [AUTOMATIC1111/stable-diffusion-webui](https://github.com/AUTOMATIC1111/stable-diffusion-webui), Click on the **Code** dropdown button, navigate to the **Codespaces** tab, and click **New with options...**
2. Leave everything as is, but change the machine type to the **8-core • 16GB RAM • 64GB storage** version.
3. Create codespace. This should launch a VS Code editor in a new tab.

### Step 2: Install libgl1

Install libgl1 in your new Codespace by executing the following command in your Codespace terminal. If you don't know how to open the terminal, click the burger icon in the top left corner, hover over **Terminal**, and click **New Terminal**. Paste the following command and press enter. This will download the libgl package.

```
sudo apt-get update && sudo apt-get install libgl1
```

### Step 3: Download a model

The next step is to download a stable diffusion model (a checkpoint file) from [HuggingFace](https://huggingface.co) and put it in the `models/Stable-diffusion` folder. These models are often big (2-10GB), so here's a trick to retrieve a checkpoint file and put it in your Codespace in seconds without using any of your internet bandwidth.

1. Find a model you want to use in HuggingFace. It could be the general purpose Stable Diffusion model [stabilityai/stable-diffusion-2-1](https://huggingface.co/stabilityai/stable-diffusion-2-1) or a fine-tuned model such as [prompthero/openjourney-v2](https://huggingface.co/prompthero/openjourney-v2).
2. Once you find a model you want to work with, click on the **Files and versions tab** and look for a file that ends with `.ckpt`. Click that file's link and you'll be navigated to that file's page.
3. Right click the **download** link and copy it.
4. Back in your Codespace terminal, navigate to the `models/Stable-diffusion` folder and download the model in this folder using the following command.
```
cd models/Stable-diffusion && wget https://huggingface.co/prompthero/openjourney-v2/resolve/main/openjourney-v2.ckpt
```
5. Navigate back to the root directory of the project.
```
cd ../..
```

### Step 4: Launch the UI

```
./webui.sh --skip-torch-cuda-test --precision full --no-half
```

## Disclaimers
