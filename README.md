# PII_Data_Detection
https://www.kaggle.com/competitions/pii-detection-removal-from-educational-data

The Learning Agency Lab - PII Data Detection
List of Experiments
1. Deberta_base-v3 with raw model parameters
2. Deberta_base-v3 with raw model parameters
3. Deberta_base-v3 with cosine lr and freezing layers
4. Deberta_base-v3 with cosine lr and freezing layers with 4 ext data
5. Deberta_large-v3 with cosine lr and freezing layers
6. Exp 3 with added token overflow parameter in tokenizer and chunk size 768 in inf
7. Deberta_base-v3 with cosine lr and freezing layers with token overflow, data balancing (removed negative data (i.e.) data with all labels as 'O' fraction used from data = 0.2).
8. Exp 3 with added token overflow parameter in tokenizer and chunk size 512 in inf.
9. Reduced the number of 'O' predictions by increasing the confidence threshold of a token being 'O' to 0.9. So the data with threshold over 0.9 would be considered as 'O' whereas the data with threshold less the 0.9 would be assigned the next highest threshold label.
10. Deb_base-v3 with relu
11. Deb_base-v3 with dropout = 0.2
12. Deb_base-v3 with dropout = 0.3
13. Deb_base-v3 with lr = 1e-5
14. Deb_base-v3 with linear lr
15. Deb_base-v3 with polynomiallr
16. Deb_base-v3 with max_grad_norm and weight decay
17. Deb_base-v3 with custom loss function with class weights in cross entropy loss cw=1.05
18. Deb_base-v3 with embeddings and layers freezed
19. Deb_base-v3 with one ext data added.
20. 'OpenAssistant/reward-model-deberta-v3-large-v2' with 2 datasets and do-0.2
21. 'deepset/deberta-v3-large-squad2' with 2 datasets and do-0.2
22. Strided submissions with deberta base and openassistant reward model.

| Exp |    Train   |   Valid   | Recall | Precision |     F1   |         Model          | Trainer | Train_Seq_len | Inf_seq_len | Public |
| --- |    ---   |   ---   | --- | --- |     ---   |         ---          | --- | --- | --- | --- |
|   1   |  0.0132  | 0.0012  |     -     |        -       |     -     |  Deberta_base_v3 |   HFT   |        1024        |     1024      |  0.794 |
|   2   |  0.0132  | 0.0012  |     -     |        -       |     -     |  Deberta_base_v3 |   HFT   |        2048        |     2048      |  0.828 |
|   3   |  0.0006  | 0.0011  |  0.891 |    0.696    | 0.882 |  Deberta_base_v3 |    HFT   |        1024       |     2048      |  0.870  |
|   4   |  0.0170  | 0.0188  |  0.942 |    0.769    | 0.933 |  Deberta_base_v3  |   HFT   |         768        |     2048      |  0.870  |
|   5   |  0.0178  | 0.0185  |  0.945 |    0.784    | 0.937 |  Deberta_large_v3 |   HFT   |         768        |     2048      |  0.887  |
|   6   |                            Exp 3 with added token overflow parameter in tokenizer                      |    1024       |  0.895  | 
|   7   |  0.0041  | 0.0049  |  0.989 |    0.986    | 0.989 |  Deberta_base_v3 |    HFT   |        768         |      768       |  0.906  |
|   8   |                            Exp 7 with added token overflow parameter in tokenizer                      |      512       |  0.912  | 
|   9   |                                        Exp 8 with 'O' prediction threshold as 0.9                                   |      512       |  0.919  | 
|  10  |  0.0010  | 0.0010  |  0.996 |    0.990    | 0.995 | Deb_base_v3+relu |   HFT   |         768        |      512       |  0.894  |
|  11  |  0.0012  | 0.0010  |  0.990 |    0.991    | 0.990 | Deb_base_v3+do0.2 | HFT  |         1024      |      512       |  0.925  |
|  12  |  0.0009  | 0.0017  |  0.991 |    0.979    | 0.990 | Deb_base_v3+do0.3 | HFT  |         1024      |      512       |  0.911  |
|  13  |  0.0009  | 0.0010  |  0.991 |    0.991    | 0.991 | Deb_base_v3+lr1e-5 | HFT  |         1024      |      512       |  0.911  |
|  14  |  0.0009  | 0.0009  |  0.992 |    0.990    | 0.992 |  Deb_base_v3+lin_lr  | HFT  |         1024      |      512       |  0.889  |
|  15  |  0.0009  | 0.0009  |  0.993 |    0.990    | 0.993 |  Deb_base_v3+pol_lr | HFT  |         1024      |      512       |  0.921  |
|  16  |  0.0009  | 0.0009  |  0.992 |    0.990    | 0.992 | Deb_base_v3+gn+wd | HFT |         1024      |      512      |  0.896  |
|  17  |  0.0432  | 0.0290  |  0.990 |    0.993    | 0.990 | Deb_base_v3+cw-loss | HFT |         1024      |      512      |  0.878  |
|  18  |  0.0034  | 0.0035  |  0.988 |    0.993    | 0.989 | Deb_base_v3+frzemb  | HFT |         1024      |      512      |  0.880  |
|  19  |  0.0023  | 0.0030  |  0.992 |    0.989    | 0.991 | Deb_base_v3+frzemb  | HFT |         1024      |      512      |  0.908  |
|  20  |  0.0004  | 0.0005  |  0.994 |    0.996    | 0.995 |    OpenAss+frzemb    | HFT  |         1024      |      512      |  0.927  |
|  21  |  0.0004  | 0.0005  |  0.994 |    0.996    | 0.995 |    Deepset+frzemb      | HFT  |         1024      |      512      |  0.924  |
|  22  | 0.926 debbase submission with stride updation in the predicted tokens.   |         1024      |     1024     |  0.955  |
