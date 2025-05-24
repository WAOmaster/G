# RVC Training and Inference Automation via Colab

**Overview:**
This project provides a Google Colab notebook (`RVC_TrainingV2.ipynb`) designed to simplify the process of training and using Retrieval-based Voice Conversion (RVC) models. RVC technology allows for converting a source voice to sound like a target voice while preserving the original speech's prosody and intonation. This notebook automates environment setup, dependency installation, model downloads, and the execution of the RVC WebUI.

**Features:**
- Streamlined setup for RVC model training and inference in a Google Colab environment.
- Automated cloning of the official RVC-Project/Retrieval-based-Voice-Conversion-WebUI.
- Automated download of necessary pre-trained models (for RVC, UVR5 for audio splitting, HuBERT for feature extraction, etc.) from Hugging Face and other sources.
- Integration with Google Drive for storing and retrieving model files and training progress.
- Choice between "training" mode (to train a new model or resume training) and "inference" mode (to use an existing model).

**How to Use `RVC_TrainingV2.ipynb`:**
1.  **Open in Google Colab:** Click the "Open In Colab" badge at the top of the notebook or directly upload it to your Colab environment.
2.  **Set Parameters (Input Form cell):**
    *   `mode`: Choose "training" to train a new voice model or "inference" to use a pre-trained one.
    *   `MODELNAME`: If training or resuming training, specify a unique name for your model. This name will be used for creating directories and naming model files.
3.  **Mount Google Drive:** Run the "Mount Drive" cell and authorize access to your Google Drive. This is crucial for saving your trained models and datasets.
4.  **Run Subsequent Cells:** Execute the cells in order:
    *   **Cloning Github:** Clones the RVC WebUI and prepares directories. It will also copy existing model data from your Drive if you are resuming training or using a model you've previously trained/downloaded to Drive.
    *   **Dependency Installation:** Installs `pyworld` and other requirements.
    *   **Download Pretrained Models:** Downloads all necessary base models. This might take some time.
    *   **Run Web:** Starts the RVC WebUI. A public link (usually `gradio.live`) will be generated, allowing you to access the interface.
5.  **Using the RVC WebUI:**
    *   **Training:** Follow the RVC WebUI instructions for dataset preprocessing, feature extraction, and model training.
    *   **Inference:** Select your model and provide input audio to perform voice conversion.
6.  **Copy Training Result to Drive (if in training mode):** After training, run this cell to save your new model (`G_*.pth`, `D_*.pth`, index files, etc.) and the final `.pth` weight file to your Google Drive in `MyDrive/RVC/{MODELNAME}` and `MyDrive/RVC/weights/` respectively.

**Key Technologies:**
- Python
- PyTorch
- Gradio (for the WebUI, via the RVC project)
- Hugging Face (for hosting pre-trained models)
- Google Colab

**Directory Structure (in Google Drive, managed by the notebook):**
- `MyDrive/RVC/{MODELNAME}/`: Stores model-specific files like generator/discriminator checkpoints, and index files from training.
- `MyDrive/RVC/weights/`: Stores the consolidated `.pth` model files ready for inference.
- The notebook also interacts with `/content/Retrieval-based-Voice-Conversion-WebUI/` within the Colab environment for the RVC software and its assets.

**Note:**
The original `README.md` was a placeholder. This version provides a comprehensive guide based on the `RVC_TrainingV2.ipynb` notebook.
