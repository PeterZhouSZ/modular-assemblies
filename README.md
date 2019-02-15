## Learning to Control Self-Assembling Morphologies ##
#### [[Project Website]](https://pathak22.github.io/modular-assemblies/) [[Demo Video]](https://www.youtube.com/watch?v=heR2yD8HOvY)

[Deepak Pathak](https://people.eecs.berkeley.edu/~pathak/), [Chris Lu](https://chris-lu.weebly.com/), [Trevor Darrell](https://people.eecs.berkeley.edu/~trevor/), [Phillip Isola](https://www.eecs.mit.edu/people/faculty/phillip-isola/), [Alexei A. Efros](https://people.eecs.berkeley.edu/~efros/)<br/>
University of California, Berkeley<br/>
MIT

<a href="envs/teaser.jpg">
<img src="envs/teaser.jpg" width="500">
</img></a>

This is a tensorflow based implementation for our [ICML 2017 paper on curiosity-driven exploration for reinforcement learning](http://pathak22.github.io/noreward-rl/). Idea is to train agent with intrinsic curiosity-based motivation (ICM) when external rewards from environment are sparse. Surprisingly, you can use ICM even when there are no rewards available from the environment, in which case, agent learns to explore only out of curiosity: 'RL without rewards'. If you find this work useful in your research, please cite:

    @inproceedings{pathak19assemblies,
        Author = {Pathak, Deepak and Lu, Chris and Darrell, Trevor and
                  Isola, Phillip and Efros, Alexei A.},
        Title = {Learning to Control Self-Assembling Morphologies:
                  A Study of Generalization via Modularity},
        Booktitle = {arXiv preprint arXiv:1902.05546},
        Year = {2019}
    }

### Installation and Usage

1. Setting up repository
  ```Shell
  git clone https://github.com/pathak22/modular-assemblies.git
  cd modular-assemblies/
  git clone https://github.com/Unity-Technologies/ml-agents.git
  cd ml-agents/
  git reset --hard 6c5255e
  cd ..
  bash envs/setup_env.sh

  python3 -m venv assemblyEnv
  source $PWD/assemblyEnv/bin/activate
  pip install --upgrade pip
  ```

2. Installation
    - Requirements:
      - CUDNN-5.1, CUDA-8.0, Python-3.5
    - Detailed setup, skip to quick setup for exact replication:
    ```Shell
    # Install Pytorch from http://pytorch.org/
    pip install http://download.pytorch.org/whl/cu80/torch-0.3.0.post4-cp35-cp35m-linux_x86_64.whl
    pip install torchvision
    pip install --upgrade visdom

    # Install baselines for Atari preprocessing
    pip install gym==0.9.4 # baselines install latest gym first automatically, but latest gym has moved to mujoco5 so first install old gym and then install baselines
    git clone https://github.com/openai/baselines.git
    cd baselines
    git reset --hard b5be53d
    pip install -e .

    # Additional packages
    pip install numpy
    pip install matplotlib
    pip install pillow
    pip install opencv-python

    # fold
    cd modular-assemblies/src/
    git clone https://github.com/nearai/pytorch-tools.git
    cd pytorch-tools/
    git reset --hard 09dccb2
    python setup.py install
    ```
    - Quick setup for exact replication:
    ```Shell
    pip install -r requirements.txt
    ```

3. Run code
  ```Shell
  cd modular-assemblies/src/
  python test_env.py
  ```

### Acknowledgement
Builds upon Ilya Kostrikov's Pytorch PPO [implementation](https://github.com/ikostrikov/pytorch-a2c-ppo-acktr).