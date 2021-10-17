Kachery consists of two elements:
  1. Kachery-daemon, a server/node which communicates with other nodes across the p2p network. 
    - It works by being authorized to join certain "channels", which are basically data sources.
      - An example of a channel could be the SpikeForest channel. (This channel is joined in Installation part 5)
    - Optional, but could be ran as a system service on startup of your PC, platform specific.

  2. Kachery-client, which exposes an interface to python.
    - This is used to communicate with your local kachery node (kachery-daemon).
    - If you ask your node for a particular 

Kachery documentation can be found here: https://github.com/kacheryhub/kachery-doc

Installation:
1. Install miniconda from [here](https://docs.conda.io/en/latest/miniconda.html) and follow the 
[instructions](https://conda.io/projects/conda/en/latest/user-guide/install/index.html#regular-installation)

2. Create new virtual environment, with virtualenv/pyenv/conda. Conda commands:
```
conda create --name kachery python=3.8
conda activate kachery
```

3. Install numpy and kachery-client inside python environment.

```
conda install -c conda-forge nodejs
pip install numpy
pip install --upgrade kachery-client
```

4. Either:
  - Install kachery-daemon globally on your system
  - Install kachery-daemon in the environment created above

```
pip install --upgrade kachery-daemon
```

5. Start your kachery daemon instance:
  
  - As per the kachery documentation [here](https://github.com/kacheryhub/kachery-doc/blob/main/doc/hostKacheryNode.md#running-the-daemon)
  - You must run this from the same environment that you installed kachery-daemon in.:

```
kachery-daemon-start --label <WHATEVER YOU CHOOSE> --owner <YOUR GOOGLE ACCOUNT ID (GMAIL)>
```
  
6. Registration of kachery node:
  - Using the same google account email you used to start the kachery node, log into https://www.kacheryhub.org/
  - Click "Register a new node"
  - With the kachery instance running, open new terminal and run "kachery-daemon info" to retrieve your node ID.
  - Complete node registration with this node ID.

7. Join spikeforest channel:
  - Click on your node in Kacheryhub, and click "Join a channel for this node"
  - Join a channel with channel name "spikeforest"
  - After joining, add the passcode "sf-rMIASUHn" to the node configuration.
  - Restart your local kachery node for changes to take effect.

8. Trying out your installation:
  - Enter the environment where your kachery-client is installed, ensuring kachery-daemon is running with the above configuration completed.
  - Run the test file in this repo: DataRetrieval.py
  - If you get a load json printed out in the console the setup has succeeded.

Troubleshooting

1. If you have used kachery in the past, ensure the most recent version is installed, of both the daemon and the client.
2. On upgrading, my node started running with a differnt node ID, making me unable to retrieve data.
  - If this is the case for you, remove the old kachery-node from kacheryhub and add the new one, with the required spikeforest config.
