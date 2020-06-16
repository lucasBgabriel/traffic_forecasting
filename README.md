# network traffic forecasting

---
## Dataset

---
## DCRNN

This work is based on the [DCRNN](https://github.com/liyaguang/DCRNN) repository, changing a few things from
their original algorithm to better fit our problem. All credits 

### Running

More information inside the `DCRNN/`

Generate train data to `users`:

`python -m scripts.generate_training_data --output_dir=../data/users --traffic_df_filename=../data/users.h5`

Generate adjacency matrix:

```bash
python -m scripts.gen_adj_mx  --sensor_ids_filename=../data/sensor_graph/sensor_ids.txt \
	--normalized_k=0.1  \
	--distances_filename=../data/sensor_graph/sensor_distance.csv  \
	--output_pkl_filename=../data/sensor_graph/adj_mx.pkl
```

Train data: 

`python dcrnn_train.py --config_filename=../data/model/dcrnn_users.yaml --use_cpu_only=True`


Evaluate training:

`python -m scripts.eval_baseline_methods --traffic_reading_filename=../data/users.h5`

---

## LSTM