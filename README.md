# How to run Stable Diffusion in GitHub Codespaces 🎨

Setup your own Stable Diffusion instance in the cloud to generate AI images in minutes using [GitHub Codespaces](https://github.com/features/codespaces). **You don’t need a powerful GPU or a fast internet connection.**

<img src="assets/banner.png" />

## Overview

- **⏱️ Estimated Setup Time**: 7 minutes
- 🐙 A GitHub account is required.
- 🤗 Beginner friendly. It helps to have some experience using a terminal, but it's not required.

## Getting Started

### Step 1: Create a Codespace

We'll be using an open source UI with over 25k stars and 280 contributers for our setup.

1. Navigate to the [AUTOMATIC1111/stable-diffusion-webui](https://github.com/AUTOMATIC1111/stable-diffusion-webui) repo. Click on the **Code** dropdown button, navigate to the **Codespaces** tab, and click **New with options...**
2. Leave everything as is, but change the machine type to **8-core • 16GB RAM • 64GB storage**. *This is the minimum machine type required to run Stable Diffusion. If you don't have this option, please read the FAQ below.*
3. Create codespace. This should launch a VS Code editor in a new tab.

### Step 2: Install dependencies

Install the libgl1 dependency in your new Codespace by executing the following command in your Codespace terminal.

- If you don't know how to open the terminal, click the burger icon in the top left corner, hover over **Terminal**, and click **New Terminal**. Paste the following command and press enter. This will download the required libgl1 package.

    ```
    sudo apt-get update && sudo apt-get install libgl1
    ```

### Step 3: Download a Stable Diffusion model

Next, we're going to download a Stable Diffusion model (a checkpoint file) from [HuggingFace](https://huggingface.co) and put it in the `models/Stable-diffusion` folder. These models are often big (2-10GB), so here's a trick to download a model and store it in your Codespace environment in seconds without using your own internet bandwidth.

1. Find a model you want to use in HuggingFace. It could be the general purpose Stable Diffusion model [stabilityai/stable-diffusion-2-1](https://huggingface.co/stabilityai/stable-diffusion-2-1) or a fine-tuned model such as [prompthero/openjourney-v2](https://huggingface.co/prompthero/openjourney-v2).
2. Once you find a model you want to work with, click on the **Files and versions tab** and look for a file that ends with `.ckpt`. Click that model's link and you'll be directed to that checkpoint file's page.
3. Right click the **download** link and copy the URL.

    <img src="assets/hf_download_link.png" width="500" />
4. Back in your Codespace terminal, navigate to the `models/Stable-diffusion` folder and download the model in this folder using the following command (replace the link below with the URL you copied if you want).

    ```
    cd models/Stable-diffusion && wget https://huggingface.co/prompthero/openjourney-v2/resolve/main/openjourney-v2.ckpt && cd ../..
    ```

### Step 4: Launch the UI

Your setup is almost done! Use the command below in your Codespace terminal to launch the UI. It'll take a few minutes to install dependencies and launch the app.

```
./webui.sh --skip-torch-cuda-test --precision full --no-half
```

You'll get a link to the UI application in your terminal once everything is installed. If you're on Windows, you can "ctrl + click" the link. If you're on Mac, you can "cmd + click" to open the link.

<details>
    <summary>Click to see example</summary>
    
<img src="assets/output.png" width="500" />
</details>

**✅ If everything went smoothly, you should have access to the UI where you can start generating images!**

<img src="assets/ui.png" width="700" />

### Step 5 (Optional): Stop Codespaces

To save on resources, make sure to stop or shutdown your Codespace instance once you're done using it. You can do this in the repo UI or using the [GitHub CLI tool](https://cli.github.com).

## FAQ

**Q. Is this free?**\
A. If you have a GitHub Pro account, you'll have access to the 8-core Codespaces machine type required for this. Otherwise, you'll have to setup billing for Codespaces. If you're a student, most universities will hook you up with a student developer account, which is essentially Pro.

**Q. Who is this guide for?**\
A. This guide is meant for people who want to use their own instance of Stable Diffusion (text-to-img, img-to-img, inpainting, etc) and who doesn't have a powerful computer or fast internet to follow the other existing local setup guides available.

**Q. Is my usage private?**\
A. Yes. Your Codespace instance is private to you.

**Q. Can't I just use Google Colab?**\
A. Sure, you can do that if you prefer. Although, there are performance differences and some people may find Colab difficult to use.

**Q. How long does it typically take to generate an image?**\
A. Since this guide uses CPU for inference, I found that it usually takes 2-3 minutes for text-to-image generation (whereas GPU inference will take a few seconds).

**Q. Can I use a GPU in Codespaces?**\
A. Apparently it's possible to configure your Codespaces environment with a GPU (which should speed up performance considerably), but I've only done surface level research on how to do this. When I have more time I'll look into how you can use GPUs in Codespaces and apply that to this guide.

**Q. What if I want to use my own fine-tuned model that I have on my local machine, not one from HuggingFace?**\
A. You can drag and drop your custom model from your local computer to your VSCode editor. This may take awhile, depending on your internet speed. You can also host your model online and download it remotely to your Codespace environment.

**Q. Where can I find other fine-tuned ML models based on Stable Diffusion?**\
A. Explore HuggingFace https://huggingface.co/models?pipeline_tag=text-to-image&sort=likes or other similar services.

**Q. I have questions, who can I ask?**\
A. Either file an issue or create a new discussion in this repo with your question or comment.

## Disclaimer

*The information provided in this guide is intended for educational purposes only. This guide is not meant to be an endorsement or advertisement for GitHub Codespaces or AUTOMATIC1111's UI. It is simply intended to educate the community on how to run Stable Diffusion models in the cloud based on the limited research conducted. Please note that this may not be the optimal way to use Stable Diffusion, but it does provide an option for those with limited access to compute resources. Additionally, this tutorial is intended to follow the [terms of service of GitHub Codespaces](https://docs.github.com/en/site-policy/github-terms/github-terms-for-additional-products-and-features#codespaces).*
