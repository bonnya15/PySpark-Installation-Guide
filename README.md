## PySpark-Installation-Guide
Detailed description for installing and using PySpark in windows through Anaconda3 and Jupyter Notebook


## First Create a virtual environment in Anaconda3 name it pyspark_env

# install required packages like, pyspark, py4j etc from Anaconda Navigator 

- Next download spark from this link http://spark.apache.org/downloads.html

- untar and unzip spark-3.1.2-bin-hadoop3.2.tgz

- after unzipping, copy it to your C drive in a blank folder say data. 

- then download and copy paste winutils.exe in the location  C:\data\spark-3.1.2-bin-hadoop3.2\bin
  (Please configure the address as per your system setting)

## Set the system paths and variables. (Most Crucial Part)

go to Control Panel --> Systems & Security --> Systems --> Advanced System Settings --> Environment Variables

- under User variables for shiuli Subhra Ghosh 

     - HADOOP_HOME = C:\data\spark-3.1.2-bin-hadoop3.2
     
     - SPARK_HOME = C:\data\spark-3.1.2-bin-hadoop3.2
     
     - add a new variable to path to where your java 8 has located 
       - path = C:\tmp\java\bin
      
     - PYSPARK_DRIVER_PYTHON = jupyter
    
     - PYSPARK_DRIVER_PYTHON_OPTS = notebook
     
- under System variables 

    - PYSPARK_PYTHON = C:\Anaconda3\envs\pyspark_env\python.exe  %% the location where you have created the new environment
     
    - add 3 new paths 
      - path = C:\tmp\java\bin
      - path = C:\data\spark-3.1.2-bin-hadoop3.2\bin
      - path = C:\Anaconda3

Your variable configuration is done 

# Now go to Anaconda Prompt

You need to activate the virtual environment you created through anaconda prompt 

- conda activate pyspark_env

Then type 

- pyspark

It will redirect you to jupyter notebook 

# for trial write your first spark code... (Name it pyspark_success)


- from pyspark.sql import SparkSession
- sc = SparkContext.getOrCreate()
- import numpy as np
- TOTAL = 1000000
- dots = sc.parallelize([2.0 * np.random.random(2) - 1.0 for i in range(TOTAL)]).cache()
- print("Number of random points:", dots.count())
    Number of random points: 1000000
- stats = dots.stats()
- print('Mean:', stats.mean())
- print('stdev:', stats.stdev())
    Mean: [-8.00075967e-04  2.46454177e-05]
    stdev: [0.57701921 0.57738532]  

It took me nearly 8 hours to figure out what is happening... Please follow the steps I think you can install it easily. 
