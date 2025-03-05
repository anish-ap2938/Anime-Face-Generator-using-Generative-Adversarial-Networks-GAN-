# Anime-Face-Generator-using-Generative-Adversarial-Networks-GAN

## Anime Face Generation using GAN

This repository contains the code for generating anime faces using a Generative Adversarial Network (GAN) trained on the Crypko dataset. In this project, I built a model based on the DCGAN architecture with improvements inspired by the WGAN-GP framework.

![image](https://github.com/user-attachments/assets/1dc89eb3-bc4f-45f6-89a0-8211b8b68f62)

## Overview

The objective of this project is to train an anime face generator that can produce high-quality images, as measured by the Anime Face Detection (AFD) rate. The implementation starts with a benchmark DCGAN and then extends it with modifications such as gradient penalty (WGAN-GP) to stabilize training and improve image quality.

## Dataset

- **Source:** Crypko dataset  (https://drive.google.com/file/d/1IJdJcXPNN_B7mMMPQO950szHZgFVvpT_/view)
- **Details:** 71,314 `.jpg` files of anime faces  
- **Usage:** The dataset was used for training the GAN. Data augmentation techniques (e.g., shifting, flipping) were applied during training to improve robustness, but only the original images were used for evaluation.
- 
![image](https://github.com/user-attachments/assets/f8015cdc-0d25-40e6-9c76-5a97c744fc59)

## Model Architecture

### Generator

- **Architecture:** Based on DCGAN  
  - Uses ConvTranspose layers for upsampling.
  - Employs Batch Normalization for training stability.
  - Uses ReLU activation functions in hidden layers.

### Discriminator

- **Architecture:** Based on DCGAN  
  - Uses convolutional layers with Batch Normalization.
  - Uses LeakyReLU activation functions.
  - The final sigmoid layer was removed in accordance with WGAN-GP guidelines.
  - 
![image](https://github.com/user-attachments/assets/ea9c2814-5fe5-4ebc-8fc1-d8452a8322ba)

## Modifications & Improvements

### WGAN-GP Enhancements

- The loss calculation is modified as per WGAN standards, avoiding the traditional GAN loss with logarithms.
- A gradient penalty term was added to the loss function to enforce the Lipschitz constraint without weight clipping.
- The optimizer was switched to Adam to take advantage of its adaptive learning rate capabilities.

### Hyperparameter Tuning

- Extensive tuning of learning rates, number of epochs, and other optimizer parameters was performed to achieve better performance.

## Training Details

- **Benchmark Model:**  
  The initial DCGAN model was run as a benchmark (with a runtime of ~15 minutes) to achieve an AFD rate of around 1.1%.
  
- **Improved Model:**  
  Building on the benchmark, the DCGAN was enhanced with WGAN-GP modifications. Training duration varied between 2–6 hours depending on the hyperparameters and training schedule.
  
- **Evaluation:**  
  The quality of generated images was assessed using an anime face detection metric (AFD rate), where a higher rate indicates better quality.

## Outputs

- **Generated Images:**  
  After training, the generator was used to produce 1000 anime face images.  
  The images are saved with filenames `1.jpg`, `2.jpg`, …, `1000.jpg`.
  
- **Packaging:**  
  The generated images were compressed into a tarball named `images.tgz` using the provided compressing script.

## Code Structure

- **Notebook:**  
  - `ap2938_HW7_DL (2).ipynb` – Contains the full implementation including data loading, model definition, training loops, and image generation.
  
- **Key Modules:**  
  - **Data Preprocessing:** Code to load and optionally augment the Crypko dataset.
  - **Model Definition:** Code implementing the generator and discriminator architectures, along with the custom loss functions incorporating gradient penalty.
  - **Training Loop:** Script to train the GAN and monitor performance using the AFD metric.
  - **Image Generation:** Code to generate 1000 images and save them with sequential numbering.

## Conclusion

This project demonstrates the use of a DCGAN-based architecture, enhanced with WGAN-GP modifications, to generate high-quality anime face images. The improvements in training stability and image quality are reflected in the AFD rate, making the generated images competitive for further evaluation. All code and generated outputs are provided in this repository.
