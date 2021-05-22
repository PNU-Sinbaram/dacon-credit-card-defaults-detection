# dacon-credit-card-defaults-detection
[![Visualization](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/sinbaramDL/dacon-credit-card-defaults-detection/blob/main/visualization.ipynb)
[![Classification](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/sinbaramDL/dacon-credit-card-defaults-detection/blob/main/classification.ipynb)

## Experiment Table

|    | Gradient Boosting | Light GBM | TabNet  |
| -- | ----------------- | --------- | ------- |
|  1 |      0.86089      | 0.85449   | 0.86643 |
|  2 |      0.84499      | 0.82350   | 0.85591 |
|  3 |      0.84039      | 0.80406   | 0.85327 |
|  4 |      0.84039      | 0.80346   | 0.85130 |
|  5 |      0.79965      | 0.73655   | 0.81079 |
|  6 |      0.79921      | 0.73911   | 0.81336 |
|  7 |      0.85392      | 0.81340   | 0.86568 |
|  8 |      0.79925      | 0.73891   | 0.87343 |
|  9 |      0.79921      | 0.73911   | 0.90922 |
| 10 |      0.74303      | 0.73150   | 0.81722 |

1. Baseline performance
   * occyp 드랍
   * boolean value들 0, 1 binarize
   * child 2 이상은 모두 2로 치환
   * family_type과 같은 nominal value들 label encoding
   * income_total과 같은 numeric value들 discretize 
2. Feature creation
   * occyp drop X
   * child, family_size 치환 X
   * boolean value들 0, 1 binarize
   * family_type과 같은 nominal value들 label encoding
   * income_total과 같은 numeric value들 discretize 
   * remove duplicates
3. remove duplicates X
   * occyp drop X
   * Feature creation
   * child, family_size 치환 X
   * boolean value들 0, 1 binarize
   * family_type과 같은 nominal value들 label encoding
   * income_total과 같은 numeric value들 discretize 
4. nominal type들 one hot
   * occyp drop X
   * Feature creation
   * child, family_size 치환 X
   * boolean value들 0, 1 binarize
   * income_total과 같은 numeric value들 discretize 
5. Feature creation X + label encoding
   * occyp drop X
   * child, family_size 치환 X
   * boolean value들 0, 1 binarize 하지 않고 onehot
   * income_total과 같은 numeric value들 discretize X
6. Feature creation X + onehot encoding
   * occyp drop X
   * child, family_size 치환 X
   * boolean value들 0, 1 binarize 하지 않고 onehot
   * income_total과 같은 numeric value들 discretize X
7. Feature creation X + onehot encoding + discretize
   * occyp drop X
   * child, family_size 치환 X
   * boolean value들 0, 1 binarize 하지 않고 onehot
8. Feature creation X + onehot encoding + normalization
   * occyp drop X
   * child, family_size 치환 X
   * boolean value들 0, 1 binarize 하지 않고 onehot
9.  tabnet cost sensitive learning (add weight to torch.nn.CrossEntropyLoss)
10. optuna (hyperparameter tuning)