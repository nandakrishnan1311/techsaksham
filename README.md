# **Image Generation using Stable Diffusion & ComfyUI**  
### **TechSaksham Internship**  

## **ComfyUI Download & Model Links**  
- [ComfyUI GitHub Repository](https://github.com/comfyanonymous/ComfyUI)  
- [Stable Diffusion Model](https://huggingface.co/Comfy-Org/stable-diffusion-v1-5-archive/blob/main/v1-5-pruned-emaonly-fp16.safetensors)  

---

## **Step 1: Prepare the Files**  

### **1. Download & Extract ComfyUI**  
- Extract the `comfyui_windows_portable_nvidia` folder to a location on your computer (e.g., `C:\ComfyUI`).  
- Inside the folder, you’ll find files like `run_nvidia_gpu.bat`, which is used to launch ComfyUI.  

### **2. Download & Place the Stable Diffusion Model**  
- Download the `v1-5-pruned-emaonly-fp16.safetensors` file from the link above.  
- Move the file to the following directory inside ComfyUI:  
  ```
  C:\ComfyUI\models\checkpoints\
  ```

---

## **Step 2: Launch ComfyUI**  

### **1. Start the Server**  
- Double-click the `run_nvidia_gpu.bat` file in the ComfyUI folder.  
- This will start the ComfyUI server and open a terminal window. Wait for it to load completely.  

### **2. Open the Web Interface**  
- Once the server is running, open your browser and visit:  
  ```
  http://127.0.0.1:8188
  ```
- This is the ComfyUI interface where you can generate images.  

---

## **Step 3: Load the Model**  

### **1. Select the Model**  
- In the ComfyUI interface, locate the **"Checkpoint Loader"** node.  
- Click on it and select your model (`v1-5-pruned-emaonly-fp16.safetensors`) from the dropdown menu.  

### **2. Set Up the Workflow**  
- Ensure the workflow includes the following nodes:  
  - **Checkpoint Loader** (loads the model).  
  - **CLIP Text Encode** (for text prompts).  
  - **KSampler** (generates images).  
  - **VAE Decoder** (converts latent images to RGB).  
  - **Save Image** (saves the output).  
- If any nodes are missing, right-click on the canvas and add them manually.  

---

## **Step 4: Generate an Image**  

### **1. Enter a Prompt**  
- In the **CLIP Text Encode** node, enter a prompt (e.g., *"A futuristic cityscape at sunset"*).  
- Optionally, enter a negative prompt (e.g., *"blurry, low quality"*).  

### **2. Adjust Settings in KSampler**  
- `Steps`: **20-30**  
- `CFG Scale`: **7-12**  
- `Seed`: Leave blank for random  

### **3. Generate the Image**  
- Click the **"Queue Prompt"** button.  
- The image will be generated and saved in the `ComfyUI/output/` folder.  

---

## **Step 5: Save and View the Image**  
- Images are saved automatically in `ComfyUI/output/`.  
- You can also view them directly in the **Save Image** node.  

---

## **Optional: Customize the Workflow**  
- Add a **ControlNet** node for pose or edge-guided generation.  
- Use a **LoRA** node for fine-tuned models.  
- Enable **Latent Upscaler** for higher resolution images.  

---

## **Troubleshooting**  

### **1. Model Not Showing Up**  
- Ensure the `.safetensors` file is inside `models/checkpoints/`.  
- Restart ComfyUI if needed.  

### **2. Out of Memory (OOM) Errors**  
- Reduce the image resolution in **KSampler**.  
- Enable `--medvram` or `--lowvram` in `run_nvidia_gpu.bat`.  

### **3. Slow Performance**  
- Update your NVIDIA GPU drivers.  
- Lower batch size or resolution.  

---

## **Demo Video**  
[https://youtu.beY-NbjTJ3ZA ](https://www.youtube.com/watch?v=Y-Nbj4TJ3ZA)

---
