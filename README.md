# #nowplaying-RS: A Benchmark Dataset for Context Aware Music Recommendation

Here, you can find the codes for implementation of the experiments conducted on the #nowplaying-RS dataset.   
We have used Factorization Machines[1] to perform the music recommendation experiments.  

The #nowplaying-RS dataset can be downloaded from http://dbis-nowplaying.uibk.ac.at/#nowplayingrs  

```

}
```

## Data

Since the #nowplaying-RS is an implicit dataset, the train-test splits provided contain Listening Events (LEs) with positive ratings. However, for model training and evaluation of Factorization Machines, negative examples are needed. Here, we provide the scripts that have been used to creating the final training and test sets that can be input to the FM.

## Environment
Python 3.5  
R 3.4.3  

## Dependencies  
#### Python  
- numpy    
- sklearn    
- pyfm  
- pandas  
- math  
- time   
#### R    
- plyr  
- dplyr 
- data.table  
- Stack

## Creating Final Training and Test Sets
1. [Context_POP_RND]: This folder contains the scripts [train_POP_RND.r] and [test_POP_RND.r] to create the traning and test set splits respectively for context-aware recommendation in the POP_RND setting.   
2. [Context_POP_USER]: This folder contains the scripts [train_POP_USER.r]) and [test_POP_USER.r] to create the traning and test set splits respectively for context-aware  recommendation in the POP_USER setting.  
3. [Sequence]: This folder contains the scripts [train_seq.r] and [test_seq.r] to create the traning and test set splits respectively for context-aware next-song recommendation.

## Code
The following scripts, stored in this repository, have been developed for implementing Factorization Machines for music recommendation using the dataset.
1. [main.py]: The main file from which the other scripts are called.  
2. [group.py]: The test set is ordered according to the user_id. However, this is optional as the test set provided has already been ordered according to user_id. 
3. [load.py]: Shows how to load the dataset. You can enter the attributes with which you want to train the Factorization Machine here. (In this file, for example, the attributes user_id + track_id + tempo(context) have been used to train the FM for context-aware recommendation. You could also do next-song recommendation by using the attributes: user_id + track_id + previous_track_id + context to train the FM).  
4. [runFM.py]: Training of the Factorization Machine takes place and prediction.
5. [calcMRR.py]: Calculation of Mean Reciprocal Rank (MRR).

## Usage

##### 1. Downloading the dataset.
You can download the datasets and uncompress the archives using the following commands:
```
wget http://dbis-nowplaying.uibk.ac.at/wp-content/uploads/nowplayingrs.zip
wget http://dbis-nowplaying.uibk.ac.at/wp-content/uploads/nowplayingrs_train_test.zip
unzip nowplayingrs.zip
unzip nowplayingrs_train_test.zip
```

```
##### 2. Installing the dependencies as have been mentioned above.  
##### 3. Creating the final train-test splits which can be used as input to the FM.  
For example, to make context-aware recommendation in the POP_RND setting, create the final training and test sets using the following commands:
```
Rscript train_POP_RND.r   
Rscript test_POP_RND.r   
```
The required training and test sets would be created, which can be input to the FM by specifying the file names in [main.py](https://github.com/asmitapoddar/nowplaying-RS-Music-Recommendation-FM/blob/master/main.py)

##### 4. Running the code.
```
python3.5 main.py
```
