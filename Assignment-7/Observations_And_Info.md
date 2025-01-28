## File Structrue Info:

1) Metric_Learning.ipynb has experiments run upto 50 epochs
2) Metric_Learning_100_X.ipynb have ecperiments run upto 100 epochs (we ran experiments on two machines due to large training times)


## Observations

| Margin_Epoch     |    ARI     |
| ------------- | ------------- |
| 0.1_50 | 0.4590 |
| 0.2_50 | 0.4363 |
| 0.5_50 | 0.4117 |
| 1.0_50 | 0.4117 |
| 0.1_100 | 0.4829 |
| 0.2_100 | 0.4711 |
| 0.5_100 | 0.4855 |
| 1.0_100 | 0.4403 |

1) As we increase the margin from 0.1, 0.2, 0.5, 1.0, the validation loss increases, but the training loss converges (given enough epochs).
2) Running the model for 50 or 100 epochs didn't make any difference in the final validation loss as it strats to jump around a mean value.
3) The ARI score for all 4 margin values increases when training for 100 epochs vs 50 epochs by an average of 4%.
4) ARI score decreases when increasing the margin from 0.1 to 1.0 when training for 50 epochs. However, no such pattern is observed when running the model for 100 epochs and a margin of 0.5 gives the best ARI score.
5) This can be atrributed to model overfitting and the embeddings fluctuating around a mean value at every epoch.
6) One thing that caught my eye is that maybe our data sampling can be done in a more pseudo-random manner to make sure that all valid anchor data points are selected at least once in every epoch. Or we can remove the randomness of the process and just go over each valid anchor data point once every epoch, leaving the randomness only to the "negative image".
7) t-SNE representations are spread all over with some similar data points making "lumps" and others spread out for all margin and epoch values.
8) This type of dissimilarity hints at insufficeint ability of the model to learn and differentiate between different images. Design choices like model depth, embedding length, and pre-training data bias (highly unlikely) seem like important factors here.


## Bonus Task
Honestly, lost for words. \
We did not expect the model to be this bad.