# Deep Learning Lab - Experiment 5
### Comprehensive CNN Tuning, Transfer Learning, and Cross-Validation

This contains the implementation, experiments, and LaTeX documentation for **Experiment 5**. The goal of this experiment is to systematically study the impact of various deep learning techniques on Convolutional Neural Networks (CNNs) and successfully apply transfer learning to a complex image classification task.

## Objective
To experimentally demonstrate how CNN performance is strongly influenced by initialization, regularization, optimization, and hyperparameter choices. The lab explores the **MobileNetV2** architecture, performs transfer learning and fine-tuning, and uses **5-Fold Cross-Validation** to select a reliable, highly-generalizing final configuration.

## Dataset
**Oxford-IIIT Pet Dataset**
- **Classes:** 37 distinct breeds of cats and dogs.
- **Task:** Fine-grained multi-class image classification.

## Experimental Phases

1. **Weight Initialization:** 
   - Evaluated `Zero`, `Random Normal`, `Xavier/Glorot`, and `He` initialization.
   - *Result:* Xavier and He initializations provided significantly faster and more stable convergence, avoiding vanishing/exploding gradients.
2. **Regularization & Overfitting:** 
   - Compared models with no regularization against `L2 Regularization`, `Dropout`, and `Batch Normalization`.
   - *Result:* Adding Dropout ($0.25$) and Batch Normalization effectively closed the generalization gap and prevented validation loss spikes.
3. **Optimization Algorithms:** 
   - Trained using `SGD`, `Momentum`, `RMSProp`, and `Adam`.
   - *Result:* Adam and Momentum converged rapidly and achieved the highest final accuracies ($\sim 91\%$), outperforming basic SGD.
4. **Hyperparameter Tuning:** 
   - Evaluated varying Learning Rates ($0.001$ vs $0.0001$), Batch Sizes ($16, 32, 64$), and Dropout rates.
5. **Transfer Learning & Fine-Tuning:** 
   - Leveraged **MobileNetV2** (pre-trained on ImageNet).
   - *Result:* Feature extraction established a strong baseline, while fine-tuning (unfreezing deeper layers with a smaller learning rate) pushed the validation accuracy even higher.
6. **K-Fold Cross-Validation:** 
   - The top configurations were strictly evaluated using 5-Fold CV to ensure the model wasn't just "lucky" on a specific train/test split.

##  Final Selected Model Configuration
After extensive testing, the most robust configuration yielded a **Mean CV Accuracy of $91.52\% \pm 0.0075$** and an independent **Test Accuracy of $90.22\%$**.

- **Architecture:** MobileNetV2 (Fine-Tuned)
- **Initialization:** He Normal
- **Regularization:** Batch Normalization + Dropout ($0.25$)
- **Optimizer:** Adam (Learning Rate: $0.001$)
- **Batch Size:** 32

## Project Links
- **Complete Code (Google Colab):** [View Notebook](https://colab.research.google.com/drive/19jyI1hcjt5Db6LtSSruVbzdvYgA5ZC-d?usp=sharing)
- **K-Fold CV Execution (Kaggle):** [View Notebook](https://www.kaggle.com/code/kothahasini/dl-exp5)
