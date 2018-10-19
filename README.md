# Spherical convolutional neural network

The code in this repository implements an efficient generalization of the
popular Convolutional Neural Networks (CNNs) to a sphere.

The implementation is based on [convolutional neural networks on
graphs][gcnn_paper], as implemented [here][gcnn_code].

[gcnn_paper]: https://arxiv.org/abs/1606.09375
[gcnn_code]: https://github.com/mdeff/cnn_graph/

## Installation

1. Clone this repository.
   ```sh
   git clone https://github.com/SwissDataScienceCenter/deepsphere.git
   cd deepsphere
   ```

2. Install the dependencies.
   ```sh
   pip install -r requirements.txt
   ```

   **Note**: if you won't be working with a GPU, comment the
   `tensorflow-gpu==1.6.0` line in `requirements.txt` and uncomment the
   `tensorflow==1.6.0` line.

   **Note**: The code has been developed and tested with Python 3.5 and 3.6. It
   should work on Python 2.7 with `requirements_py27.txt`. Please send a PR if
   you encounter an issue.

3. Play with the Jupyter notebooks.
   ```sh
   jupyter notebook
   ```

## Using the model

To use HealPixNet on your data, you need:

1. a data matrix where each row is a sample and each column is a feature,
2. a target vector,

See the [usage notebook][usage] for a simple example with fabricated data.
Please get in touch if you are unsure about applying the model to a different
setting.

[usage]: https://github.com/SwissDataScienceCenter/healpixnet/blob/master/demo.ipynb

## Experiments

Below are some notebooks which contain various experiments:
1. Classification of data on the whole sphere
1. Classification of data from part of the sphere (with noise)

The results we reported in the paper are recorded here:
1. TODO: link to notebook
1. TODO: link to notebook

## Reproducing the results of the paper
The steps to reproduce the paper results are simple, while they might take a while.
1. Download the [dataset][dataset_doi]
```
python download.py
```
2. Preprocess the dataset
```
python preprocess.py
```
3. Run the experiemnts
```
python results_deepsphere_with_augmentation.py
python results_histogram_with_augmentation.py
python results_psd_with_augmentation.py FCN
python results_psd_with_augmentation.py CNN
```
The results will be saved in the folder `results`. Please not that the result of the spherical CNN may varies from one run to the oter. So you may want to check the tensorboard summaries and verify that convergence is attained. For some experiments, the network needs a large amount of epoch to stabilize.

The scripts `results_deepsphere_with_augmentation.py` and `python results_psd_with_augmentation.py` can be executed in parallel in a HPC setting. You can adapt the script `euler_launcher.py` and `cscs_launcher.py` for your particular setting. Please contact the authors if you are stuck in trying to do so.

[dataset_doi]:https://doi.org/10.5281/zenodo.1303272

## License & co

The content of this repository is released under the terms of the [MIT license](LICENSE.txt).
Please cite our [paper][arXiv] if you use it.

```
@article{,
  title={TBD},
  author={Perraudin, Nathanaël},
  journal={Astronomy and Computing},
  year={2018}
}
```
TODO: link to arxiv

[arXiv]:https://...