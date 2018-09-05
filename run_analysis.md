---
title: "Run_Analytics Code Book"
author: "Joe DeMaro"
date: "September 5, 2018"
output: 
  html_document: default
---

## Purpose

#### The purpose of programming run_analytics.R is to learn how to create a tidy data set(tidydataset) from a large set of data.  The large data set was provided from study called 'Human Activity Recognition Using Smartphones Dataset'.  Each record in the original dataset included  
####1. Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration.
####2. Triaxial Angular velocity from the gyroscope. 
####3. A 561-feature vector with time and frequency domain variables. 
####4. Its activity label. 
####5. An identifier of the subject who carried out the experiment.

#### The larger set was processed by combining the test and training sets of data together maintaining subject and activity identity. Column names were added to describe the different data points collected per record.

#### Data was tidied by cleaning up column names, substituting activity names for identifiers and finally summarizing the data with mean or standard deviation as its metric.


## Variable Description List

|Variable   |  Description|
|---------------| -------------|
|subject        |  ID integer used to signify an individual subject|  
|activity.str   |  Activity name (one of six activities.)   |
|domain| Time vs Frequency - designated by t or f in variable name|
|instrument| the device used to measure - a (accelerometer; acceleration) or g (gyroscope; velocity) in variable|
|calculated variable| mean or standard deviation|
|axis|XYZ direction|
|count|data points to calculate average|
|average|average by variable for each subject and activity|
|magnitude|magnitude of signal|
|jerk|jerk signal|


## Variable Summary


```
## Warning in data(tidydataset): data set 'tidydataset' not found
```

