# {
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 1,
   "id": "4696bae4-d122-45c0-b5e6-d51b5f675a7b",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Requirement already satisfied: tensorflow in c:\\users\\hp\\anaconda3\\lib\\site-packages (2.17.0)\n",
      "Requirement already satisfied: tensorflow-intel==2.17.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow) (2.17.0)\n",
      "Requirement already satisfied: absl-py>=1.0.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (2.1.0)\n",
      "Requirement already satisfied: astunparse>=1.6.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (1.6.3)\n",
      "Requirement already satisfied: flatbuffers>=24.3.25 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (24.3.25)\n",
      "Requirement already satisfied: gast!=0.5.0,!=0.5.1,!=0.5.2,>=0.2.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (0.6.0)\n",
      "Requirement already satisfied: google-pasta>=0.1.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (0.2.0)\n",
      "Requirement already satisfied: h5py>=3.10.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (3.11.0)\n",
      "Requirement already satisfied: libclang>=13.0.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (18.1.1)\n",
      "Requirement already satisfied: ml-dtypes<0.5.0,>=0.3.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (0.4.0)\n",
      "Requirement already satisfied: opt-einsum>=2.3.2 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (3.3.0)\n",
      "Requirement already satisfied: packaging in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (23.2)\n",
      "Requirement already satisfied: protobuf!=4.21.0,!=4.21.1,!=4.21.2,!=4.21.3,!=4.21.4,!=4.21.5,<5.0.0dev,>=3.20.3 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (4.25.3)\n",
      "Requirement already satisfied: requests<3,>=2.21.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (2.32.2)\n",
      "Requirement already satisfied: setuptools in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (69.5.1)\n",
      "Requirement already satisfied: six>=1.12.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (1.16.0)\n",
      "Requirement already satisfied: termcolor>=1.1.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (2.4.0)\n",
      "Requirement already satisfied: typing-extensions>=3.6.6 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (4.11.0)\n",
      "Requirement already satisfied: wrapt>=1.11.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (1.14.1)\n",
      "Requirement already satisfied: grpcio<2.0,>=1.24.3 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (1.64.1)\n",
      "Requirement already satisfied: tensorboard<2.18,>=2.17 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (2.17.0)\n",
      "Requirement already satisfied: keras>=3.2.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (3.4.1)\n",
      "Requirement already satisfied: numpy<2.0.0,>=1.26.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (1.26.4)\n",
      "Requirement already satisfied: wheel<1.0,>=0.23.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from astunparse>=1.6.0->tensorflow-intel==2.17.0->tensorflow) (0.43.0)\n",
      "Requirement already satisfied: rich in c:\\users\\hp\\anaconda3\\lib\\site-packages (from keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow) (13.3.5)\n",
      "Requirement already satisfied: namex in c:\\users\\hp\\anaconda3\\lib\\site-packages (from keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow) (0.0.8)\n",
      "Requirement already satisfied: optree in c:\\users\\hp\\anaconda3\\lib\\site-packages (from keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow) (0.12.1)\n",
      "Requirement already satisfied: charset-normalizer<4,>=2 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from requests<3,>=2.21.0->tensorflow-intel==2.17.0->tensorflow) (2.0.4)\n",
      "Requirement already satisfied: idna<4,>=2.5 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from requests<3,>=2.21.0->tensorflow-intel==2.17.0->tensorflow) (3.7)\n",
      "Requirement already satisfied: urllib3<3,>=1.21.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from requests<3,>=2.21.0->tensorflow-intel==2.17.0->tensorflow) (2.2.2)\n",
      "Requirement already satisfied: certifi>=2017.4.17 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from requests<3,>=2.21.0->tensorflow-intel==2.17.0->tensorflow) (2024.7.4)\n",
      "Requirement already satisfied: markdown>=2.6.8 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorboard<2.18,>=2.17->tensorflow-intel==2.17.0->tensorflow) (3.4.1)\n",
      "Requirement already satisfied: tensorboard-data-server<0.8.0,>=0.7.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorboard<2.18,>=2.17->tensorflow-intel==2.17.0->tensorflow) (0.7.2)\n",
      "Requirement already satisfied: werkzeug>=1.0.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorboard<2.18,>=2.17->tensorflow-intel==2.17.0->tensorflow) (3.0.3)\n",
      "Requirement already satisfied: MarkupSafe>=2.1.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from werkzeug>=1.0.1->tensorboard<2.18,>=2.17->tensorflow-intel==2.17.0->tensorflow) (2.1.3)\n",
      "Requirement already satisfied: markdown-it-py<3.0.0,>=2.2.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from rich->keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow) (2.2.0)\n",
      "Requirement already satisfied: pygments<3.0.0,>=2.13.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from rich->keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow) (2.15.1)\n",
      "Requirement already satisfied: mdurl~=0.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from markdown-it-py<3.0.0,>=2.2.0->rich->keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow) (0.1.0)\n",
      "Requirement already satisfied: tensorflow-hub in c:\\users\\hp\\anaconda3\\lib\\site-packages (0.16.1)\n",
      "Requirement already satisfied: numpy>=1.12.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-hub) (1.26.4)\n",
      "Requirement already satisfied: protobuf>=3.19.6 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-hub) (4.25.3)\n",
      "Requirement already satisfied: tf-keras>=2.14.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-hub) (2.17.0)\n",
      "Requirement already satisfied: tensorflow<2.18,>=2.17 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tf-keras>=2.14.1->tensorflow-hub) (2.17.0)\n",
      "Requirement already satisfied: tensorflow-intel==2.17.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (2.17.0)\n",
      "Requirement already satisfied: absl-py>=1.0.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (2.1.0)\n",
      "Requirement already satisfied: astunparse>=1.6.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (1.6.3)\n",
      "Requirement already satisfied: flatbuffers>=24.3.25 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (24.3.25)\n",
      "Requirement already satisfied: gast!=0.5.0,!=0.5.1,!=0.5.2,>=0.2.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (0.6.0)\n",
      "Requirement already satisfied: google-pasta>=0.1.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (0.2.0)\n",
      "Requirement already satisfied: h5py>=3.10.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (3.11.0)\n",
      "Requirement already satisfied: libclang>=13.0.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (18.1.1)\n",
      "Requirement already satisfied: ml-dtypes<0.5.0,>=0.3.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (0.4.0)\n",
      "Requirement already satisfied: opt-einsum>=2.3.2 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (3.3.0)\n",
      "Requirement already satisfied: packaging in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (23.2)\n",
      "Requirement already satisfied: requests<3,>=2.21.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (2.32.2)\n",
      "Requirement already satisfied: setuptools in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (69.5.1)\n",
      "Requirement already satisfied: six>=1.12.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (1.16.0)\n",
      "Requirement already satisfied: termcolor>=1.1.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (2.4.0)\n",
      "Requirement already satisfied: typing-extensions>=3.6.6 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (4.11.0)\n",
      "Requirement already satisfied: wrapt>=1.11.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (1.14.1)\n",
      "Requirement already satisfied: grpcio<2.0,>=1.24.3 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (1.64.1)\n",
      "Requirement already satisfied: tensorboard<2.18,>=2.17 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (2.17.0)\n",
      "Requirement already satisfied: keras>=3.2.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (3.4.1)\n",
      "Requirement already satisfied: wheel<1.0,>=0.23.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from astunparse>=1.6.0->tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (0.43.0)\n",
      "Requirement already satisfied: rich in c:\\users\\hp\\anaconda3\\lib\\site-packages (from keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (13.3.5)\n",
      "Requirement already satisfied: namex in c:\\users\\hp\\anaconda3\\lib\\site-packages (from keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (0.0.8)\n",
      "Requirement already satisfied: optree in c:\\users\\hp\\anaconda3\\lib\\site-packages (from keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (0.12.1)\n",
      "Requirement already satisfied: charset-normalizer<4,>=2 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from requests<3,>=2.21.0->tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (2.0.4)\n",
      "Requirement already satisfied: idna<4,>=2.5 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from requests<3,>=2.21.0->tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (3.7)\n",
      "Requirement already satisfied: urllib3<3,>=1.21.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from requests<3,>=2.21.0->tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (2.2.2)\n",
      "Requirement already satisfied: certifi>=2017.4.17 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from requests<3,>=2.21.0->tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (2024.7.4)\n",
      "Requirement already satisfied: markdown>=2.6.8 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorboard<2.18,>=2.17->tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (3.4.1)\n",
      "Requirement already satisfied: tensorboard-data-server<0.8.0,>=0.7.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorboard<2.18,>=2.17->tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (0.7.2)\n",
      "Requirement already satisfied: werkzeug>=1.0.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorboard<2.18,>=2.17->tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (3.0.3)\n",
      "Requirement already satisfied: MarkupSafe>=2.1.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from werkzeug>=1.0.1->tensorboard<2.18,>=2.17->tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (2.1.3)\n",
      "Requirement already satisfied: markdown-it-py<3.0.0,>=2.2.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from rich->keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (2.2.0)\n",
      "Requirement already satisfied: pygments<3.0.0,>=2.13.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from rich->keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (2.15.1)\n",
      "Requirement already satisfied: mdurl~=0.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from markdown-it-py<3.0.0,>=2.2.0->rich->keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow<2.18,>=2.17->tf-keras>=2.14.1->tensorflow-hub) (0.1.0)\n",
      "Requirement already satisfied: tensorflow-datasets in c:\\users\\hp\\anaconda3\\lib\\site-packages (4.9.6)\n",
      "Requirement already satisfied: absl-py in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-datasets) (2.1.0)\n",
      "Requirement already satisfied: click in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-datasets) (8.1.7)\n",
      "Requirement already satisfied: dm-tree in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-datasets) (0.1.8)\n",
      "Requirement already satisfied: immutabledict in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-datasets) (4.2.0)\n",
      "Requirement already satisfied: numpy in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-datasets) (1.26.4)\n",
      "Requirement already satisfied: promise in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-datasets) (2.3)\n",
      "Requirement already satisfied: protobuf>=3.20 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-datasets) (4.25.3)\n",
      "Requirement already satisfied: psutil in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-datasets) (5.9.0)\n",
      "Requirement already satisfied: pyarrow in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-datasets) (14.0.2)\n",
      "Requirement already satisfied: requests>=2.19.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-datasets) (2.32.2)\n",
      "Requirement already satisfied: simple-parsing in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-datasets) (0.1.5)\n",
      "Requirement already satisfied: tensorflow-metadata in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-datasets) (1.15.0)\n",
      "Requirement already satisfied: termcolor in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-datasets) (2.4.0)\n",
      "Requirement already satisfied: toml in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-datasets) (0.10.2)\n",
      "Requirement already satisfied: tqdm in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-datasets) (4.66.4)\n",
      "Requirement already satisfied: wrapt in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-datasets) (1.14.1)\n",
      "Requirement already satisfied: etils>=1.9.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from etils[enp,epath,epy,etree]>=1.9.1; python_version >= \"3.11\"->tensorflow-datasets) (1.9.2)\n",
      "Requirement already satisfied: fsspec in c:\\users\\hp\\anaconda3\\lib\\site-packages (from etils[enp,epath,epy,etree]>=1.9.1; python_version >= \"3.11\"->tensorflow-datasets) (2024.3.1)\n",
      "Requirement already satisfied: importlib_resources in c:\\users\\hp\\anaconda3\\lib\\site-packages (from etils[enp,epath,epy,etree]>=1.9.1; python_version >= \"3.11\"->tensorflow-datasets) (6.4.0)\n",
      "Requirement already satisfied: typing_extensions in c:\\users\\hp\\anaconda3\\lib\\site-packages (from etils[enp,epath,epy,etree]>=1.9.1; python_version >= \"3.11\"->tensorflow-datasets) (4.11.0)\n",
      "Requirement already satisfied: zipp in c:\\users\\hp\\anaconda3\\lib\\site-packages (from etils[enp,epath,epy,etree]>=1.9.1; python_version >= \"3.11\"->tensorflow-datasets) (3.17.0)\n",
      "Requirement already satisfied: charset-normalizer<4,>=2 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from requests>=2.19.0->tensorflow-datasets) (2.0.4)\n",
      "Requirement already satisfied: idna<4,>=2.5 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from requests>=2.19.0->tensorflow-datasets) (3.7)\n",
      "Requirement already satisfied: urllib3<3,>=1.21.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from requests>=2.19.0->tensorflow-datasets) (2.2.2)\n",
      "Requirement already satisfied: certifi>=2017.4.17 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from requests>=2.19.0->tensorflow-datasets) (2024.7.4)\n",
      "Requirement already satisfied: colorama in c:\\users\\hp\\anaconda3\\lib\\site-packages (from click->tensorflow-datasets) (0.4.6)\n",
      "Requirement already satisfied: six in c:\\users\\hp\\anaconda3\\lib\\site-packages (from promise->tensorflow-datasets) (1.16.0)\n",
      "Requirement already satisfied: docstring-parser~=0.15 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from simple-parsing->tensorflow-datasets) (0.16)\n",
      "Requirement already satisfied: googleapis-common-protos<2,>=1.56.4 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-metadata->tensorflow-datasets) (1.63.2)\n"
     ]
    }
   ],
   "source": [
    "!pip install tensorflow\n",
    "!pip install tensorflow-hub\n",
    "!pip install tensorflow-datasets"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 2,
   "id": "304dba76-305e-41f5-b5e8-07cfe0e88820",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "WARNING:tensorflow:From C:\\Users\\hp\\anaconda3\\Lib\\site-packages\\tf_keras\\src\\losses.py:2976: The name tf.losses.sparse_softmax_cross_entropy is deprecated. Please use tf.compat.v1.losses.sparse_softmax_cross_entropy instead.\n",
      "\n"
     ]
    }
   ],
   "source": [
    "import numpy as np\n",
    "import tensorflow as tf\n",
    "import tensorflow_hub as hub\n",
    "import tensorflow_datasets as tfds"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "id": "e3aa8a4c-7066-4557-bf8f-95e39f6e6cf8",
   "metadata": {},
   "outputs": [],
   "source": [
    "train_data,val_data,test_data = tfds.load(name=\"imdb_reviews\",\n",
    "                                         split = (\"train\", \"test[:40%]\", \"test[40%:]\"),\n",
    "                                         as_supervised = True)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "id": "cf21eb5a-3ecc-4eee-bb8f-3493a5316b03",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<_PrefetchDataset element_spec=(TensorSpec(shape=(), dtype=tf.string, name=None), TensorSpec(shape=(), dtype=tf.int64, name=None))>\n"
     ]
    }
   ],
   "source": [
    "print(train_data)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "id": "a0c6f290-673c-4a3a-b38b-146917f4091a",
   "metadata": {},
   "outputs": [],
   "source": [
    "text,label = next(iter(train_data.batch(5)))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "id": "2b4060e4-9c0e-4e28-87cc-6ab21ab7ddd9",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<tf.Tensor: shape=(5,), dtype=int64, numpy=array([0, 0, 0, 1, 1], dtype=int64)>"
      ]
     },
     "execution_count": 11,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "label"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 13,
   "id": "01b9ffa6-0de3-42b4-ba03-5e646b9c1c5a",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<tf.Tensor: shape=(5,), dtype=string, numpy=\n",
       "array([b\"This was an absolutely terrible movie. Don't be lured in by Christopher Walken or Michael Ironside. Both are great actors, but this must simply be their worst role in history. Even their great acting could not redeem this movie's ridiculous storyline. This movie is an early nineties US propaganda piece. The most pathetic scenes were those when the Columbian rebels were making their cases for revolutions. Maria Conchita Alonso appeared phony, and her pseudo-love affair with Walken was nothing but a pathetic emotional plug in a movie that was devoid of any real meaning. I am disappointed that there are movies like this, ruining actor's like Christopher Walken's good name. I could barely sit through it.\",\n",
       "       b'I have been known to fall asleep during films, but this is usually due to a combination of things including, really tired, being warm and comfortable on the sette and having just eaten a lot. However on this occasion I fell asleep because the film was rubbish. The plot development was constant. Constantly slow and boring. Things seemed to happen, but with no explanation of what was causing them or why. I admit, I may have missed part of the film, but i watched the majority of it and everything just seemed to happen of its own accord without any real concern for anything else. I cant recommend this film at all.',\n",
       "       b'Mann photographs the Alberta Rocky Mountains in a superb fashion, and Jimmy Stewart and Walter Brennan give enjoyable performances as they always seem to do. <br /><br />But come on Hollywood - a Mountie telling the people of Dawson City, Yukon to elect themselves a marshal (yes a marshal!) and to enforce the law themselves, then gunfighters battling it out on the streets for control of the town? <br /><br />Nothing even remotely resembling that happened on the Canadian side of the border during the Klondike gold rush. Mr. Mann and company appear to have mistaken Dawson City for Deadwood, the Canadian North for the American Wild West.<br /><br />Canadian viewers be prepared for a Reefer Madness type of enjoyable howl with this ludicrous plot, or, to shake your head in disgust.',\n",
       "       b'This is the kind of film for a snowy Sunday afternoon when the rest of the world can go ahead with its own business as you descend into a big arm-chair and mellow for a couple of hours. Wonderful performances from Cher and Nicolas Cage (as always) gently row the plot along. There are no rapids to cross, no dangerous waters, just a warm and witty paddle through New York life at its best. A family film in every sense and one that deserves the praise it received.',\n",
       "       b'As others have mentioned, all the women that go nude in this film are mostly absolutely gorgeous. The plot very ably shows the hypocrisy of the female libido. When men are around they want to be pursued, but when no \"men\" are around, they become the pursuers of a 14 year old boy. And the boy becomes a man really fast (we should all be so lucky at this age!). He then gets up the courage to pursue his true love.'],\n",
       "      dtype=object)>"
      ]
     },
     "execution_count": 13,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "\n",
    "text"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 24,
   "id": "e0bc2dc4-a05c-44e2-a330-afa828ba25e4",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Requirement already satisfied: tensorflow in c:\\users\\hp\\anaconda3\\lib\\site-packages (2.17.0)\n",
      "Requirement already satisfied: tensorflow-hub in c:\\users\\hp\\anaconda3\\lib\\site-packages (0.16.1)\n",
      "Requirement already satisfied: tensorflow-intel==2.17.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow) (2.17.0)\n",
      "Requirement already satisfied: absl-py>=1.0.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (2.1.0)\n",
      "Requirement already satisfied: astunparse>=1.6.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (1.6.3)\n",
      "Requirement already satisfied: flatbuffers>=24.3.25 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (24.3.25)\n",
      "Requirement already satisfied: gast!=0.5.0,!=0.5.1,!=0.5.2,>=0.2.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (0.6.0)\n",
      "Requirement already satisfied: google-pasta>=0.1.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (0.2.0)\n",
      "Requirement already satisfied: h5py>=3.10.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (3.11.0)\n",
      "Requirement already satisfied: libclang>=13.0.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (18.1.1)\n",
      "Requirement already satisfied: ml-dtypes<0.5.0,>=0.3.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (0.4.0)\n",
      "Requirement already satisfied: opt-einsum>=2.3.2 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (3.3.0)\n",
      "Requirement already satisfied: packaging in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (23.2)\n",
      "Requirement already satisfied: protobuf!=4.21.0,!=4.21.1,!=4.21.2,!=4.21.3,!=4.21.4,!=4.21.5,<5.0.0dev,>=3.20.3 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (4.25.3)\n",
      "Requirement already satisfied: requests<3,>=2.21.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (2.32.2)\n",
      "Requirement already satisfied: setuptools in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (69.5.1)\n",
      "Requirement already satisfied: six>=1.12.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (1.16.0)\n",
      "Requirement already satisfied: termcolor>=1.1.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (2.4.0)\n",
      "Requirement already satisfied: typing-extensions>=3.6.6 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (4.11.0)\n",
      "Requirement already satisfied: wrapt>=1.11.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (1.14.1)\n",
      "Requirement already satisfied: grpcio<2.0,>=1.24.3 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (1.64.1)\n",
      "Requirement already satisfied: tensorboard<2.18,>=2.17 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (2.17.0)\n",
      "Requirement already satisfied: keras>=3.2.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (3.4.1)\n",
      "Requirement already satisfied: numpy<2.0.0,>=1.26.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (1.26.4)\n",
      "Requirement already satisfied: tf-keras>=2.14.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-hub) (2.17.0)\n",
      "Requirement already satisfied: wheel<1.0,>=0.23.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from astunparse>=1.6.0->tensorflow-intel==2.17.0->tensorflow) (0.43.0)\n",
      "Requirement already satisfied: rich in c:\\users\\hp\\anaconda3\\lib\\site-packages (from keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow) (13.3.5)\n",
      "Requirement already satisfied: namex in c:\\users\\hp\\anaconda3\\lib\\site-packages (from keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow) (0.0.8)\n",
      "Requirement already satisfied: optree in c:\\users\\hp\\anaconda3\\lib\\site-packages (from keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow) (0.12.1)\n",
      "Requirement already satisfied: charset-normalizer<4,>=2 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from requests<3,>=2.21.0->tensorflow-intel==2.17.0->tensorflow) (2.0.4)\n",
      "Requirement already satisfied: idna<4,>=2.5 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from requests<3,>=2.21.0->tensorflow-intel==2.17.0->tensorflow) (3.7)\n",
      "Requirement already satisfied: urllib3<3,>=1.21.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from requests<3,>=2.21.0->tensorflow-intel==2.17.0->tensorflow) (2.2.2)\n",
      "Requirement already satisfied: certifi>=2017.4.17 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from requests<3,>=2.21.0->tensorflow-intel==2.17.0->tensorflow) (2024.7.4)\n",
      "Requirement already satisfied: markdown>=2.6.8 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorboard<2.18,>=2.17->tensorflow-intel==2.17.0->tensorflow) (3.4.1)\n",
      "Requirement already satisfied: tensorboard-data-server<0.8.0,>=0.7.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorboard<2.18,>=2.17->tensorflow-intel==2.17.0->tensorflow) (0.7.2)\n",
      "Requirement already satisfied: werkzeug>=1.0.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorboard<2.18,>=2.17->tensorflow-intel==2.17.0->tensorflow) (3.0.3)\n",
      "Requirement already satisfied: MarkupSafe>=2.1.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from werkzeug>=1.0.1->tensorboard<2.18,>=2.17->tensorflow-intel==2.17.0->tensorflow) (2.1.3)\n",
      "Requirement already satisfied: markdown-it-py<3.0.0,>=2.2.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from rich->keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow) (2.2.0)\n",
      "Requirement already satisfied: pygments<3.0.0,>=2.13.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from rich->keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow) (2.15.1)\n",
      "Requirement already satisfied: mdurl~=0.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from markdown-it-py<3.0.0,>=2.2.0->rich->keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow) (0.1.0)\n"
     ]
    }
   ],
   "source": [
    "!pip install --upgrade tensorflow tensorflow-hub\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 32,
   "id": "765aaf80-489f-45db-82f0-c841fa19b941",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Requirement already satisfied: tensorflow in c:\\users\\hp\\anaconda3\\lib\\site-packages (2.17.0)\n",
      "Requirement already satisfied: tensorflow-hub in c:\\users\\hp\\anaconda3\\lib\\site-packages (0.16.1)\n",
      "Requirement already satisfied: tensorflow-intel==2.17.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow) (2.17.0)\n",
      "Requirement already satisfied: absl-py>=1.0.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (2.1.0)\n",
      "Requirement already satisfied: astunparse>=1.6.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (1.6.3)\n",
      "Requirement already satisfied: flatbuffers>=24.3.25 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (24.3.25)\n",
      "Requirement already satisfied: gast!=0.5.0,!=0.5.1,!=0.5.2,>=0.2.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (0.6.0)\n",
      "Requirement already satisfied: google-pasta>=0.1.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (0.2.0)\n",
      "Requirement already satisfied: h5py>=3.10.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (3.11.0)\n",
      "Requirement already satisfied: libclang>=13.0.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (18.1.1)\n",
      "Requirement already satisfied: ml-dtypes<0.5.0,>=0.3.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (0.4.0)\n",
      "Requirement already satisfied: opt-einsum>=2.3.2 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (3.3.0)\n",
      "Requirement already satisfied: packaging in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (23.2)\n",
      "Requirement already satisfied: protobuf!=4.21.0,!=4.21.1,!=4.21.2,!=4.21.3,!=4.21.4,!=4.21.5,<5.0.0dev,>=3.20.3 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (4.25.3)\n",
      "Requirement already satisfied: requests<3,>=2.21.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (2.32.2)\n",
      "Requirement already satisfied: setuptools in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (69.5.1)\n",
      "Requirement already satisfied: six>=1.12.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (1.16.0)\n",
      "Requirement already satisfied: termcolor>=1.1.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (2.4.0)\n",
      "Requirement already satisfied: typing-extensions>=3.6.6 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (4.11.0)\n",
      "Requirement already satisfied: wrapt>=1.11.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (1.14.1)\n",
      "Requirement already satisfied: grpcio<2.0,>=1.24.3 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (1.64.1)\n",
      "Requirement already satisfied: tensorboard<2.18,>=2.17 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (2.17.0)\n",
      "Requirement already satisfied: keras>=3.2.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (3.4.1)\n",
      "Requirement already satisfied: numpy<2.0.0,>=1.26.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-intel==2.17.0->tensorflow) (1.26.4)\n",
      "Requirement already satisfied: tf-keras>=2.14.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorflow-hub) (2.17.0)\n",
      "Requirement already satisfied: wheel<1.0,>=0.23.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from astunparse>=1.6.0->tensorflow-intel==2.17.0->tensorflow) (0.43.0)\n",
      "Requirement already satisfied: rich in c:\\users\\hp\\anaconda3\\lib\\site-packages (from keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow) (13.3.5)\n",
      "Requirement already satisfied: namex in c:\\users\\hp\\anaconda3\\lib\\site-packages (from keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow) (0.0.8)\n",
      "Requirement already satisfied: optree in c:\\users\\hp\\anaconda3\\lib\\site-packages (from keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow) (0.12.1)\n",
      "Requirement already satisfied: charset-normalizer<4,>=2 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from requests<3,>=2.21.0->tensorflow-intel==2.17.0->tensorflow) (2.0.4)\n",
      "Requirement already satisfied: idna<4,>=2.5 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from requests<3,>=2.21.0->tensorflow-intel==2.17.0->tensorflow) (3.7)\n",
      "Requirement already satisfied: urllib3<3,>=1.21.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from requests<3,>=2.21.0->tensorflow-intel==2.17.0->tensorflow) (2.2.2)\n",
      "Requirement already satisfied: certifi>=2017.4.17 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from requests<3,>=2.21.0->tensorflow-intel==2.17.0->tensorflow) (2024.7.4)\n",
      "Requirement already satisfied: markdown>=2.6.8 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorboard<2.18,>=2.17->tensorflow-intel==2.17.0->tensorflow) (3.4.1)\n",
      "Requirement already satisfied: tensorboard-data-server<0.8.0,>=0.7.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorboard<2.18,>=2.17->tensorflow-intel==2.17.0->tensorflow) (0.7.2)\n",
      "Requirement already satisfied: werkzeug>=1.0.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from tensorboard<2.18,>=2.17->tensorflow-intel==2.17.0->tensorflow) (3.0.3)\n",
      "Requirement already satisfied: MarkupSafe>=2.1.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from werkzeug>=1.0.1->tensorboard<2.18,>=2.17->tensorflow-intel==2.17.0->tensorflow) (2.1.3)\n",
      "Requirement already satisfied: markdown-it-py<3.0.0,>=2.2.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from rich->keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow) (2.2.0)\n",
      "Requirement already satisfied: pygments<3.0.0,>=2.13.0 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from rich->keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow) (2.15.1)\n",
      "Requirement already satisfied: mdurl~=0.1 in c:\\users\\hp\\anaconda3\\lib\\site-packages (from markdown-it-py<3.0.0,>=2.2.0->rich->keras>=3.2.0->tensorflow-intel==2.17.0->tensorflow) (0.1.0)\n"
     ]
    }
   ],
   "source": [
    "!pip install --upgrade tensorflow tensorflow-hub\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 50,
   "id": "5e82241a-e730-4e60-802f-7edff49a9589",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "TensorFlow version: 2.17.0\n",
      "TensorFlow Hub version: 0.16.1\n"
     ]
    },
    {
     "name": "stderr",
     "output_type": "stream",
     "text": [
      "C:\\Users\\hp\\AppData\\Local\\Temp\\ipykernel_29044\\1109947260.py:8: UserWarning: Do not pass an `input_shape`/`input_dim` argument to a layer. When using Sequential models, prefer using an `Input(shape)` object as the first layer in the model instead.\n",
      "  super(HubLayer, self).__init__(**kwargs)\n"
     ]
    },
    {
     "data": {
      "text/html": [
       "<pre style=\"white-space:pre;overflow-x:auto;line-height:normal;font-family:Menlo,'DejaVu Sans Mono',consolas,'Courier New',monospace\"><span style=\"font-weight: bold\">Model: \"sequential_10\"</span>\n",
       "</pre>\n"
      ],
      "text/plain": [
       "\u001b[1mModel: \"sequential_10\"\u001b[0m\n"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    },
    {
     "data": {
      "text/html": [
       "<pre style=\"white-space:pre;overflow-x:auto;line-height:normal;font-family:Menlo,'DejaVu Sans Mono',consolas,'Courier New',monospace\">┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━┓\n",
       "┃<span style=\"font-weight: bold\"> Layer (type)                         </span>┃<span style=\"font-weight: bold\"> Output Shape                </span>┃<span style=\"font-weight: bold\">         Param # </span>┃\n",
       "┡━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━┩\n",
       "│ hub_layer_5 (<span style=\"color: #0087ff; text-decoration-color: #0087ff\">HubLayer</span>)               │ (<span style=\"color: #00d7ff; text-decoration-color: #00d7ff\">None</span>, <span style=\"color: #00af00; text-decoration-color: #00af00\">50</span>)                  │               <span style=\"color: #00af00; text-decoration-color: #00af00\">0</span> │\n",
       "├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤\n",
       "│ dense_13 (<span style=\"color: #0087ff; text-decoration-color: #0087ff\">Dense</span>)                     │ (<span style=\"color: #00d7ff; text-decoration-color: #00d7ff\">None</span>, <span style=\"color: #00af00; text-decoration-color: #00af00\">16</span>)                  │             <span style=\"color: #00af00; text-decoration-color: #00af00\">816</span> │\n",
       "├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤\n",
       "│ dense_14 (<span style=\"color: #0087ff; text-decoration-color: #0087ff\">Dense</span>)                     │ (<span style=\"color: #00d7ff; text-decoration-color: #00d7ff\">None</span>, <span style=\"color: #00af00; text-decoration-color: #00af00\">4</span>)                   │              <span style=\"color: #00af00; text-decoration-color: #00af00\">68</span> │\n",
       "├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤\n",
       "│ dense_15 (<span style=\"color: #0087ff; text-decoration-color: #0087ff\">Dense</span>)                     │ (<span style=\"color: #00d7ff; text-decoration-color: #00d7ff\">None</span>, <span style=\"color: #00af00; text-decoration-color: #00af00\">1</span>)                   │               <span style=\"color: #00af00; text-decoration-color: #00af00\">5</span> │\n",
       "└──────────────────────────────────────┴─────────────────────────────┴─────────────────┘\n",
       "</pre>\n"
      ],
      "text/plain": [
       "┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━┓\n",
       "┃\u001b[1m \u001b[0m\u001b[1mLayer (type)                        \u001b[0m\u001b[1m \u001b[0m┃\u001b[1m \u001b[0m\u001b[1mOutput Shape               \u001b[0m\u001b[1m \u001b[0m┃\u001b[1m \u001b[0m\u001b[1m        Param #\u001b[0m\u001b[1m \u001b[0m┃\n",
       "┡━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━┩\n",
       "│ hub_layer_5 (\u001b[38;5;33mHubLayer\u001b[0m)               │ (\u001b[38;5;45mNone\u001b[0m, \u001b[38;5;34m50\u001b[0m)                  │               \u001b[38;5;34m0\u001b[0m │\n",
       "├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤\n",
       "│ dense_13 (\u001b[38;5;33mDense\u001b[0m)                     │ (\u001b[38;5;45mNone\u001b[0m, \u001b[38;5;34m16\u001b[0m)                  │             \u001b[38;5;34m816\u001b[0m │\n",
       "├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤\n",
       "│ dense_14 (\u001b[38;5;33mDense\u001b[0m)                     │ (\u001b[38;5;45mNone\u001b[0m, \u001b[38;5;34m4\u001b[0m)                   │              \u001b[38;5;34m68\u001b[0m │\n",
       "├──────────────────────────────────────┼─────────────────────────────┼─────────────────┤\n",
       "│ dense_15 (\u001b[38;5;33mDense\u001b[0m)                     │ (\u001b[38;5;45mNone\u001b[0m, \u001b[38;5;34m1\u001b[0m)                   │               \u001b[38;5;34m5\u001b[0m │\n",
       "└──────────────────────────────────────┴─────────────────────────────┴─────────────────┘\n"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    },
    {
     "data": {
      "text/html": [
       "<pre style=\"white-space:pre;overflow-x:auto;line-height:normal;font-family:Menlo,'DejaVu Sans Mono',consolas,'Courier New',monospace\"><span style=\"font-weight: bold\"> Total params: </span><span style=\"color: #00af00; text-decoration-color: #00af00\">889</span> (3.47 KB)\n",
       "</pre>\n"
      ],
      "text/plain": [
       "\u001b[1m Total params: \u001b[0m\u001b[38;5;34m889\u001b[0m (3.47 KB)\n"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    },
    {
     "data": {
      "text/html": [
       "<pre style=\"white-space:pre;overflow-x:auto;line-height:normal;font-family:Menlo,'DejaVu Sans Mono',consolas,'Courier New',monospace\"><span style=\"font-weight: bold\"> Trainable params: </span><span style=\"color: #00af00; text-decoration-color: #00af00\">889</span> (3.47 KB)\n",
       "</pre>\n"
      ],
      "text/plain": [
       "\u001b[1m Trainable params: \u001b[0m\u001b[38;5;34m889\u001b[0m (3.47 KB)\n"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    },
    {
     "data": {
      "text/html": [
       "<pre style=\"white-space:pre;overflow-x:auto;line-height:normal;font-family:Menlo,'DejaVu Sans Mono',consolas,'Courier New',monospace\"><span style=\"font-weight: bold\"> Non-trainable params: </span><span style=\"color: #00af00; text-decoration-color: #00af00\">0</span> (0.00 B)\n",
       "</pre>\n"
      ],
      "text/plain": [
       "\u001b[1m Non-trainable params: \u001b[0m\u001b[38;5;34m0\u001b[0m (0.00 B)\n"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "import tensorflow as tf\n",
    "import tensorflow_hub as hub\n",
    "from tensorflow.keras.layers import Layer\n",
    "\n",
    "# Custom wrapper for hub.KerasLayer\n",
    "class KerasLayer(Layer):\n",
    "    def __init__(self, url, **kwargs):\n",
    "        super(HubLayer, self).__init__(**kwargs)\n",
    "        self.keras_layer = hub.KerasLayer(url, trainable=True)\n",
    "\n",
    "    def call(self, inputs):\n",
    "        return self.hub_layer(inputs)\n",
    "\n",
    "# Correct the hub layer URL\n",
    "hub_layer = hub.KerasLayer(\"https://kaggle.com/models/google/gnews-swivel/frameworks/TensorFlow2/variations/tf2-preview-20dim/versions/1\", output_shape=[20],\n",
    "                           input_shape=[], dtype=tf.string,trainable = True)\n",
    "\n",
    "# Ensure TensorFlow and TensorFlow Hub are compatible\n",
    "print(\"TensorFlow version:\", tf.__version__)\n",
    "print(\"TensorFlow Hub version:\", hub.__version__)\n",
    "\n",
    "# Create the model\n",
    "model = tf.keras.Sequential()\n",
    "model.add(HubLayer(hub_url, input_shape=[], dtype=tf.string))\n",
    "model.add(tf.keras.layers.Dense(16, activation='relu'))\n",
    "model.add(tf.keras.layers.Dense(4, activation = 'relu'))\n",
    "model.add(tf.keras.layers.Dense(1, activation='sigmoid'))\n",
    "\n",
    "model.compile(optimizer='adam', loss = tf.keras.losses.BinaryCrossentropy(from_logits=True), metrics=['accuracy'])\n",
    "\n",
    "# Display model summary\n",
    "model.summary()\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 44,
   "id": "5676dbcb-d316-4208-ae28-88e6f47df7e4",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Epoch 1/25\n"
     ]
    },
    {
     "name": "stderr",
     "output_type": "stream",
     "text": [
      "C:\\Users\\hp\\anaconda3\\Lib\\site-packages\\keras\\src\\backend\\tensorflow\\nn.py:681: UserWarning: \"`binary_crossentropy` received `from_logits=True`, but the `output` argument was produced by a Sigmoid activation and thus does not represent logits. Was this intended?\n",
      "  output, from_logits = _get_logits(\n"
     ]
    },
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m7s\u001b[0m 17ms/step - accuracy: 0.5684 - loss: 0.6773 - val_accuracy: 0.6967 - val_loss: 0.5860\n",
      "Epoch 2/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 15ms/step - accuracy: 0.7164 - loss: 0.5664 - val_accuracy: 0.7235 - val_loss: 0.5463\n",
      "Epoch 3/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 14ms/step - accuracy: 0.7377 - loss: 0.5322 - val_accuracy: 0.7327 - val_loss: 0.5348\n",
      "Epoch 4/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 14ms/step - accuracy: 0.7470 - loss: 0.5214 - val_accuracy: 0.7366 - val_loss: 0.5299\n",
      "Epoch 5/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 15ms/step - accuracy: 0.7458 - loss: 0.5180 - val_accuracy: 0.7389 - val_loss: 0.5273\n",
      "Epoch 6/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 14ms/step - accuracy: 0.7462 - loss: 0.5116 - val_accuracy: 0.7394 - val_loss: 0.5258\n",
      "Epoch 7/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 14ms/step - accuracy: 0.7466 - loss: 0.5180 - val_accuracy: 0.7402 - val_loss: 0.5262\n",
      "Epoch 8/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 14ms/step - accuracy: 0.7540 - loss: 0.5075 - val_accuracy: 0.7394 - val_loss: 0.5230\n",
      "Epoch 9/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 14ms/step - accuracy: 0.7531 - loss: 0.5061 - val_accuracy: 0.7409 - val_loss: 0.5225\n",
      "Epoch 10/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 16ms/step - accuracy: 0.7550 - loss: 0.5068 - val_accuracy: 0.7423 - val_loss: 0.5214\n",
      "Epoch 11/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 17ms/step - accuracy: 0.7580 - loss: 0.5026 - val_accuracy: 0.7405 - val_loss: 0.5218\n",
      "Epoch 12/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 16ms/step - accuracy: 0.7546 - loss: 0.5080 - val_accuracy: 0.7398 - val_loss: 0.5218\n",
      "Epoch 13/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 15ms/step - accuracy: 0.7548 - loss: 0.5040 - val_accuracy: 0.7413 - val_loss: 0.5224\n",
      "Epoch 14/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m3s\u001b[0m 14ms/step - accuracy: 0.7551 - loss: 0.5016 - val_accuracy: 0.7383 - val_loss: 0.5227\n",
      "Epoch 15/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m3s\u001b[0m 13ms/step - accuracy: 0.7566 - loss: 0.5017 - val_accuracy: 0.7429 - val_loss: 0.5209\n",
      "Epoch 16/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 14ms/step - accuracy: 0.7515 - loss: 0.5063 - val_accuracy: 0.7422 - val_loss: 0.5189\n",
      "Epoch 17/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 14ms/step - accuracy: 0.7578 - loss: 0.5014 - val_accuracy: 0.7408 - val_loss: 0.5230\n",
      "Epoch 18/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 14ms/step - accuracy: 0.7582 - loss: 0.5012 - val_accuracy: 0.7426 - val_loss: 0.5195\n",
      "Epoch 19/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 15ms/step - accuracy: 0.7574 - loss: 0.5002 - val_accuracy: 0.7429 - val_loss: 0.5186\n",
      "Epoch 20/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 14ms/step - accuracy: 0.7575 - loss: 0.4986 - val_accuracy: 0.7419 - val_loss: 0.5178\n",
      "Epoch 21/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 14ms/step - accuracy: 0.7595 - loss: 0.5011 - val_accuracy: 0.7431 - val_loss: 0.5182\n",
      "Epoch 22/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 16ms/step - accuracy: 0.7579 - loss: 0.4978 - val_accuracy: 0.7411 - val_loss: 0.5184\n",
      "Epoch 23/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 15ms/step - accuracy: 0.7568 - loss: 0.4986 - val_accuracy: 0.7427 - val_loss: 0.5185\n",
      "Epoch 24/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 15ms/step - accuracy: 0.7548 - loss: 0.5037 - val_accuracy: 0.7421 - val_loss: 0.5180\n",
      "Epoch 25/25\n",
      "\u001b[1m250/250\u001b[0m \u001b[32m━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[37m\u001b[0m \u001b[1m4s\u001b[0m 14ms/step - accuracy: 0.7592 - loss: 0.4957 - val_accuracy: 0.7423 - val_loss: 0.5172\n"
     ]
    }
   ],
   "source": [
    "history = model.fit(train_data.shuffle(10000).batch(100),epochs = 25, validation_data = val_data.batch(100), verbose = 1)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 46,
   "id": "ff34ffec-6502-4356-8c8f-5b16d077c11f",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "150/150 - 2s - 11ms/step - accuracy: 0.7489 - loss: 0.5088\n"
     ]
    }
   ],
   "source": [
    "results = model.evaluate(test_data.batch(100), verbose = 2)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "4b100b75-fb00-4e41-95b8-6967fd1e5f9c",
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3 (ipykernel)",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.12.4"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
