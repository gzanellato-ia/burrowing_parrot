# burrowing_parrot
Codes for model training and nest-entrance counts on photographs from a Burrowing Parrot colony

PROCEDURE:

1) An expert biologist creates patches of dimension 256 x 256 pixels, taken ramdomly from the original images. The patches should be representative of the colony configuration. The expert also creates the recessary set of dot maps, marking the approximate center of each nest with a single pixe, on an image of zeros. The patches and the corresponding dot maps are saved on local folders called "original_patches" and "original_dots".

2) Run the Jupyter Notebook script "Adding_images.ipynb", which performs data augmentation through horizontal flips over both, patches and the corresponding dot maps. The script saves the whole augmented set in folders called "final_patches" and "final_dots".

3) During the final counting task, we grid the entire 3000x4000 pixel images into 256x256 pixel patches. The algorithm overestimates the counting predicting false nests over areas where there are none, such as empty areas, beaches, rocks or water. To solve the problem, we add to the training set some empty patches representing those areas, with corresponding empty dot maps. To create these empty patches (without nests) we can use the Jupyter Notebook script "new_patches_creation.ipynb". We estimate that 30%-40% of the entire training set should be empty patches. In the future, this percentage could be lower, if the images are focused on the cliff and closer pictures are taken, avoiding capturing the sky or the beach for example.

4) The resulting set of patches and dot maps are uploaded in the Google Drive repository: https://drive.google.com/drive/folders/1n200sPnM8jUHflfTkpXBfc0PEL8mbM6z?usp=sharing. Folders: "parches" and "puntos".

5) To train the models run the Google Colab scripts: a) "burrowing_parrots_UNet.ipynb", b) "burrowing_parrots_ResUNet.ipynb" and c) "burrowing_parrots_DeepLabv3.ipyng". We use Google Colab to take advantage of the available GPUs. In our work we run each script 7 times, to generate 7 models, and execute 7 counts per model.

6) For the counting task, the set of images are saved in the Google Drive repository: https://drive.google.com/drive/folders/1IXhXNUsAx_8Su3stdxb-BGsgJFGdg9Fb?usp=sharing, folders "por_kilometro" and "por_kilometro_marcadas". The first one contains 18 folders, each one containing the images of each kilometre of the colony. The second one contains another 18 folders with similar images, but in this case we can find the vertical yellow lines marked by the expert to delimit the counting area.

7) For the final counting of the entire colony, use the Google Colab script "whole_colony_counting.ipynb". The script also creates a report called "resultados_conteo_<name-of-the-used-model>.txt", saved in the same Google Drive repository.
