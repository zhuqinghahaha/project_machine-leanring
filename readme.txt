Machine learning Project----automatic music genre classification

MainGoal: Music genre classification

Data Resource: "GTZAN Genre Collection" with 10 genres and 100 tracks in each class.

Resource Website: http://marsyasweb.appspot.com/download/data_sets/

Original edition: Project-music%2Bgenre%2Bclassification%2B.ipynb

Revised edition: Project-music+genre+classification+.ipynb

Procedures:

1.Features extration from the audio files

Using library librosa to which has many useful functions for music feature extraction.
Features we used in this demo include mfccs, chroma energy,tempo(BPM), RMSE and ZCR. For mfccs and chroma, it should be a 2D matrix, but we didn't use the whole matrix instead we take the mean value over time as our features.

2.Traning and Testing

For each class, we have a 100(tracks)*35(feature values) data matrix.For it takes quite a while to extract features, so we save the matrixes into .mat files. So we don't need to run the extraction process over again.
We 'vstack' the 10 matrixes into one as X, and we label each class(blues=0, classical=1...rock=9) to generate a label vector y. Function 'train_test_split' in sklearn is used to divide X and y in to train and test sets. We used 800 samples for training and 200 for testing. Xtr and Xts are normalized over columns before training.

Multilayer Perceptron (MLP) was used for our multi-class softmax classification. We have print the model summary in this demo. We use Adam(lr=0.001) as optimizer and 'sparse_categorical_crossentropy' as loss function.

In another way, we use the built-in function MLPClassifier in library sklearn.nerual_network to perform the classification and test data prediction. We shuffle and divide the data matrix X,y for 5 times, and for each trial we print the confusion matrix and its hot-map to show the results. We also generate a confusion matrix which counts across all the 5 trials, it shows a result overall.3. Results analysisThe accuracy of the classification is about 0.65~0.7. Some ways to boost the accuracy: a. Apply more tracks into the data set, we only have 1000 music tracks for 10 genres classification. b. Use high dimensional features, in this demo, the feature matrixes we use are 2D. c. If we have high dimensional features, then we have more choices of nerual network like CNN, LSTM and so on.


