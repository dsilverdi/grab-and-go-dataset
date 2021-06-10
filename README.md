# Grab and Go Dataset
Source Code for Automate Generate tfrecord from Kaggle Grab and Go Dataset

# Installation
set up your python environment and use package manager [pip](https://pip.pypa.io/en/stable/) to install requirement depedency

```bash
pip install -r requirements.txt
```

then install tensorflow object detection [api](https://github.com/tensorflow/models/tree/master/research/object_detection) using our setupapi
```bash
git clone https://github.com/tensorflow/models
cd models/research/
protoc object_detection/protos/*.proto --python_out=.
cp object_detection/packages/tf2/setup.py .
python -m pip install .

```
# Download Kaggle Dataset
Download the kaggle dataset from our collected retail data in this [link](https://www.kaggle.com/hafizyusufheraldi/retail-product-dataset)

Extract the data so the project repository structure look like this

    .
    ├── data/                   # CSV file location
    ├── annotations/            # Extracted Dataset
        └── train/
        └── test/
    ├── images/                 # Extracted Dataset
        └── train/
        └── test/                 
    ├── generate_tfrecord.py                     
    ├── requirements.txt                    
    ├── detection_label_map.pbtxt                   
    ├── LICENSE
    └── README.md

# Convert XML Annotations Dataset
to generate the tfrecords formated input we need to convert XML annotations data to CSV data by running 
```bash
python xml_to_csv.py
```

# Generate TFRECORDS
We use tfrecords as input for our model training, to generate it we run generate_tfrecord.py by running

```bash
python generate_tfrecord.py --csv_input=data/train_labels.csv  --output_path=train.record --image_dir=images/train/
python generate_tfrecord.py --csv_input=data/test_labels.csv  --output_path=test.record --image_dir=images/test/
```

# Model Training
Access the Colab Notebook in this [link](https://colab.research.google.com/drive/1FzWikcT1_xjw6Ze-1gxjoUW8GWk_N2uU?usp=sharing) to train Grab and Go Retail Detection Model
