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



        
