# Improving Style Randomization via Domain-specific Feature Reweighting for Domain Generalization (EUSIPCO 2022)
# Reweighted Feature Statistics Randomization (RFR) for DomainBed
Note that this project is built upon [DomainBed](https://github.com/facebookresearch/DomainBed).

## Quick start

### Setting
1. Clone the [DomainBed repository](https://github.com/facebookresearch/DomainBed).

2. Add class RFR(algorithms.py) to DomainBed's 'domainbed/algorithms.py' (or Replace DomainBed's 'domainbed/algorithms.py' with ours)

3. Replace DomainBed's domainbed/scripts/train.py and domainbed/hparams_registry.py with these files.


### Download the datasets:
```sh
python -m domainbed.scripts.download \
       --data_dir=./domainbed/data
```
You need to edit the 'domainbed/scripts/download.py' file to download the dataset you want. The last few lines of the file(download.py) contain commands to download the dataset.

### Train a model with multi gpu:

```sh
python -m domainbed.scripts.sweep launch\
       --data_dir=./domainbed/data\
       --output_dir=./results_pacs_rfr\
       --command_launcher multi_gpu\
       --algorithms RFR\       
       --datasets PACS\ 
       --n_trials 1\ 
       --single_test_envs
```

### Train a model with single gpu:
```sh
python -m domainbed.scripts.sweep launch\
       --data_dir=./domainbed/data\
       --output_dir=./results_pacs_rfr\
       --command_launcher local\
       --algorithms RFR\       
       --datasets PACS\ 
       --n_trials 1\ 
       --single_test_envs
```

### Delete incomplete jobs:

```sh
python -m domainbed.scripts.sweep delete_incomplete\
       --data_dir=./domainbed/data\
       --output_dir=./results_pacs_rfr\
       --command_launcher multi_gpu\
       --algorithms RFR\
       --datasets PACS\
       --n_trials 1\
       --single_test_envs
```

To view the results of your sweep:

````sh
python -m domainbed.scripts.collect_results\
       --input_dir=./results_pacs_rfr/
````