```
##     Subject               activityname.str time.Body.Acc.mean.X
##  Min.   : 1.0   LAYING            :30      Min.   :0.2216      
##  1st Qu.: 8.0   SITTING           :30      1st Qu.:0.2712      
##  Median :15.5   STANDING          :30      Median :0.2770      
##  Mean   :15.5   WALKING           :30      Mean   :0.2743      
##  3rd Qu.:23.0   WALKING_DOWNSTAIRS:30      3rd Qu.:0.2800      
##  Max.   :30.0   WALKING_UPSTAIRS  :30      Max.   :0.3015      
##  time.Body.Acc.mean.Y time.Body.Acc.mean.Z time.Body.Acc.std.X
##  Min.   :-0.040514    Min.   :-0.15251     Min.   :-0.9961    
##  1st Qu.:-0.020022    1st Qu.:-0.11207     1st Qu.:-0.9799    
##  Median :-0.017262    Median :-0.10819     Median :-0.7526    
##  Mean   :-0.017876    Mean   :-0.10916     Mean   :-0.5577    
##  3rd Qu.:-0.014936    3rd Qu.:-0.10443     3rd Qu.:-0.1984    
##  Max.   :-0.001308    Max.   :-0.07538     Max.   : 0.6269    
##  time.Body.Acc.std.Y time.Body.Acc.std.Z time.Gravity.Acc.mean.X
##  Min.   :-0.99024    Min.   :-0.9877     Min.   :-0.6800        
##  1st Qu.:-0.94205    1st Qu.:-0.9498     1st Qu.: 0.8376        
##  Median :-0.50897    Median :-0.6518     Median : 0.9208        
##  Mean   :-0.46046    Mean   :-0.5756     Mean   : 0.6975        
##  3rd Qu.:-0.03077    3rd Qu.:-0.2306     3rd Qu.: 0.9425        
##  Max.   : 0.61694    Max.   : 0.6090     Max.   : 0.9745        
##  time.Gravity.Acc.mean.Y time.Gravity.Acc.mean.Z time.Gravity.Acc.std.X
##  Min.   :-0.47989        Min.   :-0.49509        Min.   :-0.9968       
##  1st Qu.:-0.23319        1st Qu.:-0.11726        1st Qu.:-0.9825       
##  Median :-0.12782        Median : 0.02384        Median :-0.9695       
##  Mean   :-0.01621        Mean   : 0.07413        Mean   :-0.9638       
##  3rd Qu.: 0.08773        3rd Qu.: 0.14946        3rd Qu.:-0.9509       
##  Max.   : 0.95659        Max.   : 0.95787        Max.   :-0.8296       
##  time.Gravity.Acc.std.Y time.Gravity.Acc.std.Z time.Body.AccJerk.mean.X
##  Min.   :-0.9942        Min.   :-0.9910        Min.   :0.04269         
##  1st Qu.:-0.9711        1st Qu.:-0.9605        1st Qu.:0.07396         
##  Median :-0.9590        Median :-0.9450        Median :0.07640         
##  Mean   :-0.9524        Mean   :-0.9364        Mean   :0.07947         
##  3rd Qu.:-0.9370        3rd Qu.:-0.9180        3rd Qu.:0.08330         
##  Max.   :-0.6436        Max.   :-0.6102        Max.   :0.13019         
##  time.Body.AccJerk.mean.Y time.Body.AccJerk.mean.Z time.Body.AccJerk.std.X
##  Min.   :-0.0386872       Min.   :-0.067458        Min.   :-0.9946        
##  1st Qu.: 0.0004664       1st Qu.:-0.010601        1st Qu.:-0.9832        
##  Median : 0.0094698       Median :-0.003861        Median :-0.8104        
##  Mean   : 0.0075652       Mean   :-0.004953        Mean   :-0.5949        
##  3rd Qu.: 0.0134008       3rd Qu.: 0.001958        3rd Qu.:-0.2233        
##  Max.   : 0.0568186       Max.   : 0.038053        Max.   : 0.5443        
##  time.Body.AccJerk.std.Y time.Body.AccJerk.std.Z time.Body.Gyro.mean.X
##  Min.   :-0.9895         Min.   :-0.99329        Min.   :-0.20578     
##  1st Qu.:-0.9724         1st Qu.:-0.98266        1st Qu.:-0.04712     
##  Median :-0.7756         Median :-0.88366        Median :-0.02871     
##  Mean   :-0.5654         Mean   :-0.73596        Mean   :-0.03244     
##  3rd Qu.:-0.1483         3rd Qu.:-0.51212        3rd Qu.:-0.01676     
##  Max.   : 0.3553         Max.   : 0.03102        Max.   : 0.19270     
##  time.Body.Gyro.mean.Y time.Body.Gyro.mean.Z time.Body.Gyro.std.X
##  Min.   :-0.20421      Min.   :-0.07245      Min.   :-0.9943     
##  1st Qu.:-0.08955      1st Qu.: 0.07475      1st Qu.:-0.9735     
##  Median :-0.07318      Median : 0.08512      Median :-0.7890     
##  Mean   :-0.07426      Mean   : 0.08744      Mean   :-0.6916     
##  3rd Qu.:-0.06113      3rd Qu.: 0.10177      3rd Qu.:-0.4414     
##  Max.   : 0.02747      Max.   : 0.17910      Max.   : 0.2677     
##  time.Body.Gyro.std.Y time.Body.Gyro.std.Z time.Body.GyroJerk.mean.X
##  Min.   :-0.9942      Min.   :-0.9855      Min.   :-0.15721         
##  1st Qu.:-0.9629      1st Qu.:-0.9609      1st Qu.:-0.10322         
##  Median :-0.8017      Median :-0.8010      Median :-0.09868         
##  Mean   :-0.6533      Mean   :-0.6164      Mean   :-0.09606         
##  3rd Qu.:-0.4196      3rd Qu.:-0.3106      3rd Qu.:-0.09110         
##  Max.   : 0.4765      Max.   : 0.5649      Max.   :-0.02209         
##  time.Body.GyroJerk.mean.Y time.Body.GyroJerk.mean.Z
##  Min.   :-0.07681          Min.   :-0.092500        
##  1st Qu.:-0.04552          1st Qu.:-0.061725        
##  Median :-0.04112          Median :-0.053430        
##  Mean   :-0.04269          Mean   :-0.054802        
##  3rd Qu.:-0.03842          3rd Qu.:-0.048985        
##  Max.   :-0.01320          Max.   :-0.006941        
##  time.Body.GyroJerk.std.X time.Body.GyroJerk.std.Y
##  Min.   :-0.9965          Min.   :-0.9971         
##  1st Qu.:-0.9800          1st Qu.:-0.9832         
##  Median :-0.8396          Median :-0.8942         
##  Mean   :-0.7036          Mean   :-0.7636         
##  3rd Qu.:-0.4629          3rd Qu.:-0.5861         
##  Max.   : 0.1791          Max.   : 0.2959         
##  time.Body.GyroJerk.std.Z time.Body.AccMag.mean. time.Body.AccMag.std.
##  Min.   :-0.9954          Min.   :-0.9865        Min.   :-0.9865      
##  1st Qu.:-0.9848          1st Qu.:-0.9573        1st Qu.:-0.9430      
##  Median :-0.8610          Median :-0.4829        Median :-0.6074      
##  Mean   :-0.7096          Mean   :-0.4973        Mean   :-0.5439      
##  3rd Qu.:-0.4741          3rd Qu.:-0.0919        3rd Qu.:-0.2090      
##  Max.   : 0.1932          Max.   : 0.6446        Max.   : 0.4284      
##  time.Gravity.AccMag.mean. time.Gravity.AccMag.std.
##  Min.   :-0.9865           Min.   :-0.9865         
##  1st Qu.:-0.9573           1st Qu.:-0.9430         
##  Median :-0.4829           Median :-0.6074         
##  Mean   :-0.4973           Mean   :-0.5439         
##  3rd Qu.:-0.0919           3rd Qu.:-0.2090         
##  Max.   : 0.6446           Max.   : 0.4284         
##  time.Body.AccJerkMag.mean. time.Body.AccJerkMag.std.
##  Min.   :-0.9928            Min.   :-0.9946          
##  1st Qu.:-0.9807            1st Qu.:-0.9765          
##  Median :-0.8168            Median :-0.8014          
##  Mean   :-0.6079            Mean   :-0.5842          
##  3rd Qu.:-0.2456            3rd Qu.:-0.2173          
##  Max.   : 0.4345            Max.   : 0.4506          
##  time.Body.GyroMag.mean. time.Body.GyroMag.std.
##  Min.   :-0.9807         Min.   :-0.9814       
##  1st Qu.:-0.9461         1st Qu.:-0.9476       
##  Median :-0.6551         Median :-0.7420       
##  Mean   :-0.5652         Mean   :-0.6304       
##  3rd Qu.:-0.2159         3rd Qu.:-0.3602       
##  Max.   : 0.4180         Max.   : 0.3000       
##  time.Body.GyroJerkMag.mean. time.Body.GyroJerkMag.std.
##  Min.   :-0.99732            Min.   :-0.9977           
##  1st Qu.:-0.98515            1st Qu.:-0.9805           
##  Median :-0.86479            Median :-0.8809           
##  Mean   :-0.73637            Mean   :-0.7550           
##  3rd Qu.:-0.51186            3rd Qu.:-0.5767           
##  Max.   : 0.08758            Max.   : 0.2502           
##  freq.Body.Acc.mean.X freq.Body.Acc.mean.Y freq.Body.Acc.mean.Z
##  Min.   :-0.9952      Min.   :-0.98903     Min.   :-0.9895     
##  1st Qu.:-0.9787      1st Qu.:-0.95361     1st Qu.:-0.9619     
##  Median :-0.7691      Median :-0.59498     Median :-0.7236     
##  Mean   :-0.5758      Mean   :-0.48873     Mean   :-0.6297     
##  3rd Qu.:-0.2174      3rd Qu.:-0.06341     3rd Qu.:-0.3183     
##  Max.   : 0.5370      Max.   : 0.52419     Max.   : 0.2807     
##  freq.Body.Acc.std.X freq.Body.Acc.std.Y freq.Body.Acc.std.Z
##  Min.   :-0.9966     Min.   :-0.99068    Min.   :-0.9872    
##  1st Qu.:-0.9820     1st Qu.:-0.94042    1st Qu.:-0.9459    
##  Median :-0.7470     Median :-0.51338    Median :-0.6441    
##  Mean   :-0.5522     Mean   :-0.48148    Mean   :-0.5824    
##  3rd Qu.:-0.1966     3rd Qu.:-0.07913    3rd Qu.:-0.2655    
##  Max.   : 0.6585     Max.   : 0.56019    Max.   : 0.6871    
##  freq.Body.Acc.mean.FreqX freq.Body.Acc.mean.FreqY
##  Min.   :-0.63591         Min.   :-0.379518       
##  1st Qu.:-0.39165         1st Qu.:-0.081314       
##  Median :-0.25731         Median : 0.007855       
##  Mean   :-0.23227         Mean   : 0.011529       
##  3rd Qu.:-0.06105         3rd Qu.: 0.086281       
##  Max.   : 0.15912         Max.   : 0.466528       
##  freq.Body.Acc.mean.FreqZ freq.Body.AccJerk.mean.X
##  Min.   :-0.52011         Min.   :-0.9946         
##  1st Qu.:-0.03629         1st Qu.:-0.9828         
##  Median : 0.06582         Median :-0.8126         
##  Mean   : 0.04372         Mean   :-0.6139         
##  3rd Qu.: 0.17542         3rd Qu.:-0.2820         
##  Max.   : 0.40253         Max.   : 0.4743         
##  freq.Body.AccJerk.mean.Y freq.Body.AccJerk.mean.Z freq.Body.AccJerk.std.X
##  Min.   :-0.9894          Min.   :-0.9920          Min.   :-0.9951        
##  1st Qu.:-0.9725          1st Qu.:-0.9796          1st Qu.:-0.9847        
##  Median :-0.7817          Median :-0.8707          Median :-0.8254        
##  Mean   :-0.5882          Mean   :-0.7144          Mean   :-0.6121        
##  3rd Qu.:-0.1963          3rd Qu.:-0.4697          3rd Qu.:-0.2475        
##  Max.   : 0.2767          Max.   : 0.1578          Max.   : 0.4768        
##  freq.Body.AccJerk.std.Y freq.Body.AccJerk.std.Z
##  Min.   :-0.9905         Min.   :-0.993108      
##  1st Qu.:-0.9737         1st Qu.:-0.983747      
##  Median :-0.7852         Median :-0.895121      
##  Mean   :-0.5707         Mean   :-0.756489      
##  3rd Qu.:-0.1685         3rd Qu.:-0.543787      
##  Max.   : 0.3498         Max.   :-0.006236      
##  freq.Body.AccJerk.mean.FreqX freq.Body.AccJerk.mean.FreqY
##  Min.   :-0.57604             Min.   :-0.60197            
##  1st Qu.:-0.28966             1st Qu.:-0.39751            
##  Median :-0.06091             Median :-0.23209            
##  Mean   :-0.06910             Mean   :-0.22810            
##  3rd Qu.: 0.17660             3rd Qu.:-0.04721            
##  Max.   : 0.33145             Max.   : 0.19568            
##  freq.Body.AccJerk.mean.FreqZ freq.Body.Gyro.mean.X freq.Body.Gyro.mean.Y
##  Min.   :-0.62756             Min.   :-0.9931       Min.   :-0.9940      
##  1st Qu.:-0.30867             1st Qu.:-0.9697       1st Qu.:-0.9700      
##  Median :-0.09187             Median :-0.7300       Median :-0.8141      
##  Mean   :-0.13760             Mean   :-0.6367       Mean   :-0.6767      
##  3rd Qu.: 0.03858             3rd Qu.:-0.3387       3rd Qu.:-0.4458      
##  Max.   : 0.23011             Max.   : 0.4750       Max.   : 0.3288      
##  freq.Body.Gyro.mean.Z freq.Body.Gyro.std.X freq.Body.Gyro.std.Y
##  Min.   :-0.9860       Min.   :-0.9947      Min.   :-0.9944     
##  1st Qu.:-0.9624       1st Qu.:-0.9750      1st Qu.:-0.9602     
##  Median :-0.7909       Median :-0.8086      Median :-0.7964     
##  Mean   :-0.6044       Mean   :-0.7110      Mean   :-0.6454     
##  3rd Qu.:-0.2635       3rd Qu.:-0.4813      3rd Qu.:-0.4154     
##  Max.   : 0.4924       Max.   : 0.1966      Max.   : 0.6462     
##  freq.Body.Gyro.std.Z freq.Body.Gyro.mean.FreqX freq.Body.Gyro.mean.FreqY
##  Min.   :-0.9867      Min.   :-0.395770         Min.   :-0.66681         
##  1st Qu.:-0.9643      1st Qu.:-0.213363         1st Qu.:-0.29433         
##  Median :-0.8224      Median :-0.115527         Median :-0.15794         
##  Mean   :-0.6577      Mean   :-0.104551         Mean   :-0.16741         
##  3rd Qu.:-0.3916      3rd Qu.: 0.002655         3rd Qu.:-0.04269         
##  Max.   : 0.5225      Max.   : 0.249209         Max.   : 0.27314         
##  freq.Body.Gyro.mean.FreqZ freq.Body.AccMag.mean. freq.Body.AccMag.std.
##  Min.   :-0.50749          Min.   :-0.9868        Min.   :-0.9876      
##  1st Qu.:-0.15481          1st Qu.:-0.9560        1st Qu.:-0.9452      
##  Median :-0.05081          Median :-0.6703        Median :-0.6513      
##  Mean   :-0.05718          Mean   :-0.5365        Mean   :-0.6210      
##  3rd Qu.: 0.04152          3rd Qu.:-0.1622        3rd Qu.:-0.3654      
##  Max.   : 0.37707          Max.   : 0.5866        Max.   : 0.1787      
##  freq.Body.AccMag.mean.Freq freq.Body.BodyAccJerkMag.mean.
##  Min.   :-0.31234           Min.   :-0.9940               
##  1st Qu.:-0.01475           1st Qu.:-0.9770               
##  Median : 0.08132           Median :-0.7940               
##  Mean   : 0.07613           Mean   :-0.5756               
##  3rd Qu.: 0.17436           3rd Qu.:-0.1872               
##  Max.   : 0.43585           Max.   : 0.5384               
##  freq.Body.BodyAccJerkMag.std. freq.Body.BodyAccJerkMag.mean.Freq
##  Min.   :-0.9944               Min.   :-0.12521                  
##  1st Qu.:-0.9752               1st Qu.: 0.04527                  
##  Median :-0.8126               Median : 0.17198                  
##  Mean   :-0.5992               Mean   : 0.16255                  
##  3rd Qu.:-0.2668               3rd Qu.: 0.27593                  
##  Max.   : 0.3163               Max.   : 0.48809                  
##  freq.Body.BodyGyroMag.mean. freq.Body.BodyGyroMag.std.
##  Min.   :-0.9865             Min.   :-0.9815           
##  1st Qu.:-0.9616             1st Qu.:-0.9488           
##  Median :-0.7657             Median :-0.7727           
##  Mean   :-0.6671             Mean   :-0.6723           
##  3rd Qu.:-0.4087             3rd Qu.:-0.4277           
##  Max.   : 0.2040             Max.   : 0.2367           
##  freq.Body.BodyGyroMag.mean.Freq freq.Body.BodyGyroJerkMag.mean.
##  Min.   :-0.45664                Min.   :-0.9976                
##  1st Qu.:-0.16951                1st Qu.:-0.9813                
##  Median :-0.05352                Median :-0.8779                
##  Mean   :-0.03603                Mean   :-0.7564                
##  3rd Qu.: 0.08228                3rd Qu.:-0.5831                
##  Max.   : 0.40952                Max.   : 0.1466                
##  freq.Body.BodyGyroJerkMag.std. freq.Body.BodyGyroJerkMag.mean.Freq
##  Min.   :-0.9976                Min.   :-0.18292                   
##  1st Qu.:-0.9802                1st Qu.: 0.05423                   
##  Median :-0.8941                Median : 0.11156                   
##  Mean   :-0.7715                Mean   : 0.12592                   
##  3rd Qu.:-0.6081                3rd Qu.: 0.20805                   
##  Max.   : 0.2878                Max.   : 0.42630                   
##  angletime.Body.AccMean,gravity angletime.Body.AccJerkMean,gravityMean
##  Min.   :-0.163043              Min.   :-0.1205540                    
##  1st Qu.:-0.011012              1st Qu.:-0.0211694                    
##  Median : 0.007878              Median : 0.0031358                    
##  Mean   : 0.006556              Mean   : 0.0006439                    
##  3rd Qu.: 0.024393              3rd Qu.: 0.0220881                    
##  Max.   : 0.129154              Max.   : 0.2032600                    
##  angletime.Body.GyroMean,gravityMean
##  Min.   :-0.38931                   
##  1st Qu.:-0.01977                   
##  Median : 0.02087                   
##  Mean   : 0.02193                   
##  3rd Qu.: 0.06460                   
##  Max.   : 0.44410                   
##  angletime.Body.GyroJerkMean,gravityMean angleX,gravityMean
##  Min.   :-0.22367                        Min.   :-0.9471   
##  1st Qu.:-0.05613                        1st Qu.:-0.7907   
##  Median :-0.01602                        Median :-0.7377   
##  Mean   :-0.01137                        Mean   :-0.5243   
##  3rd Qu.: 0.03200                        3rd Qu.:-0.5823   
##  Max.   : 0.18238                        Max.   : 0.7378   
##  angleY,gravityMean angleZ,gravityMean 
##  Min.   :-0.87457   Min.   :-0.873649  
##  1st Qu.: 0.02191   1st Qu.:-0.083912  
##  Median : 0.17136   Median : 0.005079  
##  Mean   : 0.07865   Mean   :-0.040436  
##  3rd Qu.: 0.24343   3rd Qu.: 0.106190  
##  Max.   : 0.42476   Max.   : 0.390444
```

