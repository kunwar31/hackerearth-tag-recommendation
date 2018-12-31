# Requirements
* Jupyter notebook
* Keras
* Tensorflow
* CUDA capable GPU ( Replace CuDNNGRU/CuDNNLSTM with GRU/LSTM if not available )
* Pandas
* SciKit Learn
* Numpy
* TQDM

# Training Workflow

Please run these jupyter notebooks in order in order to generate the submission file.

1. parse_html
2. clean_data
3. clean_data_punc_brute
4. embeddings
5. embeddings_punc_brute
6. 1_512 
7. 512_1024
8. 1024_1536
9. 1536_2048
10. 2048_2560
11. 2560_3072
12. Combine

submission file : final_submission.csv

### Summarisation 

Training in chunks of 512 tags helps keep the model small and realistically trainable, and allows for higher batch sizes.
Used DICE loss commonly used in image segmentation tasks combined with usual cross-entropy, to achieve better F1 scores.
Used multiple types of RNN cells - LSTMs and GRUs in same model, combined with MaxPooling and Attention both. ( See model summary in any of notebooks 6-11 ).
Used Snapshot Ensembling with Cosine Schedule for resource-cheap ensembling.
Due to high variance in CuDNN, test F1 may differ from run to run.
More epochs/bigger models may lead to better scores but I didn't have resources to train them.
All of the training was done on kaggle kernels, meaning each notebook had 9 hour time limit to run.
Keeping all the punctuations for first 512 tags gave better score than the other way of removing some punctuations, so that was used there. 
Total Train Time ( On TESLA K80 ) : ~55 Hours.


# Externel Resources/ Citation

All (Most) of the externel resources such as code snippets, embeddings, etc. have been linked to their sources in the notebooks itself.
