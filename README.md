# Social GAN

Human motion is interpersonal, multimodal and follows social conventions. In this paper, we tackle this problem by combining tools from sequence prediction and generative adversarial networks: a recurrent sequence-to-sequence model observes motion histories and predicts future behavior, using a novel pooling mechanism to aggregate information across
people.

Below we show an examples of socially acceptable predictions made by our model in complex scenarios. Each person is denoted by a different color. We denote observed trajectory by dots and predicted trajectory by stars.
<div align='center'>
<img src="images/2.gif"></img>
<img src="images/3.gif"></img>
</div>


## Model
Our model consists of three key components: Generator (G), Pooling Module (PM) and Discriminator (D). G is based on encoder-decoder framework where we link the hidden states of encoder and decoder via PM. G takes as input trajectories of all people involved in a scene and outputs corresponding predicted trajectories. D inputs the entire sequence comprising both input trajectory and future prediction and classifies them as “real/fake”.

<div align='center'>
  <img src='images/model.png' width='1000px'>
</div>


## Pretrained Models
You can download pretrained models by running the script `bash scripts/download_models.sh`. This will download the following models:

- `sgan-models/<dataset_name>_<pred_len>.pt`: Contains 10 pretrained models for all five datasets. These models correspond to SGAN-20V-20 in Table 1.
- `sgan-p-models/<dataset_name>_<pred_len>.pt`: Contains 10 pretrained models for all five datasets. These models correspond to SGAN-20VP-20 in Table 1.


## Running Models
You can use the script `scripts/evaluate_model.py` to easily run any of the pretrained models on any of the datsets. For example you can replicate the Table 1 results for all datasets for SGAN-20V-20 like this:

```bash
python scripts/evaluate_model.py \
  --model_path models/sgan-models
```