## Sample rows from Tidy data set

```
##   Subject   activityname.str time.Body.Acc.mean.X time.Body.Acc.mean.Y
## 1       1             LAYING            0.2215982         -0.040513953
## 2       1            SITTING            0.2612376         -0.001308288
## 3       1           STANDING            0.2789176         -0.016137590
## 4       1            WALKING            0.2773308         -0.017383819
## 5       1 WALKING_DOWNSTAIRS            0.2891883         -0.009918505
## 6       1   WALKING_UPSTAIRS            0.2554617         -0.023953149
##   time.Body.Acc.mean.Z time.Body.Acc.std.X time.Body.Acc.std.Y
## 1           -0.1132036         -0.92805647        -0.836827406
## 2           -0.1045442         -0.97722901        -0.922618642
## 3           -0.1106018         -0.99575990        -0.973190056
## 4           -0.1111481         -0.28374026         0.114461337
## 5           -0.1075662          0.03003534        -0.031935943
## 6           -0.0973020         -0.35470803        -0.002320265
##   time.Body.Acc.std.Z time.Gravity.Acc.mean.X time.Gravity.Acc.mean.Y
## 1         -0.82606140              -0.2488818               0.7055498
## 2         -0.93958629               0.8315099               0.2044116
## 3         -0.97977588               0.9429520              -0.2729838
## 4         -0.26002790               0.9352232              -0.2821650
## 5         -0.23043421               0.9318744              -0.2666103
## 6         -0.01947924               0.8933511              -0.3621534
##   time.Gravity.Acc.mean.Z time.Gravity.Acc.std.X time.Gravity.Acc.std.Y
## 1              0.44581772             -0.8968300             -0.9077200
## 2              0.33204370             -0.9684571             -0.9355171
## 3              0.01349058             -0.9937630             -0.9812260
## 4             -0.06810286             -0.9766096             -0.9713060
## 5             -0.06211996             -0.9505598             -0.9370187
## 6             -0.07540294             -0.9563670             -0.9528492
##   time.Gravity.Acc.std.Z time.Body.AccJerk.mean.X time.Body.AccJerk.mean.Y
## 1             -0.8523663               0.08108653             0.0038382040
## 2             -0.9490409               0.07748252            -0.0006191028
## 3             -0.9763241               0.07537665             0.0079757309
## 4             -0.9477172               0.07404163             0.0282721096
## 5             -0.8959397               0.05415532             0.0296504490
## 6             -0.9123794               0.10137273             0.0194863076
##   time.Body.AccJerk.mean.Z time.Body.AccJerk.std.X time.Body.AccJerk.std.Y
## 1              0.010834236             -0.95848211              -0.9241493
## 2             -0.003367792             -0.98643071              -0.9813720
## 3             -0.003685250             -0.99460454              -0.9856487
## 4             -0.004168406             -0.11361560               0.0670025
## 5             -0.010971973             -0.01228386              -0.1016014
## 6             -0.045562545             -0.44684389              -0.3782744
##   time.Body.AccJerk.std.Z time.Body.Gyro.mean.X time.Body.Gyro.mean.Y
## 1              -0.9548551           -0.01655309           -0.06448612
## 2              -0.9879108           -0.04535006           -0.09192415
## 3              -0.9922512           -0.02398773           -0.05939722
## 4              -0.5026998           -0.04183096           -0.06953005
## 5              -0.3457350           -0.03507819           -0.09093713
## 6              -0.7065935            0.05054938           -0.16617002
##   time.Body.Gyro.mean.Z time.Body.Gyro.std.X time.Body.Gyro.std.Y
## 1            0.14868944           -0.8735439         -0.951090440
## 2            0.06293138           -0.9772113         -0.966473895
## 3            0.07480075           -0.9871919         -0.987734440
## 4            0.08494482           -0.4735355         -0.054607769
## 5            0.09008501           -0.4580305         -0.126349195
## 6            0.05835955           -0.5448711          0.004105184
##   time.Body.Gyro.std.Z time.Body.GyroJerk.mean.X time.Body.GyroJerk.mean.Y
## 1           -0.9082847               -0.10727095               -0.04151729
## 2           -0.9414259               -0.09367938               -0.04021181
## 3           -0.9806456               -0.09960921               -0.04406279
## 4           -0.3442666               -0.08999754               -0.03984287
## 5           -0.1247025               -0.07395920               -0.04399028
## 6           -0.5071687               -0.12223277               -0.04214859
##   time.Body.GyroJerk.mean.Z time.Body.GyroJerk.std.X
## 1               -0.07405012               -0.9186085
## 2               -0.04670263               -0.9917316
## 3               -0.04895055               -0.9929451
## 4               -0.04613093               -0.2074219
## 5               -0.02704611               -0.4870273
## 6               -0.04071255               -0.6147865
##   time.Body.GyroJerk.std.Y time.Body.GyroJerk.std.Z time.Body.AccMag.mean.
## 1               -0.9679072               -0.9577902            -0.84192915
## 2               -0.9895181               -0.9879358            -0.94853679
## 3               -0.9951379               -0.9921085            -0.98427821
## 4               -0.3044685               -0.4042555            -0.13697118
## 5               -0.2388248               -0.2687615             0.02718829
## 6               -0.6016967               -0.6063320            -0.12992763
##   time.Body.AccMag.std. time.Gravity.AccMag.mean. time.Gravity.AccMag.std.
## 1           -0.79514486               -0.84192915              -0.79514486
## 2           -0.92707842               -0.94853679              -0.92707842
## 3           -0.98194293               -0.98427821              -0.98194293
## 4           -0.21968865               -0.13697118              -0.21968865
## 5            0.01988435                0.02718829               0.01988435
## 6           -0.32497093               -0.12992763              -0.32497093
##   time.Body.AccJerkMag.mean. time.Body.AccJerkMag.std.
## 1                -0.95439626               -0.92824563
## 2                -0.98736420               -0.98412002
## 3                -0.99236779               -0.99309621
## 4                -0.14142881               -0.07447175
## 5                -0.08944748               -0.02578772
## 6                -0.46650345               -0.47899162
##   time.Body.GyroMag.mean. time.Body.GyroMag.std.
## 1             -0.87475955             -0.8190102
## 2             -0.93089249             -0.9345318
## 3             -0.97649379             -0.9786900
## 4             -0.16097955             -0.1869784
## 5             -0.07574125             -0.2257244
## 6             -0.12673559             -0.1486193
##   time.Body.GyroJerkMag.mean. time.Body.GyroJerkMag.std.
## 1                  -0.9634610                 -0.9358410
## 2                  -0.9919763                 -0.9883087
## 3                  -0.9949668                 -0.9947332
## 4                  -0.2987037                 -0.3253249
## 5                  -0.2954638                 -0.3065106
## 6                  -0.5948829                 -0.6485530
##   freq.Body.Acc.mean.X freq.Body.Acc.mean.Y freq.Body.Acc.mean.Z
## 1          -0.93909905         -0.867065205           -0.8826669
## 2          -0.97964124         -0.944084550           -0.9591849
## 3          -0.99524993         -0.977070848           -0.9852971
## 4          -0.20279431          0.089712726           -0.3315601
## 5           0.03822918          0.001549908           -0.2255745
## 6          -0.40432178         -0.190976721           -0.4333497
##   freq.Body.Acc.std.X freq.Body.Acc.std.Y freq.Body.Acc.std.Z
## 1         -0.92443743         -0.83362556         -0.81289156
## 2         -0.97641231         -0.91727501         -0.93446956
## 3         -0.99602835         -0.97229310         -0.97793726
## 4         -0.31913472          0.05604001         -0.27968675
## 5          0.02433084         -0.11296374         -0.29792789
## 6         -0.33742819          0.02176951          0.08595655
##   freq.Body.Acc.mean.FreqX freq.Body.Acc.mean.FreqY
## 1              -0.15879267               0.09753484
## 2              -0.04951360               0.07594608
## 3               0.08651536               0.11747895
## 4              -0.20754837               0.11309365
## 5              -0.30739520               0.06322008
## 6              -0.41873500              -0.16069721
##   freq.Body.Acc.mean.FreqZ freq.Body.AccJerk.mean.X
## 1               0.08943766              -0.95707388
## 2               0.23882987              -0.98659702
## 3               0.24485859              -0.99463080
## 4               0.04972652              -0.17054696
## 5               0.29432270              -0.02766387
## 6              -0.52011479              -0.47987525
##   freq.Body.AccJerk.mean.Y freq.Body.AccJerk.mean.Z
## 1              -0.92246261               -0.9480609
## 2              -0.98157947               -0.9860531
## 3              -0.98541870               -0.9907522
## 4              -0.03522552               -0.4689992
## 5              -0.12866716               -0.2883347
## 6              -0.41344459               -0.6854744
##   freq.Body.AccJerk.std.X freq.Body.AccJerk.std.Y freq.Body.AccJerk.std.Z
## 1              -0.9641607              -0.9322179              -0.9605870
## 2              -0.9874930              -0.9825139              -0.9883392
## 3              -0.9950738              -0.9870182              -0.9923498
## 4              -0.1335866               0.1067399              -0.5347134
## 5              -0.0863279              -0.1345800              -0.4017215
## 6              -0.4619070              -0.3817771              -0.7260402
##   freq.Body.AccJerk.mean.FreqX freq.Body.AccJerk.mean.FreqY
## 1                    0.1324191                   0.02451362
## 2                    0.2566108                   0.04754378
## 3                    0.3141829                   0.03916190
## 4                   -0.2092620                  -0.38623714
## 5                   -0.2531643                  -0.33758970
## 6                   -0.3770231                  -0.50949553
##   freq.Body.AccJerk.mean.FreqZ freq.Body.Gyro.mean.X freq.Body.Gyro.mean.Y
## 1                  0.024387945            -0.8502492           -0.95219149
## 2                  0.092392003            -0.9761615           -0.97583859
## 3                  0.138581479            -0.9863868           -0.98898446
## 4                 -0.185530281            -0.3390322           -0.10305942
## 5                  0.009372239            -0.3524496           -0.05570225
## 6                 -0.551104284            -0.4926117           -0.31947461
##   freq.Body.Gyro.mean.Z freq.Body.Gyro.std.X freq.Body.Gyro.std.Y
## 1           -0.90930272           -0.8822965          -0.95123205
## 2           -0.95131554           -0.9779042          -0.96234504
## 3           -0.98077312           -0.9874971          -0.98710773
## 4           -0.25594094           -0.5166919          -0.03350816
## 5           -0.03186943           -0.4954225          -0.18141473
## 6           -0.45359721           -0.5658925           0.15153891
##   freq.Body.Gyro.std.Z freq.Body.Gyro.mean.FreqX freq.Body.Gyro.mean.FreqY
## 1           -0.9165825              -0.003546796               -0.09152913
## 2           -0.9439178               0.189153021                0.06312707
## 3           -0.9823453              -0.120293021               -0.04471920
## 4           -0.4365622               0.014784499               -0.06577462
## 5           -0.2384436              -0.100453729                0.08255115
## 6           -0.5717078              -0.187450248               -0.47357479
##   freq.Body.Gyro.mean.FreqZ freq.Body.AccMag.mean. freq.Body.AccMag.std.
## 1              0.0104581257            -0.86176765            -0.7983009
## 2             -0.0297839207            -0.94778292            -0.9284448
## 3              0.1006076351            -0.98535636            -0.9823138
## 4              0.0007733216            -0.12862345            -0.3980326
## 5             -0.0756762068             0.09658453            -0.1865303
## 6             -0.1333739043            -0.35239594            -0.4162601
##   freq.Body.AccMag.mean.Freq freq.Body.BodyAccJerkMag.mean.
## 1                 0.08640856                    -0.93330036
## 2                 0.23665501                    -0.98526213
## 3                 0.28455529                    -0.99254248
## 4                 0.19064372                    -0.05711940
## 5                 0.11918714                     0.02621849
## 6                -0.09774335                    -0.44265216
##   freq.Body.BodyAccJerkMag.std. freq.Body.BodyAccJerkMag.mean.Freq
## 1                    -0.9218040                         0.26639115
## 2                    -0.9816062                         0.35185220
## 3                    -0.9925360                         0.42222010
## 4                    -0.1034924                         0.09382218
## 5                    -0.1040523                         0.07649155
## 6                    -0.5330599                         0.08535241
##   freq.Body.BodyGyroMag.mean. freq.Body.BodyGyroMag.std.
## 1                  -0.8621902                 -0.8243194
## 2                  -0.9584356                 -0.9321984
## 3                  -0.9846176                 -0.9784661
## 4                  -0.1992526                 -0.3210180
## 5                  -0.1857203                 -0.3983504
## 6                  -0.3259615                 -0.1829855
##   freq.Body.BodyGyroMag.mean.Freq freq.Body.BodyGyroJerkMag.mean.
## 1                   -0.1397750127                      -0.9423669
## 2                   -0.0002621867                      -0.9897975
## 3                   -0.0286057725                      -0.9948154
## 4                    0.2688443675                      -0.3193086
## 5                    0.3496138955                      -0.2819634
## 6                   -0.2193033761                      -0.6346651
##   freq.Body.BodyGyroJerkMag.std. freq.Body.BodyGyroJerkMag.mean.Freq
## 1                     -0.9326607                           0.1764859
## 2                     -0.9870496                           0.1847759
## 3                     -0.9946711                           0.3344987
## 4                     -0.3816019                           0.1906634
## 5                     -0.3919199                           0.1900007
## 6                     -0.6939305                           0.1142773
##   angletime.Body.AccMean,gravity angletime.Body.AccJerkMean,gravityMean
## 1                   0.0213659656                            0.003060407
## 2                   0.0274415479                            0.029709788
## 3                  -0.0002223407                            0.021963783
## 4                   0.0604537474                           -0.007930378
## 5                  -0.0026951252                            0.089931687
## 6                   0.0960860762                           -0.061083841
##   angletime.Body.GyroMean,gravityMean
## 1                        -0.001666985
## 2                         0.067698134
## 3                        -0.033793838
## 4                         0.013059491
## 5                         0.063338285
## 6                        -0.194699963
##   angletime.Body.GyroJerkMean,gravityMean angleX,gravityMean
## 1                              0.08443716          0.4267062
## 2                             -0.06488162         -0.5912475
## 3                             -0.02792293         -0.7434079
## 4                             -0.01874319         -0.7292472
## 5                             -0.03997685         -0.7444838
## 6                              0.06568357         -0.6471957
##   angleY,gravityMean angleZ,gravityMean
## 1        -0.52034382        -0.35241311
## 2        -0.06046603        -0.21801723
## 3         0.27017503         0.01225285
## 4         0.27695302         0.06885891
## 5         0.26724578         0.06500471
## 6         0.33476328         0.07416637
```

