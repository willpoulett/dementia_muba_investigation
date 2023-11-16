# dementia_muba_investigation

Using a dataset from:

https://www.kaggle.com/datasets/anima890/alzheimers-disease-classification/

basic_model.h5 is a model trained with 95% training data, 2.5% validation data, and 2.5% test data. This test data was again split into test set A and test set B, with 30% of the test data being in set A. Set A was used to evaluate the model, set B will be used to help validate the MUBA technique. This gives 48, 112, 160 and 6080 images in test set A, test set B, validation and training data respectively. The random sample is set to 1. It uses only the original data, no augmentation, mixup or oversampling occurs. The best model occurred surprisingly at epoch 2, with an accuracy of 68.8% on validation data. On test A data, the model achieved accuracy of 58.3%, and an F1 score of 63.8% for the demented class.

basic_model_2.h5 takes best_model.h5, freezes all layers excluding the final 100, and trains with a lower learning rate, decreasing from 0.001 to 0.0001. Of 30 epochs, the best model occurs at epoch 23, with a validation accuracy of 75.6%, and an accuracy of 81% on the test set A (F1 = 82.4% for Demented Class).

basic_mixup_model.h5 follows the exact same training process as basic_model.h5. This time however, all the training images are mixed up with a random image form the other class, with an alpha value sampled form the beta function. The dataset sizes are the same. The test and validation data does not include mixup images, to ensure fair evaluation between the models.