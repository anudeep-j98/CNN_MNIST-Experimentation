# Experimentation with MNIST dataset

## Objective: 
Achieve 99.4% accuracy consistantly with model architecture having less than 8000 parameters and epochs less than 15

## Model 1
| Layer                         | Rin  | Rout | Jin  | Jout |
|-------------------------------|-------|------|------|------|
| **Input Image (28x28)**       | 1     | 1    | 1    | 1    |
| **Conv Block 1**              |       |      |      |      |
| Conv2d(1, 8, K=3, P=0, S=1)   | 1     | 3    | 1    | 1    |
| Conv2d(8, 8, K=3, P=0, S=1)   | 3     | 5    | 1    | 1    |
| MaxPool2d(K=2, S=2)           | 5     | 6    | 1    | 2    |
| **Conv Block 2**              |       |      |      |      |
| Conv2d(8, 16, K=3, P=0, S=1)  | 6     | 10   | 2    | 2    |
| Conv2d(16, 16, K=3, P=0, S=1) | 10    | 14   | 2    | 2    |
| MaxPool2d(K=2, S=2)           | 14    | 16   | 2    | 4    |
| **Conv Block 3**              |       |      |      |      |
| Conv2d(16, 10, K=3, P=0, S=1) | 16    | 24   | 4    | 4    |
| AvgPool2d(K=2, S=2)           | 24    | 26   | 4    | 8    |
| **GAP (Global Avg Pool)**     | 26    | Full | 8    | -    |

Target accuracy: 99.4%
Result accuracy: 97.9%
Analysis: Too High Parameters i.e ~12000. Model not improving after certain epochs so should reduce LR. Also should keep params under 8000
Link: 



## Model 2
| Layer                         | Rin  | Rout | Jin  | Jout |
|-------------------------------|-------|------|------|------|
| **Input Image (28x28)**       | 1     | 1    | 1    | 1    |
| **Conv Block 1**              |       |      |      |      |
| Conv2d(1, 8, K=3, P=0, S=1)   | 1     | 3    | 1    | 1    |
| Conv2d(8, 8, K=3, P=0, S=1)   | 3     | 5    | 1    | 1    |
| MaxPool2d(K=2, S=2)           | 5     | 6    | 1    | 2    |
| **Conv Block 2**              |       |      |      |      |
| Conv2d(8, 16, K=3, P=0, S=1)  | 6     | 10   | 2    | 2    |
| Conv2d(16, 16, K=3, P=0, S=1) | 10    | 14   | 2    | 2    |
| MaxPool2d(K=2, S=2)           | 14    | 16   | 2    | 4    |
| **Conv Block 3**              |       |      |      |      |
| Conv2d(16, 10, K=3, P=0, S=1) | 16    | 24   | 4    | 4    |
| AvgPool2d(K=2, S=2)           | 24    | 26   | 4    | 8    |
| **GAP (Global Avg Pool)**     | 26    | Full | 8    | -    |

Target accuracy: 99.4%
Result accuracy: 99.16%
Analysis: Too less Parameters i.e ~5800, model may not be able to learn features. Increasing LR have given good result. Should add and experiment with data augmentation so that it predicts test data in better way
Link: 


## Model 3
| Layer                         | Rin  | Rout | Jin  | Jout |
|-------------------------------|-------|------|------|------|
| **Input Image (28x28)**       | 1     | 1    | 1    | 1    |
| **Conv Block 1**              |       |      |      |      |
| Conv2d(1, 8, K=3, P=0, S=1)   | 1     | 3    | 1    | 1    |
| Conv2d(8, 8, K=3, P=0, S=1)   | 3     | 5    | 1    | 1    |
| MaxPool2d(K=2, S=2)           | 5     | 6    | 1    | 2    |
| **Conv Block 2**              |       |      |      |      |
| Conv2d(8, 16, K=3, P=0, S=1)  | 6     | 10   | 2    | 2    |
| Conv2d(16, 16, K=3, P=0, S=1) | 10    | 14   | 2    | 2    |
| MaxPool2d(K=2, S=2)           | 14    | 16   | 2    | 4    |
| **Conv Block 3**              |       |      |      |      |
| Conv2d(16, 10, K=3, P=0, S=1) | 16    | 24   | 4    | 4    |
| AvgPool2d(K=2, S=2)           | 24    | 26   | 4    | 8    |
| **GAP (Global Avg Pool)**     | 26    | Full | 8    | -    |

Target accuracy: 99.4%
Result accuracy: 99.38%
Analysis: Objective almost reached. Accuracy did not imporve after some epoch. Initiaiting model with lillt higher LR and reducing using scheduler and also experimenting with data augmentation like higher degree of rotation and distorion of images so that it can predict test data in better way
Link: 


## Model 4
| Layer                         | Rin  | Rout | Jin  | Jout |
|-------------------------------|-------|------|------|------|
| **Input Image (28x28)**       | 1     | 1    | 1    | 1    |
| **Conv Block 1**              |       |      |      |      |
| Conv2d(1, 10, K=3, P=0, S=1)  | 1     | 3    | 1    | 1    |
| Conv2d(10, 12, K=3, P=0, S=1) | 3     | 5    | 1    | 1    |
| MaxPool2d(K=2, S=2)           | 5     | 6    | 1    | 2    |
| **Conv Block 2**              |       |      |      |      |
| Conv2d(12, 16, K=3, P=0, S=1) | 6     | 10   | 2    | 2    |
| Conv2d(16, 20, K=3, P=0, S=1) | 10    | 14   | 2    | 2    |
| MaxPool2d(K=2, S=2)           | 14    | 16   | 2    | 4    |
| **Conv Block 3**              |       |      |      |      |
| Conv2d(20, 10, K=3, P=0, S=1) | 16    | 24   | 4    | 4    |
| AvgPool2d(K=2, S=2)           | 24    | 26   | 4    | 8    |
| **GAP (Global Avg Pool)**     | 26    | Full | 8    | -    |

Target accuracy: 99.4%
Result accuracy: 99.48%
Analysis: Achived accuracy and analysis on Model 3 was the primary reason for improvement
Link: 