# Turning Quantum Noise on Its Head: Using the Noise for Diffusion Models to Generate Images

This is Jason Han's submission (from Rice University) for the [2024 ACM SIGMETRICS Student Research Competition (SRC)](https://www.sigmetrics.org/sigmetrics2024/student_activities.html).

***Our solution won the Undergraduate category in the 2024 ACM SIGMETRICS SRC, and will be proceeding to the SRC Grand Finals.***

## Usage
1. In your terminal, run `git clone https://github.com/positivetechnologylab/QINGDM.git` to clone the repository.
2. Run `cd QINGDM`.
3. Create a virtual environment if necessary, and run `pip install -r requirements.txt` to install the requirements.
4. Run the notebook `DiffusionTrainingNotebook.ipynb`, which contains various functions that are used to train the model.
    - For hyperparameter tuning, modify the `config` variable and use the function `hyperparmeter_tuning`.
    - For the training of a model given hyperparameters (defined as global variables), use the `main` function.
    - For computing the FID score for the model, use the `calc_validation_loss` function, and inject in the function for computing FID scores (in this work, we use the function `calc_fid_given_paths` from the pytorch_fid package).

## Requirements
The requirements and specific versions are provided in `requirements.txt`. Furthermore, this code assumes you have a CPU and GPU available; otherwise, the model training and FID score calculation will not work.

## Side Effects
When computing the validation loss, this code will generate folders to store the saved images. Additionally, when training the model, if you specify to save the results, the code will also create a directory for doing so.

## Repository Structure
- [**`DiffusionTrainingNotebook.ipynb`**](DiffusionTrainingNotebook.ipynb): The notebook containing the code for training a diffusion model given a classical or quantum noise schedule, as well as code for computing the validation loss.
- [**`training_data/`**](training_data/): Directory containing the training data used for the quantum diffusion models. In particular, it contains subdirectories of the form `data_img{digit}`, and within each subdirectory, the training data for the specified number of pairs of Rx gates can be fonud in `data_img{digit}/num_revs_{num_revs}`.
    - The PCA reduced images for each digit are found in `data_img{digit}/original_img{digit}`, and the actual versions of each digit are found in `data_img{digit}/actual_original_img{digit}`.
- [**`README.md`**](README.md): Repository readme with setup and execution instructions.
- [**`requirements.txt`**](requirements.txt): Requirements to be installed before running the Python scripts. These include pytorch for training the model and pytorch_fid for computing the FID scores.

## Copyright
Copyright © 2023 Positive Technology Lab. All rights reserved. For permissions, contact ptl@rice.edu.