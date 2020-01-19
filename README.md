Loan Prediction
-----------------------

Predict whether or not loans acquired by Fannie Mae will go into foreclosure.  Fannie Mae acquires loans from other lenders as a way of inducing them to lend more.  Fannie Mae releases data on the loans it has acquired and their performance afterwards [here](http://www.fanniemae.com/portal/funding-the-market/data/loan-performance-data.html).

Installation
----------------------

### Download the data

* Clone this repo to your computer.
* Get into the folder using `cd Loan-Prediction`.
* Run `mkdir data`.
* Switch into the `data` directory using `cd data`.
* Download the data files from Fannie Mae into the `data` directory.  
    * You can find the data [here](http://www.fanniemae.com/portal/funding-the-market/data/loan-performance-data.html).
* Extract all of the `.zip` files you downloaded.
    * On OSX, you can run `find ./ -name \*.zip -exec unzip {} \;`.
    * At the end, you should have a bunch of text files called `Acquisition_YQX.txt`, and `Performance_YQX.txt`, where `Y` is a year, and `X` is a number from `1` to `4`.
* Remove all the zip files by running `rm *.zip`.
* Switch back into the `Loan-Prediction` directory using `cd ..`.

### Install the requirements
 
* Install the requirements using `pip install -r requirements.txt`.
    * Make sure you use Python 3.
    * You may want to use a virtual environment for this.

Usage
-----------------------

* Run `mkdir processed` to create a directory for our processed datasets.
* Run `python assemble.py` to combine the `Acquisition` and `Performance` datasets.
    * This will create `Acquisition.txt` and `Performance.txt` in the `processed` folder.
* Run `python annotate.py`.
    * This will create training data from `Acquisition.txt` and `Performance.txt`.
    * It will add a file called `train.csv` to the `processed` folder.
* Run `python predict.py`.
    * This will run cross validation across the training set, and print the accuracy score.