## Key variables

## Data Structure of Tidy data set

```
## Classes 'grouped_df', 'tbl_df', 'tbl' and 'data.frame':	180 obs. of  88 variables:
##  $ Subject                                : int  1 1 1 1 1 1 2 2 2 2 ...
##  $ activityname.str                       : Factor w/ 6 levels "LAYING","SITTING",..: 1 2 3 4 5 6 1 2 3 4 ...
##  $ time.Body.Acc.mean.X                   : num  0.222 0.261 0.279 0.277 0.289 ...
##  $ time.Body.Acc.mean.Y                   : num  -0.04051 -0.00131 -0.01614 -0.01738 -0.00992 ...
##  $ time.Body.Acc.mean.Z                   : num  -0.113 -0.105 -0.111 -0.111 -0.108 ...
##  $ time.Body.Acc.std.X                    : num  -0.928 -0.977 -0.996 -0.284 0.03 ...
##  $ time.Body.Acc.std.Y                    : num  -0.8368 -0.9226 -0.9732 0.1145 -0.0319 ...
##  $ time.Body.Acc.std.Z                    : num  -0.826 -0.94 -0.98 -0.26 -0.23 ...
##  $ time.Gravity.Acc.mean.X                : num  -0.249 0.832 0.943 0.935 0.932 ...
##  $ time.Gravity.Acc.mean.Y                : num  0.706 0.204 -0.273 -0.282 -0.267 ...
##  $ time.Gravity.Acc.mean.Z                : num  0.4458 0.332 0.0135 -0.0681 -0.0621 ...
##  $ time.Gravity.Acc.std.X                 : num  -0.897 -0.968 -0.994 -0.977 -0.951 ...
##  $ time.Gravity.Acc.std.Y                 : num  -0.908 -0.936 -0.981 -0.971 -0.937 ...
##  $ time.Gravity.Acc.std.Z                 : num  -0.852 -0.949 -0.976 -0.948 -0.896 ...
##  $ time.Body.AccJerk.mean.X               : num  0.0811 0.0775 0.0754 0.074 0.0542 ...
##  $ time.Body.AccJerk.mean.Y               : num  0.003838 -0.000619 0.007976 0.028272 0.02965 ...
##  $ time.Body.AccJerk.mean.Z               : num  0.01083 -0.00337 -0.00369 -0.00417 -0.01097 ...
##  $ time.Body.AccJerk.std.X                : num  -0.9585 -0.9864 -0.9946 -0.1136 -0.0123 ...
##  $ time.Body.AccJerk.std.Y                : num  -0.924 -0.981 -0.986 0.067 -0.102 ...
##  $ time.Body.AccJerk.std.Z                : num  -0.955 -0.988 -0.992 -0.503 -0.346 ...
##  $ time.Body.Gyro.mean.X                  : num  -0.0166 -0.0454 -0.024 -0.0418 -0.0351 ...
##  $ time.Body.Gyro.mean.Y                  : num  -0.0645 -0.0919 -0.0594 -0.0695 -0.0909 ...
##  $ time.Body.Gyro.mean.Z                  : num  0.1487 0.0629 0.0748 0.0849 0.0901 ...
##  $ time.Body.Gyro.std.X                   : num  -0.874 -0.977 -0.987 -0.474 -0.458 ...
##  $ time.Body.Gyro.std.Y                   : num  -0.9511 -0.9665 -0.9877 -0.0546 -0.1263 ...
##  $ time.Body.Gyro.std.Z                   : num  -0.908 -0.941 -0.981 -0.344 -0.125 ...
##  $ time.Body.GyroJerk.mean.X              : num  -0.1073 -0.0937 -0.0996 -0.09 -0.074 ...
##  $ time.Body.GyroJerk.mean.Y              : num  -0.0415 -0.0402 -0.0441 -0.0398 -0.044 ...
##  $ time.Body.GyroJerk.mean.Z              : num  -0.0741 -0.0467 -0.049 -0.0461 -0.027 ...
##  $ time.Body.GyroJerk.std.X               : num  -0.919 -0.992 -0.993 -0.207 -0.487 ...
##  $ time.Body.GyroJerk.std.Y               : num  -0.968 -0.99 -0.995 -0.304 -0.239 ...
##  $ time.Body.GyroJerk.std.Z               : num  -0.958 -0.988 -0.992 -0.404 -0.269 ...
##  $ time.Body.AccMag.mean.                 : num  -0.8419 -0.9485 -0.9843 -0.137 0.0272 ...
##  $ time.Body.AccMag.std.                  : num  -0.7951 -0.9271 -0.9819 -0.2197 0.0199 ...
##  $ time.Gravity.AccMag.mean.              : num  -0.8419 -0.9485 -0.9843 -0.137 0.0272 ...
##  $ time.Gravity.AccMag.std.               : num  -0.7951 -0.9271 -0.9819 -0.2197 0.0199 ...
##  $ time.Body.AccJerkMag.mean.             : num  -0.9544 -0.9874 -0.9924 -0.1414 -0.0894 ...
##  $ time.Body.AccJerkMag.std.              : num  -0.9282 -0.9841 -0.9931 -0.0745 -0.0258 ...
##  $ time.Body.GyroMag.mean.                : num  -0.8748 -0.9309 -0.9765 -0.161 -0.0757 ...
##  $ time.Body.GyroMag.std.                 : num  -0.819 -0.935 -0.979 -0.187 -0.226 ...
##  $ time.Body.GyroJerkMag.mean.            : num  -0.963 -0.992 -0.995 -0.299 -0.295 ...
##  $ time.Body.GyroJerkMag.std.             : num  -0.936 -0.988 -0.995 -0.325 -0.307 ...
##  $ freq.Body.Acc.mean.X                   : num  -0.9391 -0.9796 -0.9952 -0.2028 0.0382 ...
##  $ freq.Body.Acc.mean.Y                   : num  -0.86707 -0.94408 -0.97707 0.08971 0.00155 ...
##  $ freq.Body.Acc.mean.Z                   : num  -0.883 -0.959 -0.985 -0.332 -0.226 ...
##  $ freq.Body.Acc.std.X                    : num  -0.9244 -0.9764 -0.996 -0.3191 0.0243 ...
##  $ freq.Body.Acc.std.Y                    : num  -0.834 -0.917 -0.972 0.056 -0.113 ...
##  $ freq.Body.Acc.std.Z                    : num  -0.813 -0.934 -0.978 -0.28 -0.298 ...
##  $ freq.Body.Acc.mean.FreqX               : num  -0.1588 -0.0495 0.0865 -0.2075 -0.3074 ...
##  $ freq.Body.Acc.mean.FreqY               : num  0.0975 0.0759 0.1175 0.1131 0.0632 ...
##  $ freq.Body.Acc.mean.FreqZ               : num  0.0894 0.2388 0.2449 0.0497 0.2943 ...
##  $ freq.Body.AccJerk.mean.X               : num  -0.9571 -0.9866 -0.9946 -0.1705 -0.0277 ...
##  $ freq.Body.AccJerk.mean.Y               : num  -0.9225 -0.9816 -0.9854 -0.0352 -0.1287 ...
##  $ freq.Body.AccJerk.mean.Z               : num  -0.948 -0.986 -0.991 -0.469 -0.288 ...
##  $ freq.Body.AccJerk.std.X                : num  -0.9642 -0.9875 -0.9951 -0.1336 -0.0863 ...
##  $ freq.Body.AccJerk.std.Y                : num  -0.932 -0.983 -0.987 0.107 -0.135 ...
##  $ freq.Body.AccJerk.std.Z                : num  -0.961 -0.988 -0.992 -0.535 -0.402 ...
##  $ freq.Body.AccJerk.mean.FreqX           : num  0.132 0.257 0.314 -0.209 -0.253 ...
##  $ freq.Body.AccJerk.mean.FreqY           : num  0.0245 0.0475 0.0392 -0.3862 -0.3376 ...
##  $ freq.Body.AccJerk.mean.FreqZ           : num  0.02439 0.09239 0.13858 -0.18553 0.00937 ...
##  $ freq.Body.Gyro.mean.X                  : num  -0.85 -0.976 -0.986 -0.339 -0.352 ...
##  $ freq.Body.Gyro.mean.Y                  : num  -0.9522 -0.9758 -0.989 -0.1031 -0.0557 ...
##  $ freq.Body.Gyro.mean.Z                  : num  -0.9093 -0.9513 -0.9808 -0.2559 -0.0319 ...
##  $ freq.Body.Gyro.std.X                   : num  -0.882 -0.978 -0.987 -0.517 -0.495 ...
##  $ freq.Body.Gyro.std.Y                   : num  -0.9512 -0.9623 -0.9871 -0.0335 -0.1814 ...
##  $ freq.Body.Gyro.std.Z                   : num  -0.917 -0.944 -0.982 -0.437 -0.238 ...
##  $ freq.Body.Gyro.mean.FreqX              : num  -0.00355 0.18915 -0.12029 0.01478 -0.10045 ...
##  $ freq.Body.Gyro.mean.FreqY              : num  -0.0915 0.0631 -0.0447 -0.0658 0.0826 ...
##  $ freq.Body.Gyro.mean.FreqZ              : num  0.010458 -0.029784 0.100608 0.000773 -0.075676 ...
##  $ freq.Body.AccMag.mean.                 : num  -0.8618 -0.9478 -0.9854 -0.1286 0.0966 ...
##  $ freq.Body.AccMag.std.                  : num  -0.798 -0.928 -0.982 -0.398 -0.187 ...
##  $ freq.Body.AccMag.mean.Freq             : num  0.0864 0.2367 0.2846 0.1906 0.1192 ...
##  $ freq.Body.BodyAccJerkMag.mean.         : num  -0.9333 -0.9853 -0.9925 -0.0571 0.0262 ...
##  $ freq.Body.BodyAccJerkMag.std.          : num  -0.922 -0.982 -0.993 -0.103 -0.104 ...
##  $ freq.Body.BodyAccJerkMag.mean.Freq     : num  0.2664 0.3519 0.4222 0.0938 0.0765 ...
##  $ freq.Body.BodyGyroMag.mean.            : num  -0.862 -0.958 -0.985 -0.199 -0.186 ...
##  $ freq.Body.BodyGyroMag.std.             : num  -0.824 -0.932 -0.978 -0.321 -0.398 ...
##  $ freq.Body.BodyGyroMag.mean.Freq        : num  -0.139775 -0.000262 -0.028606 0.268844 0.349614 ...
##  $ freq.Body.BodyGyroJerkMag.mean.        : num  -0.942 -0.99 -0.995 -0.319 -0.282 ...
##  $ freq.Body.BodyGyroJerkMag.std.         : num  -0.933 -0.987 -0.995 -0.382 -0.392 ...
##  $ freq.Body.BodyGyroJerkMag.mean.Freq    : num  0.176 0.185 0.334 0.191 0.19 ...
##  $ angletime.Body.AccMean,gravity         : num  0.021366 0.027442 -0.000222 0.060454 -0.002695 ...
##  $ angletime.Body.AccJerkMean,gravityMean : num  0.00306 0.02971 0.02196 -0.00793 0.08993 ...
##  $ angletime.Body.GyroMean,gravityMean    : num  -0.00167 0.0677 -0.03379 0.01306 0.06334 ...
##  $ angletime.Body.GyroJerkMean,gravityMean: num  0.0844 -0.0649 -0.0279 -0.0187 -0.04 ...
##  $ angleX,gravityMean                     : num  0.427 -0.591 -0.743 -0.729 -0.744 ...
##  $ angleY,gravityMean                     : num  -0.5203 -0.0605 0.2702 0.277 0.2672 ...
##  $ angleZ,gravityMean                     : num  -0.3524 -0.218 0.0123 0.0689 0.065 ...
##  - attr(*, "vars")= chr "Subject"
##  - attr(*, "drop")= logi TRUE
```
## Tidy Dataset Variable Combinations

