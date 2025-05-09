# Projet_LSIN202

FILTRE GRIS EXPLICATION
img = img.convert("L") --> .convert prend une image ici "img" est convertit ses pixels en mode "luminance", chaque pixel de l'image n'ont plus qu'une valeur au lieu de 3(R, G et B)\n
matrice_pixels = np.array(img.convert("RGB")) --> ici stock dans la variable "matrice_pixels" un tableau des pixels de img, grâce à np.array, que l'on a reconvertit en rgb afin d'avoir 3 valeur

GAMMA EXPLICATION
gamma = 1.0 / float(valeur_gamma_str) --> on inverse la valeur du slider comme ça les valeurs de gamma au dessus de 1 augmente la luminosité et en dessous la baisse et non l'inverse 
matrice_norm = matrice_pixels.astype(np.float32) / 255.0 --> Convertit les valeurs en flottantes pour plus de précision
matrice_corr = np.power(matrice_norm, gamma) --> sortie=(entree)^^γ
matrice_gamma = np.clip(matrice_corr * 255, 0, 255).astype(np.uint8) --> après avoir appliquer gamma reconversion vers des valeurs entiers et transforme en entiers 8 bits pris en compte pour les images

np.power --> applique un exposant a tous les elements d'un tableau
np.clip --> pour être sûr que les valeurs d'un tableau ne dépasse pas celles donner en arguments
