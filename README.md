<h1>Harmful Brain Activity Classification</h1>

---

<h2> <strong> Objectives and Goal</strong></h2>

* To create a model that can automates EEG analysis will help doctors and brain researchers detect seizures and other types of brain activity that can cause brain damage, so that they can give treatments more quickly and accurately. 
* May also help researchers who are working to develop drugs to treat and prevent seizures.
* To detect and classify seizures and other types of harmful brain activity in critical ill patients.
* To develop a model trained on [EEG (Electroencephalography)](https://en.wikipedia.org/wiki/Electroencephalography) signals recorded from critically ill hospital patients.

---

## Patterns for Classification:
1. Seizure (SZ)
2. Generalized periodic discharges (GPD)
3. Lateralized periodic discharges (LPD)
4. Lateralized rhythmic delta activity (LRDA)
5. Generalized rhythmic delta activity (GRDA)
6. Other

---

##### Detailed explanation of above patterns:
* https://www.acns.org/UserFiles/file/ACNSStandardizedCriticalCareEEGTerminology_rev2021.pdf 


* In some cases experts completely agree about the correct label. On other cases the experts disagree. They call segments where there are high levels of agreement “idealized” patterns. Cases where ~1/2 of experts give a label as “other” and ~1/2 give one of the remaining five labels, we call “proto patterns”. Cases where experts are approximately split between 2 of the 5 named patterns, we call “edge cases”.

1. High level of agreement                        - Idealized pattern
2. Half of experts give a label                    - Other
3. Half of experts give one of the remaining five label      - proto patterns
4. Experts split between 2 of the 5 named patterns - edge cases

<h1 style="color: blue;"> Dataset Flowchart </h1>
</div>

<a href="https://imgur.com/JuRILfJ"><img src="https://i.imgur.com/JuRILfJ.jpg" title="source: imgur.com" /></a>

<p>
    Dataset comprises two main components: training and testing data. The training dataset consists of three folders: spectrograms, EEG, and metadata.
    <li> Spectrograms: Contains 11138 files representing unique spectrogram IDs, each with 408 rows and 401 columns.</li>
        <li>EEG: Contains 17300 files representing unique EEG IDs, each comprising 12000 rows and 20 columns.</li>
            <li>Metadata: Holds essential information about the spectrograms and EEG data, including target labels.</li>
    
    
 Similarly test dataset also has Spectrogram, EEG and Metadata.
        </p>

---

<div style="text-align:center;">
    <h1 style="color: blue;">  <strong> Spectrogram Data  </strong> </h1>

<a href="https://imgur.com/azRNvZv">
    <img src="https://i.imgur.com/azRNvZv.jpg" title="source: imgur.com" /></a>
</div>

---

<div style="text-align:center;">
    <h1 style="color: blue;">  <strong> Spectrograms  </strong> </h1>
<a href="https://imgur.com/ELn7UOW"><img src="https://i.imgur.com/ELn7UOW.jpg" title="source: imgur.com" /></a></div>

EEG spectrograms are valuable for analyzing brain activity patterns associated with different cognitive states, tasks, or clinical conditions. They can provide insights into changes in brain oscillations across different frequency bands, such as alpha, beta, theta, and delta waves, and their temporal dynamics.

---



<div style="text-align:center;">
    <h1 style="color: blue;">  <strong> Class Distribution  </strong> </h1>
    <a href="https://imgur.com/K9jbfYf"><img src="https://i.imgur.com/K9jbfYf.jpg" title="source: imgur.com" /></a></div>
    
    
   
    
 <p>
    <li>In the class distribution pie chart, the "other" category accounts for 42% of the dataset, while seizures make up 10%, LPD 16%, GPD 11%, LRDA 7.2%, and GRDA 9.4%. This chart helps us understand the proportion of different patterns in the dataset.</li>

<li>For a CNN model, this information is crucial because it guides how the model is trained to recognize different patterns. By knowing the distribution of classes, the model can be trained more effectively to accurately identify seizures and other brain activities.</li>
    <li>To address the imbalance in classification,utilized stratified group k-fold cross-validation ***StratifiedGroupKFold*** from ***sklearn.model_selection***. This method ensures that each fold of the data contains a proportional representation of each class, ensuring fair representation of each class in the training process and helping the model to learn from all classes equally</li>

---


<div style="text-align:center;" >
  <h1 style = "color: blue;">Models Architecture</h1>
    </div>
    
 
  <h1 style = "color: blue;">List of Models:</h1>
  <ul>
    <li>EfficientNetV2-B2</li>
    <li>ResNet50</li>
    <li>EfficientNetV2-B0</li>
  </ul>
<a href="https://imgur.com/7YBE8Wd"><img src="https://i.imgur.com/7YBE8Wd.jpg" title="source: imgur.com" /></a>


* Global Pooling 2D: A pooling operation that reduces the spatial dimensions of the input by taking the maximum or average value over each feature map.
* Dense Layer: A fully connected layer where each neuron is connected to every neuron in the previous layer.
* Kernel Regularization L2 0.01: Regularization technique used to prevent overfitting by penalizing large weights.
* KL Divergence: A measure of how one probability distribution diverges from a second, expected probability distribution, commonly used in probabilistic models.
* Adam Optimizer: An optimization algorithm used for training deep learning models, known for its adaptive learning rate and momentum.

---


<div style="text-align:center;">
  <a href="https://imgur.com/LBRa958">
    <img src="https://i.imgur.com/LBRa958.jpg" title="source: imgur.com" />
  </a>   
</div>


## Model 1: EfficientNetV2B2
### Epochs 1-15:
* Training Accuracy: Ranges from 31.45% to 71.70%
* Training Loss: Decreases from 1.4558 to 0.6863
* Validation Accuracy: Ranges from 46.57% to 68.36%
* Validation Loss: Decreases from 1.4106 to 0.8878

## Model 2: ResNet50
### Epochs 1-15:
* Training Accuracy: Ranges from 33.67% to 74.24%
* Training Loss: Decreases from 1.7303 to 0.6641
* Validation Accuracy: Ranges from 6.33% to 67.32%
* Validation Loss: Increases from 2.0393 to 1.0153

## Model 3: EfficientNetV2B0
### Epochs 1-15:
* Training Accuracy: Ranges from 31.76% to 71.03%
* Training Loss: Decreases from 1.4545 to 0.7109
* Validation Accuracy: Ranges from 46.57% to 66.98%
* Validation Loss: Decreases from 1.4142 to 0.9212

## Analysis:
* All models show an improvement in both training and validation accuracy over the epochs.
* Model 1 and Model 3 exhibit a steady decrease in both training and validation loss, indicating improved performance.
* Model 2, however, shows erratic behavior with a significant increase in validation loss from epochs 1-15, which suggests overfitting.
* Overall, Model 1 and Model 3 appear to perform better compared to Model 2, as they demonstrate a more consistent decrease in loss and increase in accuracy over the epochs.

---



        