```
##  [1] "Subject"                                
##  [2] "activityname.str"                       
##  [3] "time.Body.Acc.mean.X"                   
##  [4] "time.Body.Acc.mean.Y"                   
##  [5] "time.Body.Acc.mean.Z"                   
##  [6] "time.Body.Acc.std.X"                    
##  [7] "time.Body.Acc.std.Y"                    
##  [8] "time.Body.Acc.std.Z"                    
##  [9] "time.Gravity.Acc.mean.X"                
## [10] "time.Gravity.Acc.mean.Y"                
## [11] "time.Gravity.Acc.mean.Z"                
## [12] "time.Gravity.Acc.std.X"                 
## [13] "time.Gravity.Acc.std.Y"                 
## [14] "time.Gravity.Acc.std.Z"                 
## [15] "time.Body.AccJerk.mean.X"               
## [16] "time.Body.AccJerk.mean.Y"               
## [17] "time.Body.AccJerk.mean.Z"               
## [18] "time.Body.AccJerk.std.X"                
## [19] "time.Body.AccJerk.std.Y"                
## [20] "time.Body.AccJerk.std.Z"                
## [21] "time.Body.Gyro.mean.X"                  
## [22] "time.Body.Gyro.mean.Y"                  
## [23] "time.Body.Gyro.mean.Z"                  
## [24] "time.Body.Gyro.std.X"                   
## [25] "time.Body.Gyro.std.Y"                   
## [26] "time.Body.Gyro.std.Z"                   
## [27] "time.Body.GyroJerk.mean.X"              
## [28] "time.Body.GyroJerk.mean.Y"              
## [29] "time.Body.GyroJerk.mean.Z"              
## [30] "time.Body.GyroJerk.std.X"               
## [31] "time.Body.GyroJerk.std.Y"               
## [32] "time.Body.GyroJerk.std.Z"               
## [33] "time.Body.AccMag.mean."                 
## [34] "time.Body.AccMag.std."                  
## [35] "time.Gravity.AccMag.mean."              
## [36] "time.Gravity.AccMag.std."               
## [37] "time.Body.AccJerkMag.mean."             
## [38] "time.Body.AccJerkMag.std."              
## [39] "time.Body.GyroMag.mean."                
## [40] "time.Body.GyroMag.std."                 
## [41] "time.Body.GyroJerkMag.mean."            
## [42] "time.Body.GyroJerkMag.std."             
## [43] "freq.Body.Acc.mean.X"                   
## [44] "freq.Body.Acc.mean.Y"                   
## [45] "freq.Body.Acc.mean.Z"                   
## [46] "freq.Body.Acc.std.X"                    
## [47] "freq.Body.Acc.std.Y"                    
## [48] "freq.Body.Acc.std.Z"                    
## [49] "freq.Body.Acc.mean.FreqX"               
## [50] "freq.Body.Acc.mean.FreqY"               
## [51] "freq.Body.Acc.mean.FreqZ"               
## [52] "freq.Body.AccJerk.mean.X"               
## [53] "freq.Body.AccJerk.mean.Y"               
## [54] "freq.Body.AccJerk.mean.Z"               
## [55] "freq.Body.AccJerk.std.X"                
## [56] "freq.Body.AccJerk.std.Y"                
## [57] "freq.Body.AccJerk.std.Z"                
## [58] "freq.Body.AccJerk.mean.FreqX"           
## [59] "freq.Body.AccJerk.mean.FreqY"           
## [60] "freq.Body.AccJerk.mean.FreqZ"           
## [61] "freq.Body.Gyro.mean.X"                  
## [62] "freq.Body.Gyro.mean.Y"                  
## [63] "freq.Body.Gyro.mean.Z"                  
## [64] "freq.Body.Gyro.std.X"                   
## [65] "freq.Body.Gyro.std.Y"                   
## [66] "freq.Body.Gyro.std.Z"                   
## [67] "freq.Body.Gyro.mean.FreqX"              
## [68] "freq.Body.Gyro.mean.FreqY"              
## [69] "freq.Body.Gyro.mean.FreqZ"              
## [70] "freq.Body.AccMag.mean."                 
## [71] "freq.Body.AccMag.std."                  
## [72] "freq.Body.AccMag.mean.Freq"             
## [73] "freq.Body.BodyAccJerkMag.mean."         
## [74] "freq.Body.BodyAccJerkMag.std."          
## [75] "freq.Body.BodyAccJerkMag.mean.Freq"     
## [76] "freq.Body.BodyGyroMag.mean."            
## [77] "freq.Body.BodyGyroMag.std."             
## [78] "freq.Body.BodyGyroMag.mean.Freq"        
## [79] "freq.Body.BodyGyroJerkMag.mean."        
## [80] "freq.Body.BodyGyroJerkMag.std."         
## [81] "freq.Body.BodyGyroJerkMag.mean.Freq"    
## [82] "angletime.Body.AccMean,gravity"         
## [83] "angletime.Body.AccJerkMean,gravityMean" 
## [84] "angletime.Body.GyroMean,gravityMean"    
## [85] "angletime.Body.GyroJerkMean,gravityMean"
## [86] "angleX,gravityMean"                     
## [87] "angleY,gravityMean"                     
## [88] "angleZ,gravityMean"
```

