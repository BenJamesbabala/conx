# conx

## Deep Learning for Simple Folk

Built in Python on Keras.

[![CircleCI](https://circleci.com/gh/Calysto/conx/tree/master.svg?style=svg)](https://circleci.com/gh/Calysto/conx/tree/master) [![codecov](https://codecov.io/gh/Calysto/conx/branch/master/graph/badge.svg)](https://codecov.io/gh/Calysto/conx) [![Documentation Status](https://readthedocs.org/projects/conx/badge/?version=latest)](http://conx.readthedocs.io/en/latest/?badge=latest) [![PyPI version](https://badge.fury.io/py/conx.svg)](https://badge.fury.io/py/conx)

Read the documentation at [conx.readthedocs.io](http://conx.readthedocs.io/)
Ask questions on the mailing list: [conx-users](https://groups.google.com/forum/#!forum/conx-users)

Implements Deep Learning neural network algorithms using a simple interface with easy visualizations and useful analytical. Built on top of Keras, which can use either [TensorFlow](https://www.tensorflow.org/), [Theano](http://www.deeplearning.net/software/theano/), or [CNTK](https://www.cntk.ai/pythondocs/).

The network is specified to the constructor by providing sizes. For example, Network("XOR", 2, 5, 1) specifies a network named "XOR" with a 2-node input layer, 5-unit hidden layer, and a 1-unit output layer.

## Example

Computing XOR via a target function:

```python
from conx import Network, SGD

dataset = [[[0, 0], [0]],
          [[0, 1], [1]],
          [[1, 0], [1]],
          [[1, 1], [0]]]

net = Network("XOR", 2, 5, 1, activation="sigmoid")
net.set_dataset(dataset)
net.compile(loss='mean_squared_error',
            optimizer=SGD(lr=0.3, momentum=0.9))
net.train(2000, report_rate=10, accuracy=1)
net.test()
```

## Install

```shell
pip install conx -U
```

You will need to decide whether to use Theano, TensorFlow, or CNTK. Pick one. See [docs.microsoft.com](https://docs.microsoft.com/en-us/cognitive-toolkit/Setup-CNTK-on-your-machine) for installing CNTK on Windows or Linux. All platforms can also install either of the others using pip:

```shell
pip install theano
```

or

```shell
pip install tensorflow
```

Note: you may need to use pip3, or admin privileges (eg, sudo), or a user environment.

To use a Keras backend other than TensorFlow, edit (or create) `~/.keras/kerson.json`, like:

```json
{
    "backend": "theano",
    "image_data_format": "channels_last",
    "epsilon": 1e-07,
    "floatx": "float32"
}
```

## Examples

See the [notebooks folder](https://github.com/Calysto/conx/tree/master/notebooks) and the [documentation](http://conx.readthedocs.io/en/latest/) for additional examples.
