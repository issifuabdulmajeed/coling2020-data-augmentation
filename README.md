## Prepare the i2b2-2010 dataset
The training set contains only 50 sentences
~~~
cp /data/dai031/Experiments/2020-06-03-01/50/* data/
~~~

## Experiments
### No augmentation
~~~
python main.py --data_folder data --embedding_type bert --pretrained_dir /data/dai031/Corpora/SciBERT/scibert_scivocab_cased --result_filepath baseline.json
~~~
### Label-wise token replacement
~~~
python main.py --data_folder data --embedding_type bert --pretrained_dir /data/dai031/Corpora/SciBERT/scibert_scivocab_cased --augmentation LwTR --result_filepath lwtr.json
~~~
### Synonym replacement
~~~
python main.py --data_folder data --embedding_type bert --pretrained_dir /data/dai031/Corpora/SciBERT/scibert_scivocab_cased --augmentation SR --result_filepath sr.json
~~~
### Mention replacement
~~~
python main.py --data_folder data --embedding_type bert --pretrained_dir /data/dai031/Corpora/SciBERT/scibert_scivocab_cased --augmentation MR --result_filepath mr.json
~~~
### Shuffle within segments
~~~
python main.py --data_folder data --embedding_type bert --pretrained_dir /data/dai031/Corpora/SciBERT/scibert_scivocab_cased --augmentation SiS --result_filepath sis.json
~~~
### All
~~~
python main.py --data_folder data --embedding_type bert --pretrained_dir /data/dai031/Corpora/SciBERT/scibert_scivocab_cased --augmentation MR LwTR SiS SR --result_filepath all.json
~~~

## Results
| Method | F1 score |
| --- | --- |
| No augmentation | 37.9 |
| Label-wise token replacement | 40.8 |
| Synonym replacement | 40.8 |
| Mention replacement | 41.2 |
| Shuffle within segments | 38.1 |
| All | 42.5 |