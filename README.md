# Overview

Entities and relations extraction is one of the key task to build medical knowledge graph, which is of great significance to the development of medical artificial intelligence. However, overlapping triples are great challenge for biomedical entities and relations extraction. In order to improve the performance of biomedical entities and relations extraction, we propose a joint extraction of entities and relations method based on decomposition and recombination strategy to mine biomedical text. Our method decomposes entities and relations extraction task into three related sub-modules, which are entity tagging module, relation classification module and recombination matching module. Our main contributions are as follows: first, we introduce a decomposition and recombination end-to-end learning framework for joint entities and relations extraction. Second, we propose a bi-directional prediction method to deal with the overlapping triples problem. Finally, we propose the negative samples generation method to alleviate the error accumulation among these modules. The extensive experiments demonstrate that our method can improve the F1 score by 1.49%, 1.81% and 11.72% in ADE, DDI and BB biomedical corpus.![fig2](E:\投稿\BIBM\paper\BIBM2022_HongCheng\fig2.png)



# **Requirements**

Our experimental environment is as follows:

tensorflow==1.15.0 

Keras==2.3.1 

python=3.7 

cuda=10.1

# **Train**

Our training commands are as follows:

1、ADE

```
python run.py \
--do_train \
--model_name ADE \
--rel_path data/ADE/rel2id.json \
--train_path data/ADE/train_triples.json \
--dev_path data/ADE/test_triples.json \
--bert_dir BioBert/biobert_v1.1_pubmed \
--save_path ckpts/ADE.model \
--learning_rate 0.000005 \
--neg_samples 20 \
--epoch 200 \
```

2、DDI

```
python run.py \
--do_train \
--model_name DDI \
--rel_path data/DDI/rel2id.json \
--train_path data/DDI/train_triples.json \
--dev_path data/DDI/test_triples.json \
--bert_dir BioBert/biobert_v1.1_pubmed \
--save_path ckpts/DDI.model \
--learning_rate 0.000005 \
--neg_samples 20 \
--epoch 200 \
```

3、BB

```
python run.py \
--do_train \
--model_name BB \
--rel_path data/BB/rel2id.json \
--train_path data/BB/train_triples.json \
--dev_path data/BB/test_triples.json \
--bert_dir BioBert/biobert_v1.1_pubmed \
--save_path ckpts/BB.model \
--learning_rate 0.000002 \
--neg_samples 10 \
--epoch 200 \
```

