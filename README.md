

# Metastasis Segmentation Using Nested U-Net and Attention U-Net

## Overview
This project focuses on the segmentation of metastases in brain images using two powerful deep learning architectures: **Nested U-Net** and **Attention U-Net**. These models are designed to enhance the accuracy of medical image segmentation, which is critical for detecting brain metastases. 

The models are trained on annotated medical images and aim to identify metastasis regions with high precision, improving diagnostic support for clinicians.

## Architectures
### Nested U-Net
Nested U-Net (also known as U-Net++) enhances the original U-Net by adding dense connections between layers of the encoder and decoder. This helps the model capture multi-scale contextual information, making it especially useful for segmenting complex structures in medical images.

- **Benefits**: Improved segmentation accuracy due to rich multi-scale feature extraction.
- **Application**: Used to refine metastasis segmentation with more detailed boundary detection.

### Attention U-Net
The Attention U-Net introduces attention gates that enable the model to focus on the most relevant regions of an image. This is particularly helpful when certain regions (like metastases) are small or hard to distinguish from surrounding tissues.

- **Benefits**: Allows the model to emphasize metastasis regions and suppress irrelevant background features.
- **Application**: Enhances the segmentation by learning to prioritize metastasis regions while filtering out noise.

## Brain Metastasis Segmentation
Brain metastasis segmentation presents unique challenges, such as:

- **Small tumor size**: Metastases are often small and scattered, making them hard to detect.
- **High variability**: Variability in shape, size, and location of metastases across patients complicates the segmentation task.
- **Data imbalance**: Datasets often contain many more non-metastasis regions than metastasis regions, leading to class imbalance.

This implementation addresses these challenges through careful dataset preparation, model architecture choices, and post-processing techniques.

## Installation and Setup

### Prerequisites
Make sure you have the following installed:

- Python 3.x
- TensorFlow 2.x or PyTorch (depending on your implementation)
- Streamlit for the UI
- OpenCV, PIL, and other image processing libraries

### Instructions
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/metastasis-segmentation.git
   cd metastasis-segmentation
   ```

2. Install the dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Run the Streamlit UI:
   ```bash
   streamlit run app.py
   ```

4. Access the UI in your browser at `http://localhost:8501` to interact with the metastasis segmentation model.

### Dataset
- The project uses a dataset of annotated brain images.
- Ensure that your dataset is properly formatted with image and mask pairs. Modify the paths in the code as needed to point to your dataset location.

## Running the Code
To train the model, use the following command:
```bash
python train.py --model nested_unet --epochs 50
```
You can also switch to the Attention U-Net by specifying the `--model` argument:
```bash
python train.py --model attention_unet --epochs 50
```

Once training is complete, you can use the `predict.py` script to run the segmentation on new images:
```bash
python predict.py --model attention_unet --input ./path_to_image
```


## Challenges in Brain Metastasis Segmentation
1. **Data Scarcity**: A limited amount of annotated medical data.
   - **Solution**: Data augmentation techniques such as flipping, rotation, and scaling were used to artificially increase the dataset size.

2. **Complexity of Metastasis Boundaries**: Small and diffuse metastasis regions can be challenging for segmentation models.
   - **Solution**: The Nested U-Net's dense connections and the Attention U-Net's gating mechanisms improve boundary localization and reduce false positives.

3. **Class Imbalance**: There are significantly more non-metastasis regions compared to metastasis regions.
   - **Solution**: Loss functions such as focal loss were used to handle class imbalance by emphasizing harder-to-classify regions.



---

This template provides a comprehensive guide to your project, including descriptions of the models, setup instructions, challenges, and solutions. You can adapt it to suit your specific project and data.
