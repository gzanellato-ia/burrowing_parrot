# burrowing_parrot
Codes for model training and nest-entrance counts on photographs from a Burrowing Parrot colony

PROCEDURE:

1) An expert biologist generates patches with dimensions of 256x256 pixels by randomly selecting them from the original images. These patches should accurately represent the colony configuration. The expert also produces the required set of dot maps by placing a single pixel to approximate the center of each nest on an image of zeros. The patches and their corresponding dot maps are then stored in local folders named "original_patches" and "original_dots."
  
2) Execute the Jupyter Notebook script titled "Adding_images.ipynb," which carries out data augmentation via horizontal flips for both the patches and their corresponding dot maps. The script saves the complete augmented set within folders labeled "final_patches" and "final_dots."

3) During the ultimate counting process, the 3000x4000 pixel images are gridded into 256x256 pixel patches. However, the algorithm overestimates the counts by predicting false nests in areas where none exist, such as the sky, the beach at the cliff's bottom, fallen rocks, or water bodies. To address this issue, we introduce empty patches to the training set, representing these areas, along with corresponding empty dot maps. The Jupyter Notebook script "new_patches_creation.ipynb" can be employed to generate these empty patches. We anticipate that approximately 30%-40% of the entire training set should consist of these empty patches. In the future, this percentage could be reduced by capturing images focused solely on the cliff and taking closer shots, thereby avoiding the inclusion of the sky or beach.

4) The resulting collection of patches and dot maps are uploaded to the Google Drive repository at: https://drive.google.com/drive/folders/1n200sPnM8jUHflfTkpXBfc0PEL8mbM6z?usp=sharing, under the folders "parches" and "puntos."

5) To train the models, execute the Google Colab scripts: a) "burrowing_parrots_UNet.ipynb," b) "burrowing_parrots_ResUNet.ipynb," and c) "burrowing_parrots_DeepLabv3.ipynb." Google Colab is utilized to leverage available GPUs. In our study, each script is executed 7 times, generating a total of 7 models, each subjected to 7 counts.

6) For the counting task, the image set is stored in the Google Drive repository at: https://drive.google.com/drive/folders/1IXhXNUsAx_8Su3stdxb-BGsgJFGdg9Fb?usp=sharing, within folders "por_kilometro" and "por_kilometro_marcadas." The former encompasses 18 folders, each containing images for a specific kilometer of the colony. The latter also consists of 18 folders, containing similar images, but with vertical yellow lines marked by the expert to delineate the counting area.

7) To perform the final colony-wide counting, utilize the Google Colab script "whole_colony_counting.ipynb." The script additionally generates a report named "resultados_conteo_"+"name-of-the-used-model".txt," which is saved within the same Google Drive repository.






