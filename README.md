# head_motion_prediction_setup

Simple setup to use [Rondon 360-videos models/dataset collection](https://gitlab.com/miguelfromeror/head-motion-prediction).

The project dependencies are described [environment.yml](environment.yml) and [requirements.txt](requirements.txt), which the main one is [TensorFlow](https://www.tensorflow.org/install/pip).

```bash
conda env create -f environment.yml
conda activate hmp
```

To fetch and patch the Rondon head_motion_prediction submodule, do

```bash
git submodule init
git submodule update
sed -i -e 's/import keras/import tensorflow.keras/g' -e 's/from keras/from tensorflow.keras/g'  ./head_motion_prediction/*.py
```

## Usage

to train:

```bash
cd head_motion_prediction
python training_procedure.py -train -dataset_name David_MMSys_18 -model_name pos_only
```

You can skip the training step, if you fetch the weights.hdf5 from this [link](https://unice-my.sharepoint.com/personal/lucile_sassatelli_unice_fr/_layouts/15/onedrive.aspx?ga=1&id=%2Fpersonal%2Flucile%5Fsassatelli%5Funice%5Ffr%2FDocuments%2FMiguel%2Fhead%2Dmotion%2Dprediction%2FDavid%5FMMSys%5F18%2Fpos%5Fonly%2FModels%5FEncDec%5Feulerian%5FPaper%5FExp%5Finit%5F30%5Fin%5F5%5Fout%5F25%5Fend%5F25) and put it to the folder `David_MMSys_18/pos_only/Models_EncDec_eulerian_Paper_Exp_init_30_in_5_out_25_end_25/`

to evaluate:

```bash
cd head_motion_prediction
python training_procedure.py -evaluate -dataset_name David_MMSys_18 -model_name pos_only
```