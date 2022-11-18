# DriverDrowsiness
{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 17,
   "metadata": {
    "_cell_guid": "b1076dfc-b9ad-4769-8c92-a6c4dae69d19",
    "_uuid": "8f2839f25d086af736a60e9eeb907d3b93b6e0e5",
    "execution": {
     "iopub.execute_input": "2022-11-17T05:32:09.185801Z",
     "iopub.status.busy": "2022-11-17T05:32:09.185456Z",
     "iopub.status.idle": "2022-11-17T05:32:16.606580Z",
     "shell.execute_reply": "2022-11-17T05:32:16.605630Z",
     "shell.execute_reply.started": "2022-11-17T05:32:09.185770Z"
    }
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Requirement already satisfied: livelossplot in /opt/conda/lib/python3.7/site-packages (0.5.5)\n",
      "Requirement already satisfied: ipython==7.* in /opt/conda/lib/python3.7/site-packages (from livelossplot) (7.24.1)\n",
      "Requirement already satisfied: bokeh in /opt/conda/lib/python3.7/site-packages (from livelossplot) (2.3.2)\n",
      "Requirement already satisfied: matplotlib in /opt/conda/lib/python3.7/site-packages (from livelossplot) (3.4.2)\n",
      "Requirement already satisfied: numpy<1.22 in /opt/conda/lib/python3.7/site-packages (from livelossplot) (1.19.5)\n",
      "Requirement already satisfied: jedi>=0.16 in /opt/conda/lib/python3.7/site-packages (from ipython==7.*->livelossplot) (0.18.0)\n",
      "Requirement already satisfied: backcall in /opt/conda/lib/python3.7/site-packages (from ipython==7.*->livelossplot) (0.2.0)\n",
      "Requirement already satisfied: prompt-toolkit!=3.0.0,!=3.0.1,<3.1.0,>=2.0.0 in /opt/conda/lib/python3.7/site-packages (from ipython==7.*->livelossplot) (3.0.19)\n",
      "Requirement already satisfied: traitlets>=4.2 in /opt/conda/lib/python3.7/site-packages (from ipython==7.*->livelossplot) (5.0.5)\n",
      "Requirement already satisfied: pickleshare in /opt/conda/lib/python3.7/site-packages (from ipython==7.*->livelossplot) (0.7.5)\n",
      "Requirement already satisfied: setuptools>=18.5 in /opt/conda/lib/python3.7/site-packages (from ipython==7.*->livelossplot) (49.6.0.post20210108)\n",
      "Requirement already satisfied: matplotlib-inline in /opt/conda/lib/python3.7/site-packages (from ipython==7.*->livelossplot) (0.1.2)\n",
      "Requirement already satisfied: pygments in /opt/conda/lib/python3.7/site-packages (from ipython==7.*->livelossplot) (2.9.0)\n",
      "Requirement already satisfied: pexpect>4.3 in /opt/conda/lib/python3.7/site-packages (from ipython==7.*->livelossplot) (4.8.0)\n",
      "Requirement already satisfied: decorator in /opt/conda/lib/python3.7/site-packages (from ipython==7.*->livelossplot) (5.0.9)\n",
      "Requirement already satisfied: parso<0.9.0,>=0.8.0 in /opt/conda/lib/python3.7/site-packages (from jedi>=0.16->ipython==7.*->livelossplot) (0.8.2)\n",
      "Requirement already satisfied: ptyprocess>=0.5 in /opt/conda/lib/python3.7/site-packages (from pexpect>4.3->ipython==7.*->livelossplot) (0.7.0)\n",
      "Requirement already satisfied: wcwidth in /opt/conda/lib/python3.7/site-packages (from prompt-toolkit!=3.0.0,!=3.0.1,<3.1.0,>=2.0.0->ipython==7.*->livelossplot) (0.2.5)\n",
      "Requirement already satisfied: ipython-genutils in /opt/conda/lib/python3.7/site-packages (from traitlets>=4.2->ipython==7.*->livelossplot) (0.2.0)\n",
      "Requirement already satisfied: Jinja2>=2.9 in /opt/conda/lib/python3.7/site-packages (from bokeh->livelossplot) (3.0.1)\n",
      "Requirement already satisfied: typing-extensions>=3.7.4 in /opt/conda/lib/python3.7/site-packages (from bokeh->livelossplot) (3.7.4.3)\n",
      "Requirement already satisfied: PyYAML>=3.10 in /opt/conda/lib/python3.7/site-packages (from bokeh->livelossplot) (5.4.1)\n",
      "Requirement already satisfied: pillow>=7.1.0 in /opt/conda/lib/python3.7/site-packages (from bokeh->livelossplot) (8.2.0)\n",
      "Requirement already satisfied: tornado>=5.1 in /opt/conda/lib/python3.7/site-packages (from bokeh->livelossplot) (6.1)\n",
      "Requirement already satisfied: python-dateutil>=2.1 in /opt/conda/lib/python3.7/site-packages (from bokeh->livelossplot) (2.8.1)\n",
      "Requirement already satisfied: packaging>=16.8 in /opt/conda/lib/python3.7/site-packages (from bokeh->livelossplot) (20.9)\n",
      "Requirement already satisfied: MarkupSafe>=2.0 in /opt/conda/lib/python3.7/site-packages (from Jinja2>=2.9->bokeh->livelossplot) (2.0.1)\n",
      "Requirement already satisfied: pyparsing>=2.0.2 in /opt/conda/lib/python3.7/site-packages (from packaging>=16.8->bokeh->livelossplot) (2.4.7)\n",
      "Requirement already satisfied: six>=1.5 in /opt/conda/lib/python3.7/site-packages (from python-dateutil>=2.1->bokeh->livelossplot) (1.15.0)\n",
      "Requirement already satisfied: cycler>=0.10 in /opt/conda/lib/python3.7/site-packages (from matplotlib->livelossplot) (0.10.0)\n",
      "Requirement already satisfied: kiwisolver>=1.0.1 in /opt/conda/lib/python3.7/site-packages (from matplotlib->livelossplot) (1.3.1)\n",
      "\u001b[33mWARNING: Running pip as root will break packages and permissions. You should install packages reliably by using venv: https://pip.pypa.io/warnings/venv\u001b[0m\n",
      "Tensorflow version: 2.4.1\n"
     ]
    }
   ],
   "source": [
    "!pip install livelossplot\n",
    "import numpy as np\n",
    "import seaborn as sns\n",
    "import matplotlib.pyplot as plt\n",
    "import os\n",
    "%matplotlib inline\n",
    "\n",
    "from tensorflow.keras.preprocessing.image import ImageDataGenerator\n",
    "from tensorflow.keras.layers import Dense, Input, Dropout,Flatten, Conv2D\n",
    "from tensorflow.keras.layers import BatchNormalization, Activation, MaxPooling2D\n",
    "from tensorflow.keras.models import Model, Sequential\n",
    "from tensorflow.keras.optimizers import Adam\n",
    "from tensorflow.keras.callbacks import ModelCheckpoint, ReduceLROnPlateau,EarlyStopping \n",
    "from tensorflow.keras.utils import plot_model\n",
    "\n",
    "from IPython.display import SVG, Image\n",
    "from livelossplot import PlotLossesKerasTF\n",
    "import tensorflow as tf\n",
    "print(\"Tensorflow version:\", tf.__version__)\n",
    "import cv2"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 18,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T05:32:17.553548Z",
     "iopub.status.busy": "2022-11-17T05:32:17.553187Z",
     "iopub.status.idle": "2022-11-17T05:32:17.557999Z",
     "shell.execute_reply": "2022-11-17T05:32:17.556936Z",
     "shell.execute_reply.started": "2022-11-17T05:32:17.553511Z"
    }
   },
   "outputs": [],
   "source": [
    "train_dir ='../input/eyes-open-or-closed/dataset/train'\n",
    "test_dir  ='../input/eyes-open-or-closed/dataset/test'"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 55,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T05:57:50.142126Z",
     "iopub.status.busy": "2022-11-17T05:57:50.141731Z",
     "iopub.status.idle": "2022-11-17T05:57:51.014911Z",
     "shell.execute_reply": "2022-11-17T05:57:51.013856Z",
     "shell.execute_reply.started": "2022-11-17T05:57:50.142067Z"
    }
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "2 test detected\n",
      "\t 360 Open_Eyes images\n",
      "\t 240 Closed_Eyes images\n",
      "2 train detected\n",
      "\t 1640 Open_Eyes images\n",
      "\t 1760 Closed_Eyes images\n",
      "600\n"
     ]
    }
   ],
   "source": [
    "valSET = []\n",
    "for feature in os.listdir(\"../input/eyes-open-or-closed/dataset\"):\n",
    "    f_list=os.listdir(\"../input/eyes-open-or-closed/dataset/\" + feature)\n",
    "    print(str(len(os.listdir(\"../input/eyes-open-or-closed/dataset/\" + feature))) + \" \" + feature + \" detected\")\n",
    "    for state in f_list:\n",
    "        print(\"\\t\",str(len(os.listdir(\"../input/eyes-open-or-closed/dataset/\" + feature+\"/\"+state))) + \" \" + state + \" images\")\n",
    "        for img in os.listdir(\"../input/eyes-open-or-closed/dataset/\" + feature+\"/\"+state):\n",
    "            if feature==\"test\":\n",
    "                a=\"../input/eyes-open-or-closed/dataset/\" + feature+\"/\"+state+\"/\"+img\n",
    "                x=cv2.resize(cv2.imread(a),(86,86))\n",
    "                x = cv2.cvtColor(x,cv2.COLOR_BGR2GRAY)\n",
    "                y=state\n",
    "                valSET.append((x,y))\n",
    "print(len(valSET))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T05:13:16.324237Z",
     "iopub.status.busy": "2022-11-17T05:13:16.323943Z",
     "iopub.status.idle": "2022-11-17T05:13:20.735700Z",
     "shell.execute_reply": "2022-11-17T05:13:20.734734Z",
     "shell.execute_reply.started": "2022-11-17T05:13:16.324207Z"
    }
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Found 3230 images belonging to 2 classes.\n",
      "Found 600 images belonging to 2 classes.\n",
      "Found 170 images belonging to 2 classes.\n"
     ]
    }
   ],
   "source": [
    "width, height = 86, 86\n",
    "img_size = 86\n",
    "train_generator=tf.keras.preprocessing.image.ImageDataGenerator(rescale=1/255.0,\n",
    "                                                          rotation_range=7,\n",
    "                                                          horizontal_flip=True,\n",
    "                                                          validation_split=0.05\n",
    "                                                         ).flow_from_directory(train_dir,\n",
    "                                                                               class_mode = 'categorical',\n",
    "                                                                               color_mode=\"grayscale\",\n",
    "                                                                               batch_size = 8,\n",
    "                                                           target_size=(width,height),\n",
    "                                                                              subset=\"training\")\n",
    "validation_generator=tf.keras.preprocessing.image.ImageDataGenerator(rescale=1/255.0,\n",
    "                                                         ).flow_from_directory(test_dir,\n",
    "                                                                               class_mode = 'categorical',\n",
    "                                                                               color_mode=\"grayscale\",\n",
    "                                                                               batch_size = 8,\n",
    "                                                                               shuffle = False,\n",
    "                                                           target_size=(width,height))\n",
    "validing=tf.keras.preprocessing.image.ImageDataGenerator(rescale=1/255.0,\n",
    "                                                          rotation_range=7,\n",
    "                                                          horizontal_flip=True,\n",
    "                                                         validation_split=0.05\n",
    "                                                        ).flow_from_directory(train_dir,\n",
    "                                                                              batch_size = 8,\n",
    "                                                                              class_mode = 'categorical',\n",
    "                                                                              color_mode=\"grayscale\",\n",
    "                                                           target_size=(width,height),subset='validation',shuffle=True)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T05:13:20.737461Z",
     "iopub.status.busy": "2022-11-17T05:13:20.737103Z",
     "iopub.status.idle": "2022-11-17T05:13:20.784146Z",
     "shell.execute_reply": "2022-11-17T05:13:20.783196Z",
     "shell.execute_reply.started": "2022-11-17T05:13:20.737414Z"
    }
   },
   "outputs": [],
   "source": [
    "from keras.models import Sequential ,Model\n",
    "from keras.layers import Dense ,Flatten ,Conv2D ,MaxPooling2D ,Dropout ,BatchNormalization  ,Activation ,GlobalMaxPooling2D\n",
    "from keras.optimizers import Adam \n",
    "from keras.callbacks import EarlyStopping ,ReduceLROnPlateau"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T05:13:20.785854Z",
     "iopub.status.busy": "2022-11-17T05:13:20.785495Z",
     "iopub.status.idle": "2022-11-17T05:13:20.795017Z",
     "shell.execute_reply": "2022-11-17T05:13:20.794108Z",
     "shell.execute_reply.started": "2022-11-17T05:13:20.785808Z"
    }
   },
   "outputs": [],
   "source": [
    "optimizer=Adam(lr=0.001,beta_1=0.9,beta_2=0.99,decay=0.001/32)\n",
    "EarlyStop=EarlyStopping(patience=10,restore_best_weights=True)\n",
    "Reduce_LR=ReduceLROnPlateau(monitor='val_accuracy',verbose=2,factor=0.5,min_lr=0.00001)\n",
    "callback=[EarlyStop , Reduce_LR]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T05:13:20.796889Z",
     "iopub.status.busy": "2022-11-17T05:13:20.796505Z",
     "iopub.status.idle": "2022-11-17T05:13:23.347634Z",
     "shell.execute_reply": "2022-11-17T05:13:23.346687Z",
     "shell.execute_reply.started": "2022-11-17T05:13:20.796852Z"
    }
   },
   "outputs": [],
   "source": [
    "num_classes = 2\n",
    "num_detectors=32\n",
    "\n",
    "network = Sequential()\n",
    "\n",
    "network.add(Conv2D(num_detectors, (3,3), activation='relu', padding = 'same', input_shape = (img_size, img_size, 1)))\n",
    "network.add(BatchNormalization())\n",
    "network.add(Conv2D(num_detectors, (3,3), activation='relu', padding = 'same'))\n",
    "network.add(BatchNormalization())\n",
    "network.add(MaxPooling2D(pool_size=(2,2)))\n",
    "network.add(Dropout(0.2))\n",
    "\n",
    "network.add(Conv2D(2*num_detectors, (3,3), activation='relu', padding = 'same'))\n",
    "network.add(BatchNormalization())\n",
    "network.add(Conv2D(2*num_detectors, (3,3), activation='relu', padding = 'same'))\n",
    "network.add(BatchNormalization())\n",
    "network.add(MaxPooling2D(pool_size=(2,2)))\n",
    "network.add(Dropout(0.2))\n",
    "\n",
    "network.add(Conv2D(2*2*num_detectors, (3,3), activation='relu', padding = 'same'))\n",
    "network.add(BatchNormalization())\n",
    "network.add(Conv2D(2*2*num_detectors, (3,3), activation='relu', padding = 'same'))\n",
    "network.add(BatchNormalization())\n",
    "network.add(MaxPooling2D(pool_size=(2,2)))\n",
    "network.add(Dropout(0.2))\n",
    "\n",
    "network.add(Conv2D(2*2*2*num_detectors, (3,3), activation='relu', padding = 'same'))\n",
    "network.add(BatchNormalization())\n",
    "network.add(Conv2D(2*2*2*num_detectors, (3,3), activation='relu', padding = 'same'))\n",
    "network.add(BatchNormalization())\n",
    "network.add(MaxPooling2D(pool_size=(2,2)))\n",
    "network.add(Dropout(0.2))\n",
    "\n",
    "network.add(Flatten())\n",
    "\n",
    "network.add(Dense(2 * num_detectors, activation='relu'))\n",
    "network.add(BatchNormalization())\n",
    "network.add(Dropout(0.2))\n",
    "\n",
    "network.add(Dense(2 * num_detectors, activation='relu'))\n",
    "network.add(BatchNormalization())\n",
    "network.add(Dropout(0.2))\n",
    "\n",
    "network.add(Dense(num_classes, activation='softmax'))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T05:13:26.135395Z",
     "iopub.status.busy": "2022-11-17T05:13:26.135035Z",
     "iopub.status.idle": "2022-11-17T05:13:26.154190Z",
     "shell.execute_reply": "2022-11-17T05:13:26.153175Z",
     "shell.execute_reply.started": "2022-11-17T05:13:26.135363Z"
    }
   },
   "outputs": [],
   "source": [
    "network.compile(optimizer=optimizer,loss='categorical_crossentropy', metrics=[\"accuracy\"])"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T05:13:27.424137Z",
     "iopub.status.busy": "2022-11-17T05:13:27.423724Z",
     "iopub.status.idle": "2022-11-17T05:13:27.448203Z",
     "shell.execute_reply": "2022-11-17T05:13:27.447297Z",
     "shell.execute_reply.started": "2022-11-17T05:13:27.424068Z"
    }
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Model: \"sequential\"\n",
      "_________________________________________________________________\n",
      "Layer (type)                 Output Shape              Param #   \n",
      "=================================================================\n",
      "conv2d (Conv2D)              (None, 86, 86, 32)        320       \n",
      "_________________________________________________________________\n",
      "batch_normalization (BatchNo (None, 86, 86, 32)        128       \n",
      "_________________________________________________________________\n",
      "conv2d_1 (Conv2D)            (None, 86, 86, 32)        9248      \n",
      "_________________________________________________________________\n",
      "batch_normalization_1 (Batch (None, 86, 86, 32)        128       \n",
      "_________________________________________________________________\n",
      "max_pooling2d (MaxPooling2D) (None, 43, 43, 32)        0         \n",
      "_________________________________________________________________\n",
      "dropout (Dropout)            (None, 43, 43, 32)        0         \n",
      "_________________________________________________________________\n",
      "conv2d_2 (Conv2D)            (None, 43, 43, 64)        18496     \n",
      "_________________________________________________________________\n",
      "batch_normalization_2 (Batch (None, 43, 43, 64)        256       \n",
      "_________________________________________________________________\n",
      "conv2d_3 (Conv2D)            (None, 43, 43, 64)        36928     \n",
      "_________________________________________________________________\n",
      "batch_normalization_3 (Batch (None, 43, 43, 64)        256       \n",
      "_________________________________________________________________\n",
      "max_pooling2d_1 (MaxPooling2 (None, 21, 21, 64)        0         \n",
      "_________________________________________________________________\n",
      "dropout_1 (Dropout)          (None, 21, 21, 64)        0         \n",
      "_________________________________________________________________\n",
      "conv2d_4 (Conv2D)            (None, 21, 21, 128)       73856     \n",
      "_________________________________________________________________\n",
      "batch_normalization_4 (Batch (None, 21, 21, 128)       512       \n",
      "_________________________________________________________________\n",
      "conv2d_5 (Conv2D)            (None, 21, 21, 128)       147584    \n",
      "_________________________________________________________________\n",
      "batch_normalization_5 (Batch (None, 21, 21, 128)       512       \n",
      "_________________________________________________________________\n",
      "max_pooling2d_2 (MaxPooling2 (None, 10, 10, 128)       0         \n",
      "_________________________________________________________________\n",
      "dropout_2 (Dropout)          (None, 10, 10, 128)       0         \n",
      "_________________________________________________________________\n",
      "conv2d_6 (Conv2D)            (None, 10, 10, 256)       295168    \n",
      "_________________________________________________________________\n",
      "batch_normalization_6 (Batch (None, 10, 10, 256)       1024      \n",
      "_________________________________________________________________\n",
      "conv2d_7 (Conv2D)            (None, 10, 10, 256)       590080    \n",
      "_________________________________________________________________\n",
      "batch_normalization_7 (Batch (None, 10, 10, 256)       1024      \n",
      "_________________________________________________________________\n",
      "max_pooling2d_3 (MaxPooling2 (None, 5, 5, 256)         0         \n",
      "_________________________________________________________________\n",
      "dropout_3 (Dropout)          (None, 5, 5, 256)         0         \n",
      "_________________________________________________________________\n",
      "flatten (Flatten)            (None, 6400)              0         \n",
      "_________________________________________________________________\n",
      "dense (Dense)                (None, 64)                409664    \n",
      "_________________________________________________________________\n",
      "batch_normalization_8 (Batch (None, 64)                256       \n",
      "_________________________________________________________________\n",
      "dropout_4 (Dropout)          (None, 64)                0         \n",
      "_________________________________________________________________\n",
      "dense_1 (Dense)              (None, 64)                4160      \n",
      "_________________________________________________________________\n",
      "batch_normalization_9 (Batch (None, 64)                256       \n",
      "_________________________________________________________________\n",
      "dropout_5 (Dropout)          (None, 64)                0         \n",
      "_________________________________________________________________\n",
      "dense_2 (Dense)              (None, 2)                 130       \n",
      "=================================================================\n",
      "Total params: 1,589,986\n",
      "Trainable params: 1,587,810\n",
      "Non-trainable params: 2,176\n",
      "_________________________________________________________________\n"
     ]
    }
   ],
   "source": [
    "network.summary()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T05:13:29.769414Z",
     "iopub.status.busy": "2022-11-17T05:13:29.769003Z",
     "iopub.status.idle": "2022-11-17T05:18:12.377950Z",
     "shell.execute_reply": "2022-11-17T05:18:12.376845Z",
     "shell.execute_reply.started": "2022-11-17T05:13:29.769374Z"
    },
    "scrolled": true
   },
   "outputs": [
    {
     "data": {
      "image/png": "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BP/dvPzyy5k6dWrD/W+77TbGjh3LiBEjWLp0KQBFRUUcf/zxDBs2jKuuuorevXuzdevWCP8tRLfgua72CFHqXIlIFNOxKciV0wILdpSTluQnJWEfYxMDlcGRtyIibfSH/y5i8YadYX3Oob06c9upw/Z5+913383ChQuZN28en332GT/4wQ9YuHBhwzSjZ555hq5du1JRUcHBBx/M2WefTXp6+veeY8WKFbz88ss8+eSTnHfeebz++utccskle71Wt27dmDNnDo888gj33XcfTz31FH/4wx845phjuOWWW/jggw94+umnw/r+vSArNZFZ63Z8/0p1rkQkTHRscu7Y5MrOVWV1LX0bj7fdk/ZciYiLTJgw4XtjYv/+978zatQoJk2aREFBAStWrNjrMX379mX06NEAjBs3jrVr1zb53GedddZe95k+fToXXHABAFOmTCEtLS18b8YjstIS2VhSSaC20WTA+s6VwpWIuIBXj02u7Fw9cP5orLVN32it9lyJSNjs71O8SElO3v1h0meffcYnn3zCN998Q1JSEkcddVSTY2Tj43d/wBQbG9uw9GJf94uNjT3gunlpvqzUJGrrLJtLq8hKDYWq+hUVAYUrEWkbHZuc48rOFexndGKgKnipcCUiUSolJYXS0tImbyspKSEtLY2kpCSWLl3Kt99+G/bXP/TQQ3nttdcA+Oijj9ixY8cBHiF7anIce324qtGeKxGJPjo2Bbmyc7Vf9RuFFa5EJEqlp6dz6KGHMnz4cBITE8nMzGy4bcqUKTz22GMMGTKEQYMGMWnSpLC//m233caFF17I888/z+TJk+nRowcpKSlhfx03y6oPV8XlQNfglfXHJXWuRCQK6dgUZPa5fM4h48ePt7NmzWq/FyjdDPcPhB88AAdf2X6vIyKutWTJEoYMGeJ0GY6pqqoiNjYWn8/HN998w7XXXsu8efPa9JxN/Z0aY2Zba8e36YnDKJzHp8qaWgb//gN+efxAbjh2QPDKbavgobFw5hMw6vywvI6IeIeOTeE/NkHLj08e7FyFPhFU50pEpFXy8/M577zzqKurIy4ujieffNLpkqJOgj+Wbp3iWN/4XFfqXImItFpHOTZ5MFyF9lz5Fa5ERFpjwIABzJ071+kyol5WWtL3w5Vf0wJFRFqroxybXDvQYp+050pERDqA7NTEfQy0ULgSEYlW3gtX9VOYdJ4rERFxUFZaIoXFFdTVhfY+NywL1LRAEZFo5b1w1dC5SnS2DhER8bTstESqA3VsLQstVzcmGLDUuRIRiVoeDFc6z5WIiDiv/uTB31sa6EtQ50pEJIp5MFxpWaCIeEunTp0A2LBhA+ecc06T9znqqKM40JjxBx98kPLy8obvTz75ZIqLi8NWp9fsPtfVHvuu1LkSEY9w4/HJw+FKnSsR8ZZevXoxderUVj9+z4PXe++9R2pqahgq86b6zlWhOlci4nFuOj55N1xpFLuIRKmbb76Zhx9+uOH722+/nT/+8Y8ce+yxjB07lhEjRvDWW2/t9bi1a9cyfPhwACoqKrjgggsYMmQIZ555JhUVu3/Bv/baaxk/fjzDhg3jtttuA+Dvf/87GzZs4Oijj+boo48GoE+fPmzduhWABx54gOHDhzN8+HAefPDBhtcbMmQIV199NcOGDeOEE0743ut4XUqCny6J/j0mBiapcyUiUUvHJy+f50qdKxEJh/dvhk0LwvucPUbASXfv8+bzzz+fn//851x33XUAvPbaa3z44YfceOONdO7cma1btzJp0iROO+00jDFNPsejjz5KUlISS5YsIS8vj7Fjxzbcdtddd9G1a1dqa2s59thjycvL48Ybb+SBBx5g2rRpdOvW7XvPNXv2bP75z38yY8YMrLVMnDiRI488krS0NFasWMHLL7/Mk08+yXnnncfrr7/OJZdcEoa/JHfISk3cY1mgBlqISBg4cGwCHZ/Ai52r+oOW9lyJSJQaM2YMW7ZsYcOGDcyfP5+0tDR69OjBb3/7W0aOHMlxxx3H+vXr2bx58z6f44svvmg4iIwcOZKRI0c23Pbaa68xduxYxowZw6JFi1i8ePF+65k+fTpnnnkmycnJdOrUibPOOosvv/wSgL59+zJ69GgAxo0bx9q1a9v25l0mK22Pc135ErUsUESilo5Pnu5caRS7iITBAT7Fay/nnnsuU6dOZdOmTZx//vm8+OKLFBUVMXv2bPx+P3369KGysuW/pK9Zs4b77ruPmTNnkpaWxuWXX96q56kXH7/7g6zY2FgtC9xDVmoiX6/cirU2+CmuPwHKtztdlohEO4eOTaDjk/c6V4FKMLEQ671cKSLucf755/PKK68wdepUzj33XEpKSujevTt+v59p06axbt26/T7+iCOO4KWXXgJg4cKF5OXlAbBz506Sk5Pp0qULmzdv5v333294TEpKCqWlpXs91+GHH86bb75JeXk5ZWVlvPHGGxx++OFhfLfulZ2WSFl1LSUVNcErNNBCRKKc149P3ksYgUrttxKRqDds2DBKS0vJysqiZ8+eXHzxxZx66qmMGDGC8ePHM3jw4P0+/tprr+WKK65gyJAhDBkyhHHjxgEwatQoxowZw+DBg8nJyeHQQw9teMw111zDlClT6NWrF9OmTWu4fuzYsVx++eVMmDABgKuuuooxY8ZoCWAzZKftnhiYmhSnUewiEvW8fnwy1tp2e/LWGD9+vD3QLPs2efeXsPA/8Js17fcaIuJqS5YsYciQIU6X4SpN/Z0aY2Zba8c7VNJe2uP4tKCwhFP/MZ3HLx3HicN6wFvXw4qP4VfLwvo6IuJ+Oja1j5Yen7y5LNCv/VYiIuK8rLQ9znXlT4KAOlciItHKg+GqSpMCRUSkQ0hL8pMUF7t7YqA/AWq050pEJFp5L1zVVGjPlYiIdAjGmNC5rsqDV/gSobYK6uqcLUxERFrFe+EqUKVwJSJt1tH2q0Yzr/9dZqUlNloWGDo+aWKgiLSC1/89DbfW/H16MFxpWqCItE1CQgLbtm3TQSwMrLVs27aNhATv/rsc7FzVn+A+tCdY4UpEWkjHpvBq7fHJg6PYqyAu2ekqRCSKZWdnU1hYSFFRkdOluEJCQgLZ2dlOl+GY7LQkistrKKsKkFzfuaopB7o6WpeIRBcdm8KvNccnD4arCkhKd7oKEYlifr+fvn37Ol2GuET9xMD1xRUM9CcFr9RQCxFpIR2bOgYPLgus2r2mXURExGFZqfXj2Mt3L1vXOHYRkajkwXClPVciItJxZNd3rnZU7D4PozpXIiJRyXvhqqZS57kSEZEOI6NTPHGxMRQWV6hzJSIS5bwXrgJVu6cxiYiIOCwmxtArNUGdKxERF/BguFLnSkREOpaGc12pcyUiEtW8Fa6sDZ75XnuuRESkA2k411VD50rhSkQkGnkrXNWflFGdKxER6UCy05IoKq2ikrjgFQpXIiJRyZvhyq89VyIi0nHUj2PfXGGCVwS050pEJBp5LFxVBS/VuRIRkQ6k/kTChaU2eIU6VyIiUclb4ar+YKU9VyIi0oHUd64KdtYFr1DnSkQkKnkrXDV0rhSuRESk4+jZJYHYGMP6ktCJ7tW5EhGJSh4LV/UDLRSuRESk4/DFxtCjc+hcVwpXIiJRy2PhSnuuRESkY8pKDZ3ryp+k81yJiEQpj4Ur7bkSEZGOKTut/lxXCVCjPVciItHIY+Eq1LnyK1yJiEjHkpWWyKadlVhfggZaiIhEKY+FK+25EhGRjikrNZHaOkuNideeKxGRKOWtcFWjcCUiIh1T/bmuKolT50pEJEp5K1ypcyUiIh1UdloSAOV1fqgpd7gaERFpDY+FK53nSkREOqaeXYLHpl11fg20EBGJUj6nC4iohmmBGsUuIiIdS4I/loyUeHYGfBCjPVciItFInSsREZEOIis1kZJArDpXIiJRymPhqhJifBDrrYadiIhEh+y0RLZXxeokwiIiUcpbKSNQpa6ViIh0WFlpiWyrisHaSozTxYiISIt5q3NVU6H9ViIi0mFlpyZSbv2Y2iqoq3O6HBERaSFvhatAFfgSna5CRESkSVlpiVTY0IeAWhooIhJ1PBauKtW5EhGRDis7LSl4EmHQUAsRkSjkwXClPVciItIxZaUm7g5X6lyJiEQdD4Yrda5ERKRjSo73ERsXWr6uzpWISNTxWLiqAr/2XImISMeVnNwp+IU6VyIiUcdj4UqdKxER6dhSOoXClTpXIiJRx1vhqkZ7rkREpGPr0rkLALamzOFKRESkpbwVrjTQQkREOrjULp0B2LVrl8OViIhIS3ksXFUpXImISIeWnhrsXG0v2elwJSIi0lIeC1cV2nMlIiIdWve0VABKdipciYhEG4+FK3WuRES8wBgzxRizzBiz0hhzcxO3/8IYs9gYk2eM+dQY09uJOpuSmZ4KQElpqbOFiIhIi3ksXFWCX+FKRMTNjDGxwMPAScBQ4EJjzNA97jYXGG+tHQlMBf4S2Sr3rXNKCgC7dilciYhEG++Eq7o6qK1W50pExP0mACuttauttdXAK8Dpje9grZ1mrS0PffstkB3hGvfJhM7HWFGmgRYiItHGO+EqEDpfiPZciYi4XRZQ0Oj7wtB1+3Il8H5TNxhjrjHGzDLGzCoqKgpjifsR+hCwskKj2EVEoo0Hw1Wis3WIiEiHYYy5BBgP3NvU7dbaJ6y146214zMyMiJVFNUmnupKhSsRkWjjoXBVFbxU50pExO3WAzmNvs8OXfc9xpjjgP8HnGatrYpQbc1SF5uACVRSWlnjdCkiItICHgpXFcFL7bkSEXG7mcAAY0xfY0wccAHwduM7GGPGAI8TDFZbHKhxv6wvgQRqWF9c4XQpIiLSAh4KV+pciYh4gbU2AFwPfAgsAV6z1i4yxtxhjDktdLd7gU7Av40x84wxb+/j6Rxh4hJJMNWs36FwJSISTXxOFxAx9Xuu/NpzJSLidtba94D39rju1kZfHxfxolrAF5dIAtXqXImIRBl1rkRERDqY2Phkkkw1hepciYhElWaFq2ac6T7XGDPNGDM3dLb7k0PX9zHGVISWXMwzxjwW7jfQbDXacyUiItHB+BPp4gtoWaCISJQ54LLARme6P57guUJmGmPettYubnS33xFc0/6oMWYowaUYfUK3rbLWjg5r1a3R0LlSuBIRkQ7Ol0Cn2ACFWhYoIhJVmtO5OuCZ7gELdA593QXYEL4Sw6ThPFcKVyIi0sH5E0iKqWH9jnKnKxERkRZoTrhqzpnubwcuMcYUEuxa3dDotr6h5YKfG2MOb+oFjDHXGGNmGWNmFRUVNb/6lmgIV9pzJSIiHZwvkURTzdZd1VTW1DpdjYiINFO4BlpcCPzLWpsNnAw8b4yJATYCudbaMcAvgJeMMZ33fLC19glr7Xhr7fiMjIwwlbQHda5ERCRa+BOIs9UAmhgoIhJFmhOumnOm+yuB1wCstd8ACUA3a22VtXZb6PrZwCpgYFuLbpX6PVcaxS4iIh2dPwl/XfBDQQ21EBGJHs0JVwc80z2QDxwLYIwZQjBcFRljMkIDMTDG9AMGAKvDVXyLaFmgiIhEC18CsXXBDwXXbStzuBgREWmuA4arZp7p/pfA1caY+cDLwOXWWgscAeQZY+YBU4GfWGu3t8P7OLAaLQsUEZEo4U/E1FbTLSmW+YUlTlcjIiLNdMBR7NCsM90vBg5t4nGvA6+3scbwCFRCjB9iYp2uREREZP9CHwSOz05iXkGxs7WIiEizhWugRccXqFLXSkREokNof/DYXoms3LKLkooahwsSEZHm8FC4qtB+KxERiQ6hDwNHZcYBkFdY7GAxIiLSXB4KV+pciYhIlAh1roZm+AGYl1/sYDEiItJcHgpXleBXuBIRkSgQClcpsQH6ZyRr35WISJTwULhS50pERKKEL3ROxkAlo3PSmFdQTHAIr4iIdGTeCVc12nMlIiJRon6lRU0Fo3NT2VZWTcF2nUxYRKSj8064ClTt/iRQRESkI2vUuRqTkwrA3IIdztUjIiLN4qFwVanOlYiIRIdGnavBPVJI8Mdo35WISBTwWLjSnisREYkC9cerQCW+2BhGZHVRuBIRiQIeC1fqXImISBTwJwUva8oBGJ2TyqL1O6kK1DpYlIiIHIiHwlVVw2hbERGRDq1hWWAlAGNy06iurWPJxlIHixIRkQPxULhS50pERKJEw0CL4ITA0aGhFvPyNdRCRKQj8064qtGeKxERiRK+eMA0dK56dkmge0q89l2JiHRw3glXGmghIiLRwpjgMSvUuTLGMDonVeFKRKSD80a4qquFuhqFKxERiR7+hIbOFQT3Xa3dVs72smoHixIRkf3xRrgKhA5O2nMlIiLRwp8ENRUN39bvu5qv7pWISIflkXBVFbxU50pERKJFo2WBACOzuxBjYK7ClYhIh+WRcBXqXPkVrkREJEr4E7+3LDA53sfAzBTtuxIR6cC8Fa7UuRIRkWixR+cKYExuKvPyd1BXZx0qSkRE9scb4apGe65ERCTK7NG5guC+q52VAdZsK3OoKBER2R9vhKuGzlWis3WIiIg0VxOdq9E5aQDMyy92oCARETkQj4Sr+oEW6lyJiEiU8Cd+b1ogwEHdO5EcF6t9VyIiHZRHwlXo4KQ9VyIiEi2aCFexMYZROanMLdjhUFEiIrI/HglX6lyJiEiU8SXsXtbeyOicVJZuLKWyptaBokREZH88Eq7qR7Frz5WIiESJJgZaQDBcBeosC9eXOFCUiIjsj0fClTpXIiISZZoYaAEwOjcVQPuuREQ6IG+EqxrtuRIRkSjjT4Taaqj7/vK/7ikJZKUmMlcTA0VEOhxvhKuGzpXClYiIRIn6Y1ZT+65yU9W5EhHpgDwSrurPc6VwJSIiUcKfFLys2Xtp4JicVNYXV7CldO/gJSIizvFYuNKeKxERiRL+0AeCTYSr0TmpgE4mLCLS0XgnXMX4ISbW6UpERESaxxeacNvEssDhWV3wxRjmammgiEiH4pFwVaUx7CIiEl3207lK8McypGdnda5ERDoYj4SrSi0JFBGR6LKfzhUElwbmFRZTW2cjWJSIiOyPN8JVTaWGWYiISHTZT+cKguGqrLqWlVt2RbAoERHZH2+Eq4DClYiIRJn65ez7CFdjQicTnpu/I0IFiYjIgXgkXFUpXImISHRpWBbYdLjq2y2ZLol+ne9KRKQD8Ui4qtCeKxERiS4NywKb3nNljGFUjk4mLCLSkXgkXKlzJSIiUSaxa/CydMM+7zI6J5Xlm0vZVRWIUFEiIrI/HglXlbs/ARQREYkGianQbSDkz9jnXcbkplJnIa+wOGJliYjIvnkkXKlzJSIiUSh3EhTMgLq6Jm8enZ0KoKWBIiIdhDfCVY32XImISBTKnQyVxbB1WZM3pyXH0Sc9SScTFhHpILwRrgJVu6cuiYiIRIvcScHL/G/2eZfRoaEW1upkwiIiTvNIuKpU50pERKJPWl9I7g753+7zLmNy09hSWsXGkqanCoqISOR4KFxpz5WIiEQZY4Ldq/2Eq9E5qQDM1dJAERHHeShcqXMlIiJRKHcyFK+DnU2PZB/SszNxvhjmFeyIcGEiIrIn94er2gDUBcCvPVciIhKFGvZdNd29ivPFMKxXZ00MFBHpADwQrqqCl+pciYhINOoxAvxJ+993lZPGgvUl1NQ2PbJdREQiw/3hqia0wVd7rkREJBrF+iF7PBTsZ99VbiqVNXUs21QawcJERGRP7g9XAYUrERGJcrmTYdMCqGo6PI2pH2qhpYEiIo5SuBIREenocieBrYPCmU3enJ2WSHpynE4mLCLiMA+FK+25EhGRKJV9MJiYfe67MsYwJjdVEwNFRBzmoXClzpWIiESp+BTIHH7A812tKiqjpLwmgoWJiEhjHghXoWmBfoUrERGJYrmToXAW1DYdnkbnpAEwv7A4gkWJiEhj7g9XNRXBS3WuREQkmuVOgpqy4GCLJozM6YIx8PnyoggXJiIi9dwfrgI6z5WIiLjAAU4m3DnBz5mjs3jmqzV8tmxLBAsTEZF6HghX9XuuEp2tQ0REpC0694LU3P2e7+qPZw5nUGYKP3tlHvnbyiNYnIiIgCfClTpXIiLiErmTg50ra5u8OSnOxxOXjgfgmudnUV4diGR1IiKe54FwpT1XIiLiErmTYNdm2LFm33dJT+LvF45h2eZSfvP6Auw+gpiIiISfB8KVOlciIuISOfvfd1XvyIEZ/PrEQfx3/gae+nLfQUxERMLLA+EqtOfKrz1XIiIS5TIGQ0KXA4YrgGuP7M9Jw3vw5/eX8PXKrREoTkRE3B+uakLhKladKxERiXIxMcHuVTPClTGGe88dRf+MTlz30hwKd2jAhYhIe3N/uApUQmxc8IAkIiIS7XInwdZlULbtgHftFO/jiR+OJ1Bn+ckLs6msqY1AgSIi3uX+xBGo0hh2ERFxj/rzXRXMaNbd+3ZL5sHzR7Nw/U5++4YGXIiItCcPhKtKDbMQERH36DU2uCJjP+e72tOxQzL5v+MG8p8563n267XtV5uIiMd5JFxpDLuIiLiEPwF6jWnWvqvGbjjmII4bkskf313CjNUHXlIoIiIt55Fwpc6ViIi4SO4kWD8Haiqa/ZCYGMMD548it2sS1700h40lzX+siIg0jwfCVVXwUz4RERG3yJkEdTWwYW6LHtY5wc8TPxxHRXUtP3lhDlUBDbgQEQkn94ermgotCxQREXfJmRi8zP+mxQ89qHsK9583mvkFxdz65iINuBARCSP3h6tAlcKViIjHGGOmGGOWGWNWGmNubuL2I4wxc4wxAWPMOU7U2CbJ6dBtEOQ3b2LgnqYM78H1Rx/Eq7MKeHFGfpiLExHxLg+EKw20EBHxEmNMLPAwcBIwFLjQGDN0j7vlA5cDL0W2ujDKnRScGFhX16qH/9/xAzlqUAa3v72I79ZsD3NxIiLe5IFwVaWBFiIi3jIBWGmtXW2trQZeAU5vfAdr7VprbR7QumTSEeROgsoSKFraqofHxhj+dsEYcrsmce0Ls1lfrAEXIiJt5YFwpT1XIiIekwUUNPq+MHRdixljrjHGzDLGzCoqKgpLcWFTfzLhVuy7qtcl0c+Tl42nOlDHNc/NoqJaAy5ERNrCA+FKe65ERKR1rLVPWGvHW2vHZ2RkOF3O96X1hU6ZUNC6fVf1+md04u8XjmHxxp38eup8DbgQEWkDD4SrSo1iFxHxlvVATqPvs0PXuYsxwe5VGzpX9Y4e3J2bThzMO3kbeeSzVWEoTkTEm9wfrmo00EJExGNmAgOMMX2NMXHABcDbDtfUPnInQ3E+lLQ9O/7kyH6cNqoX9320jE8Wbw5DcSIi3uP+cBWo1EALEREPsdYGgOuBD4ElwGvW2kXGmDuMMacBGGMONsYUAucCjxtjFjlXcRvUn++q4Ns2P5UxhnvOHsmwXp35+avzWLG5tM3PKSLiNe4OV7UBsLXgS3S6EhERiSBr7XvW2oHW2v7W2rtC191qrX079PVMa222tTbZWpturR3mbMWt1GMk+JNbfb6rPSXGxfLEpeNJ8Mdy9XOzKCmvCcvzioh4hbvDVaAyeKnOlYiIuFGsD7LHh2XfVb1eqYk8dslY1hdXcP3LcwjURu+0ehGRSPNIuNKeKxERcancybB5IVTuDNtTju/TlTtPH86XK7Zy9/utO4+WiIgXeSRcqXMlIiIulTsRbB0Uzgzr014wIZfLJvfmqelreH12YVifW0TErVwerqqCl37tuRIREZfKPhhMTJvPd9WU350ylMn90rnljQXMKygO+/OLiLiNu8NVTUXwUp0rERFxq/gU6DEirPuu6vljY3j44rF0T4nnmudmsXlnZdhfQ0TETdwdruo7V9pzJSIibpY7GQpnQW34p/t1TY7jyR+OZ1dVgB8/P5vKmtqwv4aIiFu4PFxpoIWIiHhAzkSoKYdNee3y9EN6duaB80Yxr6CY296KzlOCiYhEgsKViIhItMudFLwM0/mumjJleE9+cmR/Xp1VwMy129vtdUREoplHwpX2XImIiIt17gWpvdtl31VjNx57ED06J3DHfxdTV2fb9bVERKKRR8KVOlciIuJyuZMh/1uw7Rd6kuJ83HzSYBasL2HqHI1nFxHZk8vDVf0odoUrERFxudyJULYFtq9u15c5fXQvxuSmcu+Hy9hVFWjX1xIRiTbuDlcNo9gVrkRExOVyJwcv2+F8V40ZY7jt1GEUlVbx8LSV7fpaIiLRxt3hqmEUu/ZciYiIy3UbBPFdoHBmu7/U6JxUzhqTxdNfriF/W3m7v56ISLRoVrgyxkwxxiwzxqw0xtzcxO25xphpxpi5xpg8Y8zJjW67JfS4ZcaYE8NZ/AE17LlKjOjLioiIRFxMDGQOg82LI/JyN00ZTGyM4U/vLYnI64mIRIMDhitjTCzwMHASMBS40BgzdI+7/Q54zVo7BrgAeCT02KGh74cBU4BHQs8XGepciYiIl2QOhS1L2nWoRb0eXRL46VH9+WDRJr5Zta3dX09EJBo0p3M1AVhprV1tra0GXgFO3+M+Fugc+roLsCH09enAK9baKmvtGmBl6PkiI1ABsfFgTMReUkRExDHdh0JVCZREZpLf1Uf0Iys1kTveWUytRrOLiDQrXGUBBY2+Lwxd19jtwCXGmELgPeCGFjwWY8w1xphZxphZRUVFzSy9GQJVGmYhIiLekTkseLl5UUReLsEfyy0nD2bJxp28OrPgwA8QEXG5cA20uBD4l7U2GzgZeN4Y0+znttY+Ya0db60dn5GREaaSCO650hh2ERHxiu5DgpdbIhOuAH4woicT+nTl/o+WsbOyJmKvKyLSETUnAK0Hchp9nx26rrErgdcArLXfAAlAt2Y+tv3UVGq/lYiIeEdCF+iSE7GhFhAczX7rqUPZXl7NQ5+uiNjrioh0RM0JVzOBAcaYvsaYOIIDKt7e4z75wLEAxpghBMNVUeh+Fxhj4o0xfYEBwHfhKv6AApVaFigiIt6SOQy2RC5cAQzP6sK547L519drWbO1LKKvLSLSkRwwXFlrA8D1wIfAEoJTARcZY+4wxpwWutsvgauNMfOBl4HLbdAigh2txcAHwHXW2tr2eCNN0p4rERHxmu5DYetyCFRH9GV/deIg4n2x3PVuZIOdiEhH4mvOnay17xEcVNH4ulsbfb0YOHQfj70LuKsNNbaeOlciIuI1mcOgLhAMWD2GR+xlu6ckcN3RB3HPB0v5ckURhw8I4x5qEZEoEa6BFh1TQHuuRETEY7qHTkUZ4aWBAD86rA+5XZO4853FBGrrIv76IiJO80C4UudKREQ8pNsAiPFHbBx7Y/G+WH578hCWb97FS9/lR/z1RUSc5vJwVaVR7CIi4i2xfsgY5EjnCuDEYZlM7pfOAx8vp7g8svu+RESc5u5wVVOhzpWIiHhP96ERHcfeWP1o9p0VNTz4iUazi4i3uDtcBaq050pERLwncyjsLISKYkdefkjPzlwwIZfnv13Hyi2ljtQgIuIEl4erSvAlOl2FiIhIZHUfFrx0aGkgwC+PH0hSXCy3v72YiurInYVFRMRJLg9X6lyJiIgHZYYmBjow1KJeeqd4bpoymOkrt3LM/Z/x1rz1WGsdq0dEJBLcG66shYD2XImIiAd1zoL4Lo52rgAundSbf/9kMt06xfOzV+Zx1qNfMzd/h6M1iYi0J/eGq7oA2DqFKxER8R5jgicTdmioRWMH9+nKW9cdyl/OGUnhjgrOfORr/u/VeWwqqXS6NBGRsHNvuAqE/tHWKHYREfGizKHBzlUHWIoXE2M4b3wO0351FD89qj/vLtjI0fd9xt8+WaH9WCLiKu4NVzWhcKXOlYiIeFH3oVC1E0oKnK6kQad4HzdNGcynvziSowdn8NdPlnPs/Z/x9vwN2o8lIq7g3nBV37nSQAsREfGizNDEwA6wNHBPOV2TeOTicbxyzSRSk+K48eW5nPPYN8wvKHa6NBGRNnFxuKoKXmoUu4iIeFH3IcHLLc5NDDyQSf3S+e8Nh3HP2SNYt62M0x/+il+8No+C7eVOlyYi0io+pwtoN+pciYiIlyV0gS45HbJz1VhsjOH8g3M5eURPHp62imemr+HteRs4Z1w21x19EDldk5wuUUSk2VzcudKeKxER8bjMYY6PY2+ulAQ/N580mM9vOoqLJ+bynznrOfq+z7jlP3kU7lAnS0SigwfClTpXIiLiUd2HwtblEKh2upJm69klkT+cPpzPbzqKiybm8vrs+pC1QCFLRDo894crv/ZciYiIR2UOC573cetypytpsZ5dErkjFLIuODiX12cXcvR9n/HbNxawvrjC6fJERJrk3nBVo86ViIh4XPehwcsoWRrYlJ5dErnzjOF89utgyJo6q5Cj7p3G/1PIEpEOyL3hSnuuRETE67oNgBg/bO64EwObq1fq7pB1/sE5vDargKPuncbv3lxAaWWN0+WJiACuDlf1o9gVrkRExKNi/dBtYFR3rvbUKzWRP54xgs9+fTTnH5zDy98V8MvX5uskxCLSIbg4XKlzJSIiQuawDj+OvTWyQiHrtycP4aPFm3nyy9VOlyQi4oVwpT1XIiLiYZlDYWchVOxwupJ28aND+3DyiB7c88EyZqze5nQ5IuJxHghX6lyJiIiHdR8WvNyyxNk62okxhnvOHknvrklc//JctpRWOl2SiHiYi8NV/Z4rda5ERMTDMkMTA10w1GJfUhL8PHLJWEora7jx5bkEauucLklEPMq94aqmIti1MsbpSkRERJzTOQviu7hqqEVTBvfozF1njODb1du5/+PoO6+XiLiDe8NVoEpdKxEREWNcO9RiT2ePy+bCCbk8+tkqPlm82elyRMSDXByuKsGX6HQVIiIizsscGuxceWBc+W2nDmV4Vmd+8do88reVO12OiHiMi8OVOlciIiIAdB8KVTuhpMDpStpdgj+WRy8eB8BPX5pNZU2twxWFV2llDe/kbaCuzv1BWSQauThcVWhSoIiICASXBYInlgYC5HRN4oHzRrNw/U7+8F93ved7PljK9S/N5eFpK50uRUSa4OJwpc6ViIgIAN2HBC+3uHdi4J6OG5rJtUf15+Xv8nl9dqHT5YTFppJKXptZSEq8jwc+Wc6XK4qcLklE9uDicFUJfu25EhERIaELdMnxTOeq3i+PH8ikfl35f28uYOmmnU6X02aPf7GKWmuZeu0hDOjeiZ+9Mo8NxRVOlyUijbg3XNVUqnMlIiJSL3OY68ex78kXG8PfLxxD5wQ/174wh9LKGqdLarWi0ipempHPmWOyGNQjhUcvGUd1oI6fvjiH6oDO6yXtz3pgIE44uDdcBSq150pERKRe96GwdTkEqp2uJKK6pyTwj4vGkr+9nJum5kXtL4hPfbmamto6rjv6IAD6Z3TiL+eMZF5BMXe9663QLJH39PQ1jPrDR/zlg6WUVETvhxSR4OJwVaVwJSIiUi9zGNQFggErUorzYd5LkXu9fZjQtyu/mTKI9xdu4pmv1jpdTottL6vm+W/XceqoXvTtltxw/ckjenLVYX159pt1vDVvvYMVips9/vkq7nxnMRkp8Tzy2SqOvHcaT36x2nWTOMPFxeFKnSsREZEG3YcGLyO5NPC9X8Ob10L+t5F7zX24+vB+nDA0kz+/t4RvVm1zupwWeWb6Gipqark+1LVq7DcnDebgPmnc/PoClm8udaC6lqmsqeXip77l2Ps/46kvV1Nc7q1OanOt2FzKppJKp8vg4Wkr+fP7SzllZE8+/PkRvHvjYYzKTuWu95ZwzH2f8e9ZBdTqtADf4/JwpT1XIiIiAHQbADF+2ByhiYEb5sHyD4Jff3FfZF5zP4wx3HfeKHqnJ/Gjf83k65VbnS6pWUoqanj267WcNLwHAzJT9rrdHxvDPy4aS3K8j5+8MJtdVQEHqmyeQG0d1780h69XbSPBH8sf313CxD99yi9fm8/c/B2OLdmck7+D376xgC07nQ8zAC98u46T/vYlZz/6Ndt2VTlWx0OfruDeD5dx+uhePHj+aHyxMQzr1YVnfzSBl66eSEbnBH49NY+T/vYFHy/eHLVLbsPN5eFKnSsREREAYv3QbWDkOldf3BucUnjoz2Hlx8Gw5bDOCX5euWYyvdOTuPxfM5m2dIvTJR3Qv75aS2lVgOuPHrDP+2R2TuChC8ewdmsZv+mg+8qstdzynwV8smQLd5w+nHdvPJx3bzyMs8dl8/7CjZz5yNec8tB0Xv4un7IIBcTKmlruencxZz/6NS/NyOfSp79ztJNWU1vH795cwO/eXMi43mkU7ari+pfmEqiN/MCSBz9Zzv0fL+esMVk8cF4wWDV2SP9uvPnTQ3j04rEEai1XPzeLcx/7hllrt7fodXZVBZibv4NXZ+ZzzwdL+XZ1dHWVm2I62v+A48ePt7NmzWr7E93VEw6+Ek74Y9ufS0REIs4YM9taO97pOuqF7fjkpNevhnVfwS/aOWBtWgCPHQZH3QKTroW/joB+R8L5z7fv6zbTjrJqLn1mBss2lfLQhWOZMryH0yU1qbSyhsPumcbBfbry1GUH/l/hsc9Xcff7S7n1lKH86LC+rX7dQG3dXr9Mt9Xd7y/lsc9X8bNjB/B/xw/83m2llTW8OW8DL367jqWbSkmJ93Hm2CwuntibQT327taFw8y127lpah5rtpZx0cRcjhyYwQ0vzWVIr868eNVEOsX72uV192XbriqufXEO363Zzo+P6MdNUwbz5tz1/PLf87nysL78/pShEanDWstfP17O3/+3knPGZXPP2SOJjTH7fUygto7XZhXy4CfL2VJaxXFDMrlpyiAGNuq0VgVqWbWljOWbS1m2uZTlm4KXhTt2n0rAGLAWjhuSyS0nD6Z/Rqd2e59ttb/jU2T/y4kUa6GmQp0rERGRxjKHwoLXoGIHJKa13+t8cS/Ed4aJPw52ryZcDV/eD0XLIGNQ+71uM6Ulx/HiVZO44p/fcd1Lc3jgvFGcPjrL6bL28vy36yipqOHGY/fea9WUHx/RjznrdvCn95YwMrsL4/t0bfZrWWuZk7+Dp6ev4cNFmzlhaCZ/OWckKQn+1pbf4KkvV/PY56u4eGIuPz9u7w5cSoKfSyf15pKJucxet4MXZ+TzyncFPPfNOg7uk8Ylk3ozZXgP4n2xba6lvDrAXz5YxrPfrCUrNZGXrprIIQd1A+Chi8bw0xfncM1zs3jm8oNJ8Lf99Zpj8YadXP3cLIp2VfHX80dx5phsAM4el82C9SU8PX0NI7K6cMaY9v1v1FrLfR8t4+Fpqzh/fA5/PmsEMQcIVhA85cFFE3M5c0wWz3y1hsc+X8WUB7/g5BE9qbOWZZtKWbutvGFvlj/W0D+jE2Nz07hwQi4DundiUI8UMlLi+edXa3n0s1Wc8NcvuHhiLj87dgDpnaJrm487O1eBavhjBhzzOzji1+EpTEREIkqdq3aw/CN46Vy44n3ofUj7vMbmxfDo5ODx95jfBa8r2wYPDochp8FZj7fP67ZCWVWAK5+dyYw127nnrJGcd3BOm56vtLKGJ79YTZwvhuuOPghjDvyL6b6UVwc47J5pjMgK7nFprpKKGk77x3Qqa2p554bDyUjZ/y+mNbV1vL9wE09PX8P8gmK6JPo5alAG7+RtpHd6Eo9dMu57HYiW+s+cQn7x2nxOHtGDhy4ce8AuSL3tZdVMnV3AizPyWbetnNQkPz8Y0ZOzxmYxNjetVX+336zaxm9ezyN/ezmXH9KHX584iOQ9OlT19R4/NJNHLh6LP8wdvD29v2Ajv3htPp0TfTxx6XhG5aR+7/aa2joufnIGeeuLmfqTQxie1aVd6rDWcs8Hy3js81VcOCGXu84Y3qxg1ZQdZdU8+vkqXpqRT0ZKPAMzOzEoM4WBPVIYlJlCn27J+/173bqrir99soKXvssnyR/LT48+iCsO7ROxsNsc+zs+uTNcVe6Eu3PghLvgkOvDU5iIiESUwlU7KCmEvw6Dk+8LdpPaw9QfwfIP4ecLIKlR5+SD38KMx+CG2dC19UvWwq2iupYfvzCbL5YXccfpw/jh5D4tfo5AbR0vzyzgwY+Xs60suGfnxmMO4hcntL5L99SXq/nju0t4/drJjOvd/A4UBDshZz7yFWNz03j+yglNLvErqajhle/yefbrtWwoqaRvt2R+dGgfzh6XTVKcj29Xb+P6l+ZSXh3gnrNHcuqoXi1+D9OWbeHqZ2cxoW9X/nnFwa3qPNXVWaav3MrU2YV8tHgTlTV15HRN5IzRWZwxJqtZS8d2VQW4+/0lvPBtPn3Sk/jLOaOY0Hfff6fPfr2W295exJljsrj/3FGtDhn7U1dnefDTFfz90xWMyU3l8UvG0b1z0yuuikqrOPWh6cTGGP57w2F0TY4Lay3WWv703hKe/HINl0zK5Y7TWh+swmnlllLufn8pnyzZQlZqIjdNGcSpI3t1iNr2d3xy50CLQGjai6YFioiI7NY5C+K7tN9Qi6LlsPA/weCWtMcvr4fcADGx8NXf2ue1WykxLpYnfziO44dmcutbi3jyi9XNfqy1lv8t3cyUv33J799cSP/unXjrukM5f3wOf//fSp6ZvqZVNVXW1PL4F6s5pH96i4MVwNBenbnrzBF8s3obD3z8/fOardtWxu1vL2Lynz/lz+8vpXd6Mk9fNp5Pf3Ekl07uQ1JcsJMzqV867954GEN7duaGl+fyh/8uoqYFgxVmr9vBtS/MZnDPFB6/dFyrl/TFxBiOGJjB3y8cw6zfHc/9546iT3oyD09bybH3f85p/5jOM9PXUFTa9FS9L1cUceJfv+DFGflcdVhf3v/ZEfsNVgCXHdKHX50wkDfmruf2/y4K+4CQsqoA1744m79/uoJzxmXz8tWT9hmsADJS4nns0nEUlVZxw8tzwjrgwlrLne8Eg9Vlk3tz5+kdI1gBHNQ9hacuO5iXrppIapKfn70yjzMe+YoZHXzohTv3XDWEK+25EhERaWBMcN9Ve41j//J+8CfC5CZWjXTuCWMugbkvwJE3QeeWd0LaS7wvlkcuHsvPX53HXe8toaKmlhuO2f+yvsUbdnLXe4v5auU2+qQn8fil4zhhaCbGGIb16kxJRQ13vLOYLol+zh6X3aJ6Xp1ZQFFpFX+/YEyr39M547KZvW47j3y2ijG5aaQk+Hh6+ho+WbIZX4zh1FG9uPKwvgzrte9lZpmdE3j5mkn86b0l/POrtSwoLOHhi8eSuZ8gAMFzNP3oXzPJ7JzAPy+fEJZ9WwCd4n2cPS6bs8dls3lnJf+dv4E35q7njncWc9d7SzjsoG6cOSaLE4ZlEqiz/OndJbwys4B+GclM/ckhjOvd/H2G1x19EKWVAR7/YjWdE/z86sTw7BUs2F7O1c/NYvnmUn5/ylB+dGifZi1xHJ2Tyh/PGM5Nr+dx74fLuOXkIW2uxVrLH/67mH99vZYrDu3DracMbdNS1vZyyEHd+O/1h/HG3PXc++Eyzn/iW04YmsnNJw2mXwcceuHScBX69ELhSkRE5Psyh0Hea8HhT+H8RWrbquCwjEk/heRuTd/n0J/B7Gfh63/AlD+F77XDwB8bw98vGEOCL5YHPl5ORU0tN504aK9fNjfvrOT+j5bx79mFdEn0c9upQ7l4Ym/ifLsXA/liY/jbhaP50b9mctPreXRJ9HPc0Mxm1VEVqOWxz1dxcJ80JvVredeqsdtOHcaC9SX8+PlZ1FlIS/Jz/dEHcemk3vvtlDTmj43htlOHMSY3jZtfz+MHf5/OwxeNYWK/9Cbvv6G4gh8+8x1xvhie/9HEA+75aq3MzglcdXg/rjq8H8s3l/Lm3PW8NW8DP391HklxsSTF+dheVsWPj+zH/x03sMX7dYwx3HzSYHZW1vCPaStJSfDx4yP7t6nmr1dt5boX51Bn4dkfTeDwARktevx5B+eQt76Yx79YzfCsLq1aqlmvrs5y29uLeP7bdVx9eF9+e/KQDhms6sXEGM4el83JI3ry9PTVDUMvRuWk0q1THN06xZPeKZ6MRl936xRHeqd4Oif4IvreXBquQp0rv8KViIjI93QfClU7oaQAUnPD97xfPgCxcXDIjfu+T1ofGHkezP4nHP5LSG76F3SnxMYY7j1nJAn+GB79bBUV1bXcdmrw0/zy6gBPfLGaxz9fTaCujqsO68v1Rw+gS1LTXZl4XyyPXzqei5/8lutemsNzP5qwz0DS2Ouz17OxpJJ7zh7Z5l8IE/yxPHrxOO58ZzFHDerOmWOySIxr3fK800b1YnCPFH7ywmwuemoGN08ZzFWH9/1ejTvKqrn06Rnsqgzw6o8nk5ue1Kb6m2tgZgo3TRnMr04YxMy123lz3gbWF1fwi+MHMnqPAREtYYzhj2eMoLQywJ/fX0rnRD8XTmj5/zPby6p5bVYB9364jL7dknnqh+Pp0y25VTXdesowlmws5aapeRzUvRNDenZu0eOttXyzaht/+3QFM9Zs58dH9uPmKYM7dLBqLDEuluuPGcD5B+fy2OerWLxhJ2u2ljFz7Q52lFfT1ArOOF8M3ZKDQWtsbip/OH14u9boznBVo2WBIiIiTcocFrzcvDh84WrHWpj/Mky4BlIO0KE57Bcw/xX49hE49vfhef0wiokx/PGM4cT7YnnmqzVUBWoZk5vGfR8uY0tpFT8Y0ZPfTBncrODQKd7HP6+YwHmPf8NVz87i5Wsm7XfaW01tHY98tpJROakcPmAf3b8WyumaxBM/DM9cmIGZKbx13aH8+t953PXeEuYW7OAv54yiU7yP8uoAV/xrJgU7Knj+RxMY2qtlv/SHQ0yMYWK/9GaF2OaKjTE8cN5oyqoC/PaNBXSK9zWrY7SqaBefLN7MJ0s2M3vdDuosHDekO389f3SblknG+WJ49OKxnPLQdH78/Gzevv5QUpMOPODCWstny4t46NMVzMkvpntKPHeeMZxLJuZGTbBqLCMlfq9zfwVq69heXs3W0mq27qpiW1lV8Ov6y11V1EVgjp87w5UGWoiIiDSte2ivxpZFMGhKeJ7zywcgxhdc9ncgGQNh6Gnw3ZNw6I3B82B1MMYYfn/KEBLjYnh42ipe/q6A0TmpPHLx2BadOwqga3Icz185gXMe/YbLnvmOf/9k8j73ibwxdz2FOyr4w2nDOuwvvCkJfh69ZCxPfrmau99fyrJNpfzjorHc/f5S8gqLefSScWENNx1BnC+GRy4ex2X//I7/e3UeneJ9HD24+/fuE6itY/a6HXyyZDOfLNnCmq1lAAzr1ZkbjhnAcUMyGZ7VOSw/1+6dE3j0knFc8MQ33PjKPP55+cH7HHFfV2f5eMlm/vG/lSxYX0JWaiJ3njGcc8dld6jR5uHgi42he0oC3VOcba64NFzV77lKdLYOERGRjiahC3TJCXauwqE4H+a9BOMuDw6taI7DfwmL3woGrCN+FZ46wswYw69PHEyf9GSS4nycPKJHq38x7tklkeevnMC5j33DpU9/x9RrJ9Ozy/d/RwnU1vHItJUM69WZY/b4xb2jMcZwzRH9GZGVyg0vz+Gkv30JwN1njeDEYT0crq59JMbF8vRl47noyRn85IXZPBfqzn2xfCufLNnMtGVbKC6vIS42hsn90/nRYX05dnB3eqW2z++i43qnccfpw7nlPwu476Nl/GbK4O/dXltneX/hRv7xv5Us3VRK7/Qk7jl7BGeOyf7e/kAJP5eGq4rgpTpXIiIie8scFr6JgdMfDF4e9vPmP6bnKBhwQnBp4KRrIa51+08i4dzxbTuxcL1+GZ149kcTuOCJb7n06e/4948nk9bofEXv5G1k7bZyHrtkbIftWu1pcv903rnhcH735kIO6Z/OBa3YjxRNUhL8PPuj4DLPHz7zHXXWUlNrSUvyc8zg7hw/JJPDB2bQKT4yv15fOCGXvMISHv1sFcN7deEHI3sSqK3j7fkbeHjaSlYVldE/I5m/nj+KU0f2avJ8ZxJ+Lg1XmhYoIiKyT92HwspPIFANvjackHTnBpj7fHDEepeWjRvn8F/BMyfA7H/B5OtaX0MUGZ7VhacuG88Pn/mOy/81kxevmkineB91dZZ/TFvJoMwUThgaXZ2fHl0SeOqyDnOu73bXNTmOF66cyO/eXED/jE4cNzSTsblp+1yW195uP20oSzft5NdT55O/vZyXv8snf3s5g3uk8PBFY5kyvIdjtXmVOyOs9lyJiIjsW+YwqAvA1uUHvu/+fPU3sHVw2P+1/LG5E6HP4fD1Q7s/FPWASf3SefiisSwMjUivCtTy/sJNrNyyi+uOOajDnMBV9i0YKA/mlpOHcHCfro6Gl3hfLI9dMo7keB/3fLCULol+nrh0HO/deDg/GNlTwcoBLu1c1Y9i154rERGRvXQPTdnashh6tHIscemmYNdp1AWQ1rt1z3H4L+H5M2DeizD+R617jih0/NBM/nL2SH757/n87OV5rN1WRr+MZH4wopl71kQayeycwKvXTGLTzkom90uPmmWlbuXOcFWjzpWIiMg+dRsAMf627bv6+iGorQkGpNbqdxRkjQvu2xrzQ4h1568lTTl7XDbFFTXc+U5wsMj9545Sl0FarV9Gp31OoZTIcvmyQO25EhER2UusH7oNbH242lUEM58OnhC4a7/W12FMcO9V8TpYOLX1zxOlrjysLzdNGcSRAzM4ffSBz50kIh2fS8NVFWCCZ4oXERGRvWUOCy4LbI1vHoLaqrZ1reoNnALdhwXPlVVX1/bnizI/Peognv3RBE1yE3EJd/6fHKgIdq205lRERKRpmUNh53qo2NGyx5Vtg++eguFnB5cXtlVMDBz+C9i6DJb+t+3PJyLiIJeGqyrttxIREdmf7sOCl1uWtOxx3z4MNeXB5XzhMuxM6NofvrgPrA3f84qIRJhLw1Wl9luJiHiYMWaKMWaZMWalMebmJm6PN8a8Grp9hjGmjwNlOiszNDGwJfuuyrfDjCdg2BnQfXD4aomJDY5z35QXPP+WiEiUcudYnkAV+BWuRES8yBgTCzwMHA8UAjONMW9baxtvMLoS2GGtPcgYcwFwD3B+5Kt1UOcsiO8SHIO+fTXUVgen/9XWhL4OfV9Xs/vrsiKoLoUjfh3+ekaeD5/dDZ/fA3HJwQ6WrQv+of5ru/v6xtfF+IJDOmLjQpf+4DTExt/HxoXuFwdmj8+W99pGYNp4+x726sa1pDvXnC0Oezxfc7p/B3pP7S0iWze0PcTdWtPlNu0+ldSd4aqmQp0rERHvmgCstNauBjDGvAKcDjQOV6cDt4e+ngr8wxhjrPXQmjRjYNAUWPwWbF3ZKJzENfra9/3r0voEz2uVOSz89fji4LCfw3u/gn+eFP7nFxHJmQRXftiuL+HOcDX8bCjf5nQVIiLijCygoNH3hcDEfd3HWhswxpQA6cDWxncyxlwDXAOQm5vbXvU656wngn86ivFXQvchwS6ZiQkGQBMT6jQ1+tqY3bcB1NU26rjt0W2rv76u0dffy9AH6vq08Pb6q/ZqmrSw29Xka+3nBVrUiWrOe2rPrk8EPsPwzsckbdDeP+cIaGn5nbPapYzG3Bmuhp3hdAUiIuIC1tongCcAxo8fr1/X2ltMDPQ5zOkqRERazZ0DLURExMvWAzmNvs8OXdfkfYwxPqALoCUPIiLSJgpXIiLiNjOBAcaYvsaYOOAC4O097vM2cFno63OA/3lqv5WIiLQLdy4LFBERzwrtoboe+BCIBZ6x1i4yxtwBzLLWvg08DTxvjFkJbCcYwERERNpE4UpERFzHWvse8N4e193a6OtK4NxI1yUiIu6mZYEiIiIiIiJhoHAlIiIiIiISBgpXIiIiIiIiYaBwJSIiIiIiEgYKVyIiIiIiImGgcCUiIiIiIhIGClciIiIiIiJhoHAlIiIiIiISBgpXIiIiIiIiYaBwJSIiIiIiEgYKVyIiIiIiImGgcCUiIiIiIhIGClciIiIiIiJhoHAlIiIiIiISBgpXIiIiIiIiYaBwJSIiIiIiEgYKVyIiIiIiImFgrLVO1/A9xpgiYF0YnqobsDUMzxNN9J7dz2vvF/SevaKp99zbWpvhRDFNCdPxST9bb9B79gavvWevvV/Y93ve5/Gpw4WrcDHGzLLWjne6jkjSe3Y/r71f0Hv2Cq+8Z6+8z8b0nr1B79n9vPZ+oXXvWcsCRUREREREwkDhSkREREREJAzcHK6ecLoAB+g9u5/X3i/oPXuFV96zV95nY3rP3qD37H5ee7/Qivfs2j1XIiIiIiIikeTmzpWIiIiIiEjEKFyJiIiIiIiEgSvDlTFmijFmmTFmpTHmZqfraW/GmLXGmAXGmHnGmFlO19MejDHPGGO2GGMWNrquqzHmY2PMitBlmpM1hts+3vPtxpj1oZ/1PGPMyU7WGG7GmBxjzDRjzGJjzCJjzM9C17vyZ72f9+van7MxJsEY850xZn7oPf8hdH1fY8yM0L/brxpj4pyuNdy8dmwCHZ/c9m9WPa8dn7x2bAIdn9pyfHLdnitjTCywHDgeKARmAhdaaxc7Wlg7MsasBcZba117YjdjzBHALuA5a+3w0HV/AbZba+8O/aKSZq39jZN1htM+3vPtwC5r7X1O1tZejDE9gZ7W2jnGmBRgNnAGcDku/Fnv5/2eh0t/zsYYAyRba3cZY/zAdOBnwC+A/1hrXzHGPAbMt9Y+6mSt4eTFYxPo+OS2f7Pqee345LVjE+j41Jbjkxs7VxOAldba1dbaauAV4HSHa5I2stZ+AWzf4+rTgWdDXz9L8H9619jHe3Y1a+1Ga+2c0NelwBIgC5f+rPfzfl3LBu0KfesP/bHAMcDU0PWu+Rk3omOTS+n45H5eOzaBjk+04fjkxnCVBRQ0+r4Ql//HQPAH/5ExZrYx5hqni4mgTGvtxtDXm4BMJ4uJoOuNMXmhZRmuWYKwJ2NMH2AMMAMP/Kz3eL/g4p+zMSbWGDMP2AJ8DKwCiq21gdBd3PjvthePTaDjE7j036x9cO2/W/W8dmwCHZ9o4fHJjeHKiw6z1o4FTgKuC7XrPcUG17e6a41r0x4F+gOjgY3A/Y5W006MMZ2A14GfW2t3Nr7NjT/rJt6vq3/O1tpaa+1oIJtgR2ewsxVJO9LxyYX/Zu2Dq//dAu8dm0DHJ1pxfHJjuFoP5DT6Pjt0nWtZa9eHLrcAbxD8j8ELNofWBNevDd7icD3tzlq7OfQ/fh3wJC78WYfWOb8OvGit/U/oatf+rHo6aVDnhnmJHdu2jKdLLFxwhfp51ds3YL/tz13bAIdn8B9/2bti9v/3fLasQl0fKKVxyc3hquZwIDQZI844ALgbYdrajfGmOTQRkOMMcnACcDC/T/KNd4GLgt9fRnwloO1RET9P+IhZ+Kyn3VoM+nTwBJr7QONbnLlz3pf79fNP2djTIYxJjX0dSLBAQ9LCB7EzgndzTU/40Y8dWwCHZ9w4b9Z++Pyf7c8dWwCHZ/acnxy3bRAgNBYyAeBWOAZa+1dzlbUfowx/Qh+GgjgA15y4/s1xrwMHAV0AzYDtwFvAq8BucA64DxrrWs22O7jPR9FsBVvgbXAjxut9456xpjDgC+BBUBd6OrfElzn7bqf9X7e74W49OdsjBlJcENwLMEP+F6z1t4R+rHo6aVDnhnmJHdu2jKdLLFxwhfp51ds3YL+IQL/82q57Xjk9eOTaDjE204PrkyXImIiIiIiESaG5cFioiIiIiIRJzClYiIiIiISBgoXImIiIiIiISBwpWIiIiIiEgYKFyJiIiIiIiEgcKVSJQyxhxljHnH6TpERETq6dgkXqdwJSIiIiIiEgYKVyLtzBhziTHmO2PMPGPM48aYWGPMLmPMX40xi4wxnxpjMkL3HW2M+dYYk2eMecMYkxa6/iBjzCfGmPnGmDnGmP6hp+9kjJlqjFlqjHkxdEZ1ERGR/dKxSaR9KFyJtCNjzBDgfOBQa+1ooBa4GEgGZllrhwGfEzy7PcBzwG+stSMJnhW9/voXgYettaOAQ4D6s6GPAX4ODAX6AYe281sSEZEop2OTSPvxOV2AiMsdC4wDZoY+uEsEtgB1wKuh+7wA/McY0wVItdZ+Hrr+WeDfxpgUIMta+waAtbYSIPR831lrC0PfzwP6ANPb/V2JiEg007FJpJ0oXIm0LwM8a6295XtXGvP7Pe5nW/n8VY2+rkX/T4uIyIHp2CTSTrQsUKR9fQqcY4zpDmCM6WqM6U3w/71zQve5CJhurS0BdhhjDg9dfynwubW2FCg0xpwReo54Y0xSJN+EiIi4io5NIu1EnySItCNr7WJjzO+Aj4wxMUANcB1QBkwI3baF4Np3gMuAx0IHqNXAFaHrLwUeN8bcEXqOcyP4NkRExEV0bBJpP8ba1nZ8RaS1jDG7rLWdnK5DRESkno5NIm2nZYEiIiIiIiJhoM6ViIiIiIhIGKhzJSIiIiIiEgYKVyIiIiIiImGgcCUiIiIiIhIGClciIiIiIiJhoHAlIiIiIiISBv8fAW9g3xz6Z6cAAAAASUVORK5CYII=\n",
      "text/plain": [
       "<Figure size 864x576 with 2 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    },
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "accuracy\n",
      "\ttraining         \t (min:    0.887, max:    0.999, cur:    0.997)\n",
      "\tvalidation       \t (min:    0.767, max:    1.000, cur:    1.000)\n",
      "Loss\n",
      "\ttraining         \t (min:    0.008, max:    0.298, cur:    0.017)\n",
      "\tvalidation       \t (min:    0.000, max:    0.528, cur:    0.000)\n",
      "\n",
      "Epoch 00030: saving model to Eyes.h5\n"
     ]
    }
   ],
   "source": [
    "epochs = 30\n",
    "steps_per_epoch = train_generator.n//train_generator.batch_size\n",
    "validation_steps = validation_generator.n//validation_generator.batch_size\n",
    "\n",
    "reduce_lr = ReduceLROnPlateau(monitor='val_accuracy',verbose=2,factor=0.5,\n",
    "                              patience=2, min_lr=0.00001, mode='auto')\n",
    "checkpoint = ModelCheckpoint(\"Eyes.h5\", monitor='val_accuracy',\n",
    "                             save_weights_only=True, mode='max', verbose=2)\n",
    "callbacks = [EarlyStop ,PlotLossesKerasTF(), checkpoint, reduce_lr]\n",
    "\n",
    "history = network.fit(\n",
    "    x=train_generator,\n",
    "    steps_per_epoch=steps_per_epoch,\n",
    "    epochs=epochs,\n",
    "    validation_data = validation_generator,\n",
    "    validation_steps = validation_steps,\n",
    "    callbacks=callbacks\n",
    ")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T05:18:12.380141Z",
     "iopub.status.busy": "2022-11-17T05:18:12.379753Z",
     "iopub.status.idle": "2022-11-17T05:18:12.393121Z",
     "shell.execute_reply": "2022-11-17T05:18:12.390986Z",
     "shell.execute_reply.started": "2022-11-17T05:18:12.380084Z"
    }
   },
   "outputs": [],
   "source": [
    "model_json = network.to_json()\n",
    "with open(\"eyes.json\", \"w\") as json_file:\n",
    "    json_file.write(model_json)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T05:20:21.953020Z",
     "iopub.status.busy": "2022-11-17T05:20:21.952643Z",
     "iopub.status.idle": "2022-11-17T05:20:22.102521Z",
     "shell.execute_reply": "2022-11-17T05:20:22.101546Z",
     "shell.execute_reply.started": "2022-11-17T05:20:21.952986Z"
    }
   },
   "outputs": [],
   "source": [
    "from sklearn.metrics import classification_report as csr"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 14,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T05:23:52.188853Z",
     "iopub.status.busy": "2022-11-17T05:23:52.188509Z",
     "iopub.status.idle": "2022-11-17T05:23:53.236341Z",
     "shell.execute_reply": "2022-11-17T05:23:53.235181Z",
     "shell.execute_reply.started": "2022-11-17T05:23:52.188820Z"
    }
   },
   "outputs": [],
   "source": [
    "y_pd = network.predict(validation_generator)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 22,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T05:34:18.895603Z",
     "iopub.status.busy": "2022-11-17T05:34:18.895203Z",
     "iopub.status.idle": "2022-11-17T05:34:18.901970Z",
     "shell.execute_reply": "2022-11-17T05:34:18.900616Z",
     "shell.execute_reply.started": "2022-11-17T05:34:18.895564Z"
    }
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "len of valiadation set: 600\n"
     ]
    }
   ],
   "source": [
    "print(\"len of valiadation set:\",len(valSET))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 32,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T05:37:41.041424Z",
     "iopub.status.busy": "2022-11-17T05:37:41.041045Z",
     "iopub.status.idle": "2022-11-17T05:37:41.047039Z",
     "shell.execute_reply": "2022-11-17T05:37:41.046016Z",
     "shell.execute_reply.started": "2022-11-17T05:37:41.041391Z"
    }
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Closed_Eyes\n",
      "Open_Eyes\n"
     ]
    }
   ],
   "source": [
    "print(valSET[400][1])\n",
    "print(valSET[0][1])"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "execution": {
     "iopub.status.busy": "2022-11-13T19:32:30.952323Z",
     "iopub.status.idle": "2022-11-13T19:32:30.953018Z"
    }
   },
   "outputs": [],
   "source": [
    "network.save('eyes.h5')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 56,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T05:58:20.458229Z",
     "iopub.status.busy": "2022-11-17T05:58:20.457861Z",
     "iopub.status.idle": "2022-11-17T05:58:20.464039Z",
     "shell.execute_reply": "2022-11-17T05:58:20.462969Z",
     "shell.execute_reply.started": "2022-11-17T05:58:20.458192Z"
    }
   },
   "outputs": [
    {
     "name": "stderr",
     "output_type": "stream",
     "text": [
      "/opt/conda/lib/python3.7/site-packages/ipykernel_launcher.py:1: VisibleDeprecationWarning: Creating an ndarray from ragged nested sequences (which is a list-or-tuple of lists-or-tuples-or ndarrays with different lengths or shapes) is deprecated. If you meant to do this, you must specify 'dtype=object' when creating the ndarray\n",
      "  \"\"\"Entry point for launching an IPython kernel.\n"
     ]
    }
   ],
   "source": [
    "val = np.array(valSET)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 57,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T05:58:20.859006Z",
     "iopub.status.busy": "2022-11-17T05:58:20.858635Z",
     "iopub.status.idle": "2022-11-17T05:58:20.865375Z",
     "shell.execute_reply": "2022-11-17T05:58:20.864383Z",
     "shell.execute_reply.started": "2022-11-17T05:58:20.858970Z"
    }
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "(600, 2)"
      ]
     },
     "execution_count": 57,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "val.shape"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 68,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T06:02:02.934264Z",
     "iopub.status.busy": "2022-11-17T06:02:02.933857Z",
     "iopub.status.idle": "2022-11-17T06:02:02.949534Z",
     "shell.execute_reply": "2022-11-17T06:02:02.948591Z",
     "shell.execute_reply.started": "2022-11-17T06:02:02.934226Z"
    }
   },
   "outputs": [],
   "source": [
    "x_val=[]\n",
    "y_val=[]\n",
    "for x,y in val:\n",
    "    if \"open\" in y.lower():\n",
    "        y_val.append(1)\n",
    "    else:\n",
    "        y_val.append(0)\n",
    "    x = np.expand_dims(x,axis=2)\n",
    "    x_val.append(x)\n",
    "#     print(x.shape)\n",
    "#     break\n",
    "    \n",
    "    "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 69,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T06:02:04.331931Z",
     "iopub.status.busy": "2022-11-17T06:02:04.331581Z",
     "iopub.status.idle": "2022-11-17T06:02:04.340358Z",
     "shell.execute_reply": "2022-11-17T06:02:04.339520Z",
     "shell.execute_reply.started": "2022-11-17T06:02:04.331896Z"
    }
   },
   "outputs": [],
   "source": [
    "x_val=np.array(x_val)\n",
    "y_val=np.array(y_val)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 70,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T06:02:05.285172Z",
     "iopub.status.busy": "2022-11-17T06:02:05.284798Z",
     "iopub.status.idle": "2022-11-17T06:02:05.293905Z",
     "shell.execute_reply": "2022-11-17T06:02:05.292787Z",
     "shell.execute_reply.started": "2022-11-17T06:02:05.285134Z"
    }
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "(600, 86, 86, 1)"
      ]
     },
     "execution_count": 70,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "x_val.shape"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 71,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T06:02:06.526562Z",
     "iopub.status.busy": "2022-11-17T06:02:06.526213Z",
     "iopub.status.idle": "2022-11-17T06:02:06.532364Z",
     "shell.execute_reply": "2022-11-17T06:02:06.531339Z",
     "shell.execute_reply.started": "2022-11-17T06:02:06.526529Z"
    }
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "(600,)"
      ]
     },
     "execution_count": 71,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "y_val.shape"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 72,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T06:02:07.848145Z",
     "iopub.status.busy": "2022-11-17T06:02:07.847737Z",
     "iopub.status.idle": "2022-11-17T06:02:07.860675Z",
     "shell.execute_reply": "2022-11-17T06:02:07.859682Z",
     "shell.execute_reply.started": "2022-11-17T06:02:07.848074Z"
    }
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "1    360\n",
       "0    240\n",
       "dtype: int64"
      ]
     },
     "execution_count": 72,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "import pandas as pd\n",
    "pd.Series(y_val).value_counts()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 73,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T06:02:08.624695Z",
     "iopub.status.busy": "2022-11-17T06:02:08.624278Z",
     "iopub.status.idle": "2022-11-17T06:02:09.227054Z",
     "shell.execute_reply": "2022-11-17T06:02:09.226073Z",
     "shell.execute_reply.started": "2022-11-17T06:02:08.624640Z"
    }
   },
   "outputs": [],
   "source": [
    "y_pd=network.predict(x_val)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 76,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T06:04:06.180482Z",
     "iopub.status.busy": "2022-11-17T06:04:06.180127Z",
     "iopub.status.idle": "2022-11-17T06:04:06.184343Z",
     "shell.execute_reply": "2022-11-17T06:04:06.183235Z",
     "shell.execute_reply.started": "2022-11-17T06:04:06.180450Z"
    }
   },
   "outputs": [],
   "source": [
    "y_pd=np.argmax(y_pd,axis=1)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 77,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T06:04:13.296940Z",
     "iopub.status.busy": "2022-11-17T06:04:13.296621Z",
     "iopub.status.idle": "2022-11-17T06:04:13.303930Z",
     "shell.execute_reply": "2022-11-17T06:04:13.303018Z",
     "shell.execute_reply.started": "2022-11-17T06:04:13.296910Z"
    }
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "array([1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,\n",
       "       1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,\n",
       "       1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,\n",
       "       1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,\n",
       "       1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,\n",
       "       1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,\n",
       "       1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,\n",
       "       1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,\n",
       "       1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,\n",
       "       1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,\n",
       "       1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,\n",
       "       1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,\n",
       "       1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,\n",
       "       1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,\n",
       "       1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,\n",
       "       1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,\n",
       "       1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,\n",
       "       0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,\n",
       "       0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,\n",
       "       0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,\n",
       "       0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,\n",
       "       0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,\n",
       "       0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,\n",
       "       0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,\n",
       "       0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,\n",
       "       0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,\n",
       "       0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,\n",
       "       0, 0, 0, 0, 0, 0])"
      ]
     },
     "execution_count": 77,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "y_val"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 79,
   "metadata": {
    "execution": {
     "iopub.execute_input": "2022-11-17T06:04:44.051541Z",
     "iopub.status.busy": "2022-11-17T06:04:44.051179Z",
     "iopub.status.idle": "2022-11-17T06:04:44.063882Z",
     "shell.execute_reply": "2022-11-17T06:04:44.062637Z",
     "shell.execute_reply.started": "2022-11-17T06:04:44.051506Z"
    }
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "              precision    recall  f1-score   support\n",
      "\n",
      "           0       0.96      1.00      0.98       240\n",
      "           1       1.00      0.97      0.98       360\n",
      "\n",
      "    accuracy                           0.98       600\n",
      "   macro avg       0.98      0.98      0.98       600\n",
      "weighted avg       0.98      0.98      0.98       600\n",
      "\n"
     ]
    }
   ],
   "source": [
    "print(csr(y_val,y_pd))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
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
   "version": "3.9.11"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 4
}